# Maintainer: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>
# Contributor: Roan Huang <pichuang@cs.nctu.edu.tw>

_pkgname=bittornado
pkgname=papa-${_pkgname}
pkgver=0.3.18
pkgrel=1
pkgdesc="An experimental client based on the official bittorrent"
arch=('any')
url="http://bittornado.com/"
license=('MIT')
depends=('python2' 'python2-crypto')
optdepends=('wxpython: for using the graphical client'
            'wxgtk: for using the graphical client')
source=("http://download2.bittornado.com/download/BitTornado-${pkgver}.tar.gz"
        'bttracker.service'
        'papa-btmakemetafile'
        'papa-btdownloadcurses')
md5sums=('faeb137036cfaaeab91afc7f62c7dc30'
         '3dbe56e749bc30d8ed6a23df965b029d'
         '85b0b5923e62aa2a6b07707d952b7bf6'
         '3a2704a20995cfede0b832d699a30d1f')

package() {
  cd "${srcdir}/BitTornado-CVS"

  python2 setup.py install --root="${pkgdir}"

  #license file install
  install -D -m644 "${srcdir}/BitTornado-CVS/LICENSE.txt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  
  #install bttracker service
  install -d -m755 ${pkgdir}/usr/lib/systemd/system
  install -m644 ${srcdir}/bttracker.service ${pkgdir}/usr/lib/systemd/system/
    
  #install bt log dir
  install -d -m755 ${pkgdir}/var/log/bittornado
  
  #For cs use to make torrent
  install -m755 ${srcdir}/papa-btmakemetafile ${pkgdir}/usr/bin/
  install -m755 ${srcdir}/papa-btdownloadcurses ${pkgdir}/usr/bin/
  
}
