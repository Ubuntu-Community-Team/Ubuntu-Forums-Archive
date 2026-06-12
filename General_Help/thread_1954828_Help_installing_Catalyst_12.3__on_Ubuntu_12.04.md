---
title: "Help installing Catalyst 12.3  on Ubuntu 12.04"
date: 2012-04-08
forum: General Help
---

### Post by mentalchaos on 2012-04-08
I've been at this for about two days now. I've used the following links for help 

[http://ubuntuguide.net/install-amd-ati-driver-catalyst-12-3-in-ubuntu-12-04-precise]("http://ubuntuguide.net/install-amd-ati-driver-catalyst-12-3-in-ubuntu-12-04-precise") 

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx") 

My issue is the run file won't packet in to a deb. 

Here is what I get when I run the command "sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/natty"

```
Created directory fglrx-install.5izkch
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.951...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/natty
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: cannot create /tmp/pkg_build.out: Permission denied
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: cannot create /tmp/pkg_build.out: Permission denied
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.951-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.PJDBSi
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
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
Removing temporary directory: fglrx-install.5izkch

```

---

### Post by dylan07 on 2012-04-08
What video card do you have? And also, just wondering, do you have an AMD Processor?

---

### Post by mentalchaos on 2012-04-08
I have a 5830. I'm using intel.

---

### Post by dylan07 on 2012-04-08
Maybe try using "sudo" to run as super user?

---

### Post by mentalchaos on 2012-04-08
Okay I got it to install, but with the following error ```
Error] Kernel Module : Failed to build fglrx-8.951 with DKMS
[Error] Kernel Module : Removing fglrx-8.951 from DKMS

```

---

### Post by aeronutt on 2012-04-08
Just FYI, I loaded fglrx from the repositories in 12.04, and it works fine! (Has never worked on my laptop prior to 12.04). So you might want to try the easy way.

---

### Post by mentalchaos on 2012-04-08
I'm sorry, but what exactly do you mean by repositories? I'm new to ubuntu. How would I go about doing that?

---

### Post by aeronutt on 2012-04-08
> **mentalchaos said:**
> I'm sorry, but what exactly do you mean by repositories? I'm new to ubuntu. How would I go about doing that?

To install fglrx:
```
sudo apt-get install fglrx
```

To setup, run this once:
```
sudo aticonfig --initial
```
Restart xserver (alt-prntscr-k), or reboot

Then, use the following commands to switch between graphics:

To select descrete graphics:
```
sudo aticonfig --px-dgpu 
```
Restart xserver (alt-prntscr-k)

To select integrated graphics:
```
sudo aticonfig --px-igpu 
```
Restart xserver (alt-prntscr-k)

There's a 'bug' in fglrx when trying to use Intel integrated graphics and Unity3D or gnome-shell.  If that's the case for you, there's one line in one file you'll have to edit. But see if the above works first.

---

### Post by mentalchaos on 2012-04-08
Ok I did what you said. When I tried the integrated graphics my computer locked up flashed a brown screen, then went to black. So when using descrete graphics am I using my graphics card with the new drivers?

---

### Post by aeronutt on 2012-04-08
Try logging in to Unity 2D, if that works, then you'll probably have to make a small edit to a fgrlx file.

---

### Post by mentalchaos on 2012-04-08
I'm in unity 2d. Thats default right? Never had unity 3d.

---

### Post by aeronutt on 2012-04-08
> **mentalchaos said:**
> I'm in unity 2d. Thats default right? Never had unity 3d.

Hmmmm.....unity3d is usually the default. It's shown simply as "unity" at the login. Is it working?

---

### Post by mentalchaos on 2012-04-08
Well everything seem to be working fine now Thank You.

---

### Post by mentalchaos on 2012-04-08
> **aeronutt said:**
> Hmmmm.....unity3d is usually the default. It's shown simply as "unity" at the login. Is it working?


Works just fine in 2d.

---

### Post by Hungry Man on 2012-04-08
How do I check which version I'm using? I see this:
> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6500M/5600/5700 Series
OpenGL version string: 4.2.11627 Compatibility Profile Context



---

### Post by mentalchaos on 2012-04-08
> **Hungry Man said:**
> How do I check which version I'm using? I see this:

Open up the Catalyst Control Center from the Dash Home search, once open click the information tab.

---

### Post by Yellow Pasque on 2012-04-09
For the record, the problem in the OP was:
```
--buildpkg Ubuntu/natty
```
should have been:
```
--buildpkg Ubuntu/precise
```

---

### Post by mentalchaos on 2012-04-09
I just gave up using that command altogether. I ended up just clicking on the .run file and running in the terminal

---

### Post by Hungry Man on 2012-04-09
> **mentalchaos said:**
> Open up the Catalyst Control Center from the Dash Home search, once open click the information tab.

Haha, I'm so used to using the terminal at this point I'd forgotten to check for a gui.

Thank you, it seems to have installed flawlessly.

---

### Post by DjDiabolik on 2012-04-09
It's usless!! i don't want to install the FLGX but i want to install latest 12.3 downloaded from AMD Site.

The FLGRX maded on ubuntu it's a old version of catalyst like 11.8........

I'm stay on ubuntu 11.10 with latest kernel 3.3.1 but i have same exactly problems on first post!

How i can to resolve it ?

---

### Post by Yellow Pasque on 2012-04-10
> **DjDiabolik said:**
> It's usless!! i don't want to install the FLGX but i want to install latest 12.3 downloaded from AMD Site.

The FLGRX maded on ubuntu it's a old version of catalyst like 11.8........

I'm stay on ubuntu 11.10 with latest kernel 3.3.1 but i have same exactly problems on first post!

How i can to resolve it ?
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by DjDiabolik on 2012-04-10
> **Temüjin said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
This guide it's usless and obsolete and not working.

DKMS during of installation............

```
diabolik@Diabolik-ubuntu:~/catalyst12.3$ sudo sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/oneiric
[sudo] password for diabolik: 
Created directory fglrx-install.7Vqqf2
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.951...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/oneiric
Package /home/diabolik/catalyst12.3/fglrx_8.951-0ubuntu1_i386.deb has been successfully generated
Package /home/diabolik/catalyst12.3/fglrx-dev_8.951-0ubuntu1_i386.deb has been successfully generated
Package /home/diabolik/catalyst12.3/fglrx-amdcccle_8.951-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.7Vqqf2
diabolik@Diabolik-ubuntu:~/catalyst12.3$ 

```**** guide for **** driver:
```
diabolik@Diabolik-ubuntu:~/catalyst12.3$ sudo dpkg -i fg*.deb
Selezionato il pacchetto fglrx.
(Lettura del database... 322768 file e directory attualmente installati.)
Estrazione di fglrx (da fglrx_8.951-0ubuntu1_i386.deb)...
Selezionato il pacchetto fglrx-amdcccle.
Estrazione di fglrx-amdcccle (da fglrx-amdcccle_8.951-0ubuntu1_i386.deb)...
Selezionato il pacchetto fglrx-dev.
Estrazione di fglrx-dev (da fglrx-dev_8.951-0ubuntu1_i386.deb)...
Configurazione di fglrx (2:8.951-0ubuntu1)...
update-alternatives: viene usato /usr/lib/fglrx/ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica.
update-alternatives: attenzione: saltata la creazione di /etc/OpenCL/vendors/amdocl64.icd poiché il file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalcl.so poiché il file /usr/lib32/fglrx/libaticalcl.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalrt.so poiché il file /usr/lib32/fglrx/libaticalrt.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: viene forzata l'installazione dell'alternativa /usr/lib/fglrx/ld.so.conf poiché il gruppo i386-linux-gnu_gl_conf è danneggiato.
update-alternatives: attenzione: saltata la creazione di /etc/OpenCL/vendors/amdocl64.icd poiché il file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalcl.so poiché il file /usr/lib32/fglrx/libaticalcl.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalrt.so poiché il file /usr/lib32/fglrx/libaticalrt.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: viene usato /usr/lib/fglrx/alt_ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in modalità automatica.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.3.1-030301-generic-pae
Loading new fglrx-8.951 DKMS files...
First Installation: checking all kernels...
Building only for 3.3.1-030301-generic-pae
Building for architecture i686
Building initial module for 3.3.1-030301-generic-pae
Error! Bad return status for module build on kernel: 3.3.1-030301-generic-pae (i686)
Consult /var/lib/dkms/fglrx/8.951/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Elaborazione dei trigger per ureadahead...
Elaborazione dei trigger per gnome-menus...
Elaborazione dei trigger per bamfdaemon...
Rebuilding /usr/share/applications/bamf.index...
Configurazione di fglrx-amdcccle (2:8.951-0ubuntu1)...
Configurazione di fglrx-dev (2:8.951-0ubuntu1)...
Elaborazione dei trigger per initramfs-tools...
update-initramfs: Generating /boot/initrd.img-3.3.1-030301-generic-pae
Elaborazione dei trigger per libc-bin...
ldconfig deferred processing now taking place
diabolik@Diabolik-ubuntu:~/catalyst12.3$ 

```

This is the make.log created:
```

DKMS make.log for fglrx-8.951 for kernel 3.3.1-030301-generic-pae (i686)
mar 10 apr 2012, 13.40.34, CEST
AMD kernel module generator version 2.1
[: 393: 1: unexpected operator
[: 399: 1: unexpected operator
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.3.1-030301-generic-pae/build SUBDIRS=/var/lib/dkms/fglrx/8.951/build/2.6.x modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.3.1-030301-generic-pae"
  CC [M]  /var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c: In function &#8216;KCL_fpu_begin&#8217;:
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: error: &#8216;TS_USEDFPU&#8217; undeclared (first use in this function)
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o] Errore 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.951/build/2.6.x] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.3.1-030301-generic-pae"
make: *** [kmod_build] Errore 2
build failed with return value 2

```

---

### Post by Yellow Pasque on 2012-04-10
> **DjDiabolik said:**
> This guide it's usless and obsolete and not working.

It is not useless or obsolete. The reason it's not working is that you're using a custom 3.3 kernel. Fortunately, there's an easy workaround: [http://forums.fedoraforum.org/showpost.php?p=1564578&postcount=6](http://forums.fedoraforum.org/showpost.php?p=1564578&postcount=6)

---

### Post by DjDiabolik on 2012-04-10
and how i can apply ?? and what's file i need to modify ?

*EDIT*
and WTF i need to configure to uninstall correctly all driver i try to install now ?

And after what procedure i need to use ?? Running the .run official installer or install manually the .deb file ?? or both ?

I have so many confusion!

---

### Post by Yellow Pasque on 2012-04-10
Removal instructions are found on the same page: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

You seem to have difficulty following directions. Maybe you should just wait for AMD to release a Catalyst that supports kernel 3.3..

---

### Post by DjDiabolik on 2012-04-10
> **Temüjin said:**
> Removal instructions are found on the same page: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

You seem to have difficulty following directions. Maybe you should just wait for AMD to release a Catalyst that supports kernel 3.3..
Ok.. i don't have understand if i need to execute this:

```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon sudo apt-get install xserver-xorg-video-ati sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup sudo rm -rf /etc/ati 
```

---

### Post by Yellow Pasque on 2012-04-10
Those commands are only relevant if you plan on going back to open-source radeon driver.

---

### Post by DjDiabolik on 2012-04-10
ok.. i have try now to execute this:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

Command not found... it's normal i thinks because driver it's not installed

Execute this:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
```
I obtain for all package it's no installed..........

Continue to execute this:
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```

After that i have restarted my ubuntu...... the unity 2d apps list it's no appears......... it's normal because i thinks there's no driver installed.

From Terminal i have try to proced to install driver.... after i created the 3 file .deb:
```
diabolik@Diabolik-ubuntu:~/catalyst12.3$ sudo dpkg -i *deb
Selezionato il pacchetto fglrx.
(Lettura del database... 214702 file e directory attualmente installati.)
Estrazione di fglrx (da fglrx_8.951-0ubuntu1_i386.deb)...
Selezionato il pacchetto fglrx-amdcccle.
Estrazione di fglrx-amdcccle (da fglrx-amdcccle_8.951-0ubuntu1_i386.deb)...
Selezionato il pacchetto fglrx-dev.
Estrazione di fglrx-dev (da fglrx-dev_8.951-0ubuntu1_i386.deb)...
Configurazione di fglrx (2:8.951-0ubuntu1)...
update-alternatives: viene usato /usr/lib/fglrx/ld.so.conf per fornire /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modalità automatica.
update-alternatives: attenzione: saltata la creazione di /etc/OpenCL/vendors/amdocl64.icd poiché il file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalcl.so poiché il file /usr/lib32/fglrx/libaticalcl.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalrt.so poiché il file /usr/lib32/fglrx/libaticalrt.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: viene forzata l'installazione dell'alternativa /usr/lib/fglrx/ld.so.conf poiché il gruppo i386-linux-gnu_gl_conf è danneggiato.
update-alternatives: attenzione: saltata la creazione di /etc/OpenCL/vendors/amdocl64.icd poiché il file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalcl.so poiché il file /usr/lib32/fglrx/libaticalcl.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: attenzione: saltata la creazione di /usr/lib32/libaticalrt.so poiché il file /usr/lib32/fglrx/libaticalrt.so associato (del gruppo i386-linux-gnu_gl_conf) non esiste.
update-alternatives: viene usato /usr/lib/fglrx/alt_ld.so.conf per fornire /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in modalità automatica.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-18-generic-pae
Loading new fglrx-8.951 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-18-generic-pae
Building for architecture i686
Building initial module for 3.0.0-18-generic-pae
Error! Bad return status for module build on kernel: 3.0.0-18-generic-pae (i686)
Consult /var/lib/dkms/fglrx/8.951/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Elaborazione dei trigger per ureadahead...
ureadahead will be reprofiled on next reboot
Elaborazione dei trigger per gnome-menus...
Elaborazione dei trigger per bamfdaemon...
Rebuilding /usr/share/applications/bamf.index...
Configurazione di fglrx-amdcccle (2:8.951-0ubuntu1)...
Configurazione di fglrx-dev (2:8.951-0ubuntu1)...
Elaborazione dei trigger per initramfs-tools...
update-initramfs: Generating /boot/initrd.img-3.0.0-18-generic-pae
Elaborazione dei trigger per libc-bin...
ldconfig deferred processing now taking place
```

This terminal it's a my precedent try with kernel 3.0.0-18... now i'm installed 3.3.1-generic-pae but i obtain the exact same error........

---

### Post by Yellow Pasque on 2012-04-10
The cause of the error may be different. You need to look at /var/lib/dkms/fglrx/8.951/build/make.log for more information.

---

### Post by DjDiabolik on 2012-04-11
> **Temüjin said:**
> The cause of the error may be different. You need to look at /var/lib/dkms/fglrx/8.951/build/make.log for more information.
on this folder i don't have this .log file..........

I thinks i need to retry to install it from deb file.

---

