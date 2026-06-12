---
title: "ATI graphics driver problem"
date: 2012-02-05
forum: General Help
---

### Post by Falc7 on 2012-02-05
I have a Radeon 5xxx series graphics card in my laptop, after upgrading to KDE 4.8, i think the driver has stopped working anymore, because of this:

```
jamie@jamie-Inspiron-N5010:~$ sudo apt-get remove --purge xorg-driver-fglrx fglrx*
[sudo] password for jamie: 
Sorry, try again.
[sudo] password for jamie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'xorg-driver-fglrx' can't be removed
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-amdcccle-updates is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmarblewidget12 kdewallpapers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jamie@jamie-Inspiron-N5010:~$ 


```

However this code seems to suggest it is working, so i'm a bit confused
```
jamie@jamie-Inspiron-N5010:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6500M/5600/5700 Series
OpenGL version string: 4.1.11251 Compatibility Profile Context

```

But my laptop has been running hot for no reason recently, which could be caused by it using the open source driver.



So i downloaded the new driver as it recommends here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But i get this error message:
```
cd /home/jamie/Downloads
clear
jamie@jamie-Inspiron-N5010:~/Downloads$ cd /home/jamie/Downloads
jamie@jamie-Inspiron-N5010:~/Downloads$ clear







jamie@jamie-Inspiron-N5010:~/Downloads$ sudo sh amd-driver-installer-12-1-x86.x86_64.run --buildpkg Ubuntu/oneiric
[sudo] password for jamie: 
Created directory fglrx-install.Sguz8u
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.93.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/oneiric
Resolving build dependencies...
Continuing package build
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.930-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.Xu5vry
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
                         dkms.conf \
                         fglrx.install \
                         fglrx-dev.install \
                         fglrx-dev.links \
                         fglrx-amdcccle.install \
                         fglrx.grub-gfxpayload \
                         fglrx.dirs \
                         fglrx.links \
                         fglrx.postinst \
                         fglrx.postrm \
                         fglrx.preinst \
                         fglrx.prerm \
                         overrides/fglrx; do \
                sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
                        -e "s|#LIBDIR#|usr/lib|g" \
                        -e "s|#LIBDIR32#|usr/lib32|g" \
                        -e "s|#BINDIR#|usr/bin|g" \
                        -e "s|#SYSCONFDIR#|etc|g" \
                        -e "s|#MANDIR#|usr/share/man/man1|g" \
                        -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
                        -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
                        -e "s|#ALTPRIORITY#|1000|g" \
                        -e "s|#PXALTPRIORITY#|900|g" \
                        -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
                        -e "s|#DATADIR#|usr/share|g" \
                        -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
                        -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
                        -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
                        -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
                        -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
                        -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
                        -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
                        -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
                        -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
                        -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
                        -e "s|#DRIVERNAME#|fglrx|g" \
                        -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
                        -e "s|#DRIVERSRCNAME#||g" \
                        -e "s|#INCLUDEDIR#|usr/include|g" \
                        -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
                        -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
                        -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
                        -e "s|#PXDIR#|usr/lib/pxpress|g" \
                        -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
                        -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
                        -e "s|#PXDIRNAME#|pxpress|g" \
                        -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
                        -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
                        -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
                        -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
                        -e "s|#CVERSION#|8.930|g" \
                        -e "s|#SRCXARCH#|xpic_64a|g" \
                        -e "s|#SRCARCH#|x86_64|g" \
                        -e "s|#SRCLIBDIR#|lib64|g" \
                        -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
                        -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
                        debian/$i.in > debian/$i;      \
        done
# remove exec bit on everything
find arch \
                etc \
                lib \
                module \
                usr \
                xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
                arch/x86_64/usr/X11R6/bin \
                usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
for i in \
                        debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
                        debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
                        ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/fglrx-libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
                        debian/fglrx/usr/lib/fglrx/bin/clinfo \
                        debian/fglrx/usr/lib/fglrx/bin/atiode \
                        debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
                        debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
                        debian/fglrx/usr/lib/fglrx/*libGL.so.*.* \
                        debian/fglrx/usr/lib/fglrx/*libOpenCL.so.* \
                        ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/clinfo
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/fglrx-libGL.so.1.2
- debian/fglrx/usr/lib/fglrx/libOpenCL.so.1
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
                -type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libGL*'`; \
                do \
                        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
                        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
                        # Remove fglrx prefix \
                        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
                        full_path=`echo "$path$new_name"`; \
                        mv -f $lib $full_path; \
        done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libglx*'`; \
                do \
                        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
                        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
                        new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
                        # Remove fglrx prefix \
                        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
                        full_path=`echo "$new_path$new_name"`; \
                        mv -f $lib $full_path; \
        done
# Create links for PowerXpress X modules (except for extensions)
for i in \
                debian/fglrx/usr/lib/fglrx/xorg/modules/* \
                ; do \
                        orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
                        if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
                                link_name=$orig_name ; \
                                link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
                                dh_link -pfglrx $orig_name $link_name ; \
                        fi \
                done
# Create links for PowerXpress libs (except for libGL)
for i in \
                debian/fglrx/usr/lib/fglrx/* \
                ; do \
                        orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
                        # Copy each file except for libGL* \
                        if [ -f $i ]; then \
                                if [ ! `echo $orig_name  | grep libGL` ]; then \
                                        link_name=$orig_name ; \
                                        link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                                        dh_link -pfglrx $orig_name $link_name ; \
                                fi \
                        else \
                                # Here we only accept the dri directory \
                                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                                if [ "$dir_name" = "dri" ]; then \
                                        link_name=$orig_name ; \
                                        link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
                                        dh_link -pfglrx $orig_name $link_name ; \
                                fi \
                        fi \
                done
# Create links for PowerXpress 32bit libs (except for libGL)
for i in \
                debian/fglrx/usr/lib32/fglrx/* \
                ; do \
                        orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
                        # Copy each file except for libGL* \
                        if [ -f $i ]; then \
                                if [ ! `echo $orig_name  | grep libGL` ]; then \
                                        link_name=$orig_name ; \
                                        link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                                        dh_link -pfglrx $orig_name $link_name ; \
                                fi \
                        else \
                                # Here we only accept the dri directory \
                                dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
                                if [ "$dir_name" = "dri" ]; then \
                                        link_name=$orig_name ; \
                                        link_name=`echo $orig_name  | sed -e "s|usr/lib32/fglrx|usr/lib32/pxpress/lib|"`; \
                                        dh_link -pfglrx $orig_name $link_name ; \
                                fi \
                        fi \
                done
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
printf '# This file was installed by fglrx\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.Xu5vry/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" > "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>      "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/x86_64-linux-gnu/mesa" >         "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/pxpress/lib" >>  "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/i386-linux-gnu/mesa" >>      "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib32/pxpress/lib" >>        "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/pxpress/ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative
echo "" > "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/fglrx/alt_ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
                lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
                debian/fglrx.modaliases
dh_modaliases
rm debian/fglrx.modaliases
#Run the normal stuff
dh binary-arch
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_installexamples -a -Nfglrx
   dh_installman -a -Nfglrx
   dh_installcatalogs -a -Nfglrx
   dh_installcron -a -Nfglrx
   dh_installdebconf -a -Nfglrx
   dh_installemacsen -a -Nfglrx
   dh_installifupdown -a -Nfglrx
   dh_installinfo -a -Nfglrx
   dh_installinit -a -Nfglrx
   dh_installmenu -a -Nfglrx
   dh_installmime -a -Nfglrx
   dh_installmodules -a -Nfglrx
   dh_installlogcheck -a -Nfglrx
   dh_installlogrotate -a -Nfglrx
   dh_installpam -a -Nfglrx
   dh_installppp -a -Nfglrx
   dh_installudev -a -Nfglrx
   dh_installwm -a -Nfglrx
   dh_installxfonts -a -Nfglrx
   dh_installgsettings -a -Nfglrx
   dh_bugfiles -a -Nfglrx
   dh_ucf -a -Nfglrx
   dh_lintian -a -Nfglrx
   dh_gconf -a -Nfglrx
   dh_icons -a -Nfglrx
   dh_perl -a -Nfglrx
   dh_usrlocal -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.Xu5vry'
dh_shlibdeps -l/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.Xu5vry/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 23 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libSlotMaximizerBe.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libSlotMaximizerAg.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.Xu5vry'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.Sguz8u
jamie@jamie-Inspiron-N5010:~/Downloads$ 

```

---

### Post by Yellow Pasque on 2012-02-05
You might need to install some packages before building the ATI driver. See: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by Falc7 on 2012-02-06
That seems to have fixed it, thanks!

---

### Post by cazazo on 2012-04-29
Will this work for Ubuntu 12.04 with classic Gnome as desktop??? Since I've update from 10.10... OpenGL apps are like in muddy grounds! Specially games such as Alien Arena.
Thank you!

---

### Post by Yellow Pasque on 2012-04-29
You should just use the fglrx package included in Precise. That takes care of the dependencies for you.

---

### Post by cazazo on 2012-04-29
I did installed the driver but still having issues... here is the thread I opened today 
[http://ubuntuforums.org/showthread.php?p=11889572#post11889572]("http://ubuntuforums.org/showthread.php?p=11889572#post11889572")
Thank you for the reply!

---

