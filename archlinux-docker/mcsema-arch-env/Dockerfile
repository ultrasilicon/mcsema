FROM archlinux

RUN pacman -Syu --noconfirm --needed base-devel git wget yajl

# ========== use builduser ==========
RUN useradd builduser -m \ 
    && passwd -d builduser \
    && printf 'builduser ALL=(ALL) NOPASSWD:ALL\n' | tee -a /etc/sudoers 
USER builduser

# ========== install yay ==========
RUN cd /tmp \
    && git clone https://aur.archlinux.org/yay.git \
    && cd yay/ \
    && makepkg -si --noconfirm 

# ========== install mcsema build env ==========
RUN yay -S --noconfirm \
    git \
    cmake \
    protobuf \
    gflags \
    google-glog \
    gtest \
    intelxed-git \
    llvm \
    clang \
    python2 \
    python-pip

USER root
RUN pip install \
    protobuf \
    clang \
    ccsyspath



CMD echo "hello world"