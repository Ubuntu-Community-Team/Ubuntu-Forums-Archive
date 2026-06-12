---
title: "Building ATI catalyst driver 8.732 packages fail to build"
date: 2010-05-02
forum: General Help
---

### Post by bdw on 2010-05-02
Greetings!  I just downloaded the ATI Catalyst driver 8.723 and attempted to build the Ubuntu .deb packages for Karmic Koala and the packages fail to build.  Has anyone else had the same problem?

I run the following command:

```
sudo sh ati-driver-installer-10-4-x86.x86_64.run --buildpkg Ubuntu/karmic
```

and it fails with the resulting (long) output, even if I don't use sudo before the sh command:

```
Generating package: Ubuntu/karmic
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.723-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.723|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
#they don't provide the symlink for us (starting at 8.699)
dh_link -pxorg-driver-fglrx usr/lib/libatiuki.so.1.0 usr/lib/libatiuki.so.1
#they don't provide the symlink for us (starting at 8.72)
dh_link -pxorg-driver-fglrx usr/lib/libfglrx_gamma.so.1.0 usr/lib/libfglrx_gamma.so.1
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
```

The kernel that I'm using is 2.6.31, and the chipset is the ATI 4850.

---

