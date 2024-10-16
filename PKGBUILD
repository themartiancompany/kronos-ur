# Maintainer: Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix
# Contributor: Pellegrino Prevete <pellegrinoprevete@gmail.com>

pkgname=kronos
pkgver=2.6.2
pkgrel=1
pkgdesc="Sega Saturn emulator, fork of yabause"
arch=(x86_64 aarch64 i686 pentium4)
url="https://github.com/FCare/Kronos"
license=(GPL-2.0-or-later)
depends=(openal qt5-base qt5-multimedia sdl2 libglvnd glibc gcc-libs)
makedepends=(cmake glu ) #gcc13
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/FCare/Kronos/archive/refs/tags/${pkgver}_official_release.tar.gz")
b2sums=('4c8a5fe5335664cff809d364436afacb77f502358d5272a09eaf9556713a5f470a210cafad0f092f4cfd104ae94f55a5d96702977a2509c6b4d6be55bc0ebfd6')

build() {
  #export CC=/usr/bin/gcc-13 CXX=/usr/bin/g++-13
  export CFLAGS+=" -Wno-error=format-security"
  export CXXFLAGS+=" -Wno-error=format-security"

  cmake -B build -S "Kronos-${pkgver}_official_release/yabause" \
    -Wno-dev \
    -DCMAKE_BUILD_TYPE=None \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DYAB_USE_QT5=ON

  cmake --build build
}

package() {
  DESTDIR="${pkgdir}" cmake --install build
}
