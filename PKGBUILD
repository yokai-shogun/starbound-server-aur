# Maintainers: Mike Cooper <mythmon at elem.us>, Mikko <mikko at 5x.fi>

pkgname=starbound-server
pkgver=1.4.4
pkgrel=1
pkgdesc="Official dedicated server for Starbound"
arch=('x86_64' 'x86')
license=('unknown')
url="https://terraria.org/"
depends=('screen')
makedepends=('unzip')

_pkgver=$(echo $pkgver | sed 's/\.//g')

source=(
  "starbound-server-144.zip"
  "starbound-server"
  'starbound_server.config'
  "starbound-server.service"
)

sha256sums=(
  '1ef0e24190f99eafd774456e96ab73cd8bb7ad438c5c9267d88d48dd2a1a0044'
  'd1dd215acbd04be64120225ef905af460be157340a07c589e5293939023ababa'
  '7bf0d6cf43467e3b7dcac24679d7a6c61d12de20c00342cf1d16caefe12655a5'
  '0baf62d83d69809c1fed447db85c6b3e6d7ebb0d651cec46e7e87ecb211c4c4d'
)

package() {
    dest="${pkgdir}/opt/starbound-server"
    install -d "${dest}"

    cd "starbound-server-144"
    cp -r * "${dest}/"
    chmod +x "${dest}/linux/starbound_server"

    cd "${srcdir}"
    install -d "${pkgdir}/usr/bin/"
    install -m755 starbound-server "${pkgdir}/usr/bin/"
    install -d "${pkgdir}/usr/lib/systemd/system/"
    install -m644 starbound-server.service "${pkgdir}/usr/lib/systemd/system/"
    install -m755 starbound_server.config "${dest}/storage"
}
