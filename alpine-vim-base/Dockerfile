FROM alpine:latest

MAINTAINER JAremko <w3techplaygound@gmail.com>

RUN apk --update add --virtual build-deps python bash python-dev ctags build-base \
      make mercurial libxpm-dev libx11-dev libxt-dev ncurses-dev git gcc cmake && \
    cd /tmp && \
    hg clone https://code.google.com/p/vim/ && \
    cd /tmp/vim && \
    ./configure --with-features=normal \
                --enable-multibyte \
                --enable-pythoninterp \
                --with-x=yes \
                --enable-acl \
                --disable-gui \
                --disable-netbeans \
                --prefix /usr && \
    make VIMRUNTIMEDIR=/usr/share/vim/vim74 && \
    make install && \
    apk del build-deps && \
    apk --update add libsm libice libxt libx11 ncurses && \
    rm -rf /var/cache/apk/* && \
    rm -rf /tmp/*