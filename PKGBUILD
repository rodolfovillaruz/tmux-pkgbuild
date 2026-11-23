pkgname=tmux-git
pkgver=r12778.6069d58e
pkgrel=1
pkgdesc="tmux built from rodolfovillaruz fork"
arch=('x86_64')
url="https://github.com/rodolfovillaruz/tmux"
license=('ISC')
depends=('ncurses' 'libevent' 'libutempter' 'systemd-libs')
makedepends=('git' 'bison' 'pkgconf')
provides=('tmux')
conflicts=('tmux')
source=("tmux::git+https://github.com/rodolfovillaruz/tmux.git#branch=master")
sha256sums=('SKIP')

pkgver() {
  cd tmux
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd tmux
  sh autogen.sh
  ./configure --prefix=/usr --enable-systemd --enable-utempter
  make
}

package() {
  cd tmux
  make DESTDIR="$pkgdir" install
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
