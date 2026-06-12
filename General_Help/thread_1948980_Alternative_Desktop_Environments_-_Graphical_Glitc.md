---
title: "Alternative Desktop Environments - Graphical Glitches"
date: 2012-03-29
forum: General Help
---

### Post by jbblack on 2012-03-29
I'm a new user and I am having an issue when trying to change desktop environments.

I don't necessarily mind Unity, but it's not my favorite.  I have downloaded and installed the Gnome 3 and Cinnamon desktops, but I get graphical glitches on the menus - they're pixelated and unreadable.  I can send screen shots if need be.

I am using Ubuntu 11.10 with an ATI video card (Radeon HD 5770).  I have downloaded and installed the restricted drivers from the graphical installer (that was a pain), but I cannot install the "post release" restricted drivers.  It gives an error, but I have not read the log file to figure out what the error is.

If you need more info, let me know what else you might need.

Thanks,
Joel

---

### Post by kc1di on 2012-03-29
hi Joel and welcome to Ubuntu,

How did you install gnome3 and cinnamon?  when you said downloaded did you do it from command line? or downloaded the actual files and install them? 

I would suggest that you use Cinnamon's PPA Repository and install it through apt-get or install synatpic package manager and do it through that route.

Here a page for Cinnamon

[http://www.howtogeek.com/103691/install-linux-mints-new-cinnamon-desktop-on-ubuntu]("http://www.howtogeek.com/103691/install-linux-mints-new-cinnamon-desktop-on-ubuntu")

Also you should be able to install gnome 3 from software center go a search for gnome desktop.
If this is the way you installed them and your are having this problem others will have to help.
Cheers!

---

### Post by jbblack on 2012-03-29
> **jbblack said:**
>   I have downloaded and installed the Gnome 3 and Cinnamon desktops,

I'm sorry. I should have stated, "Gnome Shell" not "Gnome 3."

---

### Post by jbblack on 2012-03-29
> **kc1di said:**
>  

I would suggest that you use Cinnamon's PPA Repository and install it through apt-get or install synatpic package manager and do it through that route.



I will try this when I get home this afternoon. Thanks.

I did speak with a local Linux guru. He said to install the ATI drivers from ATI not from the restricted drivers.  I will try that too.

Thanks,
Joel

---

### Post by kc1di on 2012-03-29
> **jbblack said:**
> I will try this when I get home this afternoon. Thanks.

I did speak with a local Linux guru. He said to install the ATI drivers from ATI not from the restricted drivers.  I will try that too.

Thanks,
Joel
I would agree with him ATI Drivers have had some problems.
Let us know how it all works out for you.

---

### Post by jbblack on 2012-03-29
Mmmkay...  I tried installing the ATI drivers using the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

I thought I uninstalled everything using the procedure on that same page.

Running the installation, I get to a point where I get a graphical interface.  I tell it to make a file for Ubuntu/Oneiric.  It proceeds through the installation.  When it gets done, I click OK (or whatever the only button is) and I get an error with the filename.  Here are the file contents which make no sense to me:

Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.951-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.67Nafd
dpkg-buildpackage: host architecture i386
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
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
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
			-e "s|#CVERSION#|8.951|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
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
dh_installdirs -pfglrx
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
make: execstack: Command not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.951-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.piiS3q
dpkg-buildpackage: host architecture i386
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
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
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
			-e "s|#CVERSION#|8.951|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
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
dh_installdirs -pfglrx
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
make: execstack: Command not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.951-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.ufwAwW
dpkg-buildpackage: host architecture i386
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
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
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
			-e "s|#CVERSION#|8.951|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
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
dh_installdirs -pfglrx
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
make: execstack: Command not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.951-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.HbyEpz
dpkg-buildpackage: host architecture i386
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
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
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
			-e "s|#CVERSION#|8.951|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
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
dh_installdirs -pfglrx
dh_installdirs -pfglrx-dev
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx debian/AUTHORS
dh_installdocs -pfglrx debian/copyright
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
make: execstack: Command not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/oneiric

---

### Post by jbblack on 2012-03-29
Forget my last.  I got it figured out.  I don't remember what I did now, but it's working.

I have also discovered that a lot of the apps I run do not appear to like the Unity / Gnome Shell 3D environments.  I run D-RATS and found that it would not run in Unity or Gnome Shell 3D.  I tried running from the terminal and I got some kind of "gtk" error.  Not sure why, but I ran Unity2D and D-RATS works fine.

I currently have another amateur radio app, fldigi, running just fine.

Thanks for the help.

Joel

---

### Post by wildmanne39 on 2012-03-29
Hi, if the applications are using gtk2 that is the problem because unity and gnome uses gtk3 this is my best guess since you did not say where you installed this applications from.
Thanks

---

### Post by kc1di on 2012-03-31
Hi Again Joel,

What's your ham call ?  

d-rats has a PPA that should work to install in ubuntu.
That should pull the dependecies needed and it may work that way in unity. don't know as have never used it here. 

I use fldigi and xlog a lot and also jLog with ubuntu they all seem to work fine. 

73 ,
Dave
P.S. Wildmanne39 is most likely correct unity uses gtk3 and d-rats gtk2 that's why it's not working in unity.
Don't know if it will work in cinnamon or not but worth a try.
found this on their developers page you need to have the following installed also > Debian/Ubuntu: apt-get install python-serial python-gtk2 python-libxml2 python-libxslt1 
most likey the python-gtk2 your missing.
Good Luck!

---

### Post by Cheesemill on 2012-03-31
> **kc1di said:**
> P.S. Wildmanne39 is most likely correct unity uses gtk3 and d-rats gtk2 that's why it's not working in unity.

This isn't a problem. Gnome 3 has all of the GTK2 and GTK3 libraries installed to allow backwards compatibility for applications that are written for GTK2. I'm currently running Gnome Shell and have no problems at all with GTK2 apps.

---

### Post by jbblack on 2012-03-31
Dave,

My amateur call is W4JBB.  :)  I figured you were a ham by your user name.

Regarding D-RATS, I think I'm running Gnome classic for the desktop.  I'd have to log out to make sure.  I do know that D-RATS works here but not in either Unity or the new Gnome Shell.

I think I figured out how I got the restricted drivers to work - install from terminal.  Wow!!!  That worked great, saved my changes, all I had to do was restart.

I guess I'll get me an Nvidia card when I can.  I've always been a fan of ATI and had problems with Nvidia.  Must be time to switch.

Thanks again and I've got more questions but they're not really relative to this one.

-Joel

---

