---
title: "Help compiling latest Intel driver for Lucid (x64)"
date: 2010-04-26
forum: General Help
---

### Post by mockingbird on 2010-04-26
Hi,

> The decision to stick with this aging release is based on the fact that Intel stripped out user-space mode-setting (UMS) support from the xf86-video-intel 2.10 driver and that leaves this X.Org driver to only supporting kernel mode-setting. Kernel mode-setting is certainly superior to the old user-space mode-setting and KMS is where all the X.Org drivers are moving to, but there are a few caveats with Intel's support. At this time there's reports of some Ubuntu users with the very old Intel 8xx series IGPs running into KMS problems or quirks not being handled correctly with these newer code paths.

I have a G31 so this doesn't concern me.  The graphics performance is a little slow when scrolling in firefox and I think the newer Intel drivers will solve this.

I tried first with the 2d package from Intel, and when running configure I got an error saying my xserver-xorg was < 1.6.  I'm kind of at a loss.

```
checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Does anyone the variables for Kubuntu I would have to append to ./configure?

---

### Post by klemes on 2010-04-26
Only means that you need the -dev (development) version of these packages(and also many more dependencies as you will find out)
Perform a search in Synaptic for complete package names install them and proceed with the compilation.
:guitar:

---

### Post by 3rdalbum on 2010-04-26
Have you got the xorg-dev package?

---

### Post by mockingbird on 2010-04-26
Ok I installed xserver-xorg-dev, x11proto-xf86dri-dev, x11proto-gl-dev and configure went ok.  I hope make goes well too.  Thanks.  Oh yea, one more thing.  If make install is successful do I have to do anything else or does that upgrade it (well the 2d, anyway)?

edit:
is this a successful make or did I get an error?
```
make[3]: Leaving directory `/temp/xf86-video-intel-2.11.0/src'
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/src'
Making all in man
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/man'
sed -e 's|__vendorversion__|"xf86-video-intel 2.11.0" "X Version 11"|' -e 's|__xorgversion__|"xf86-video-intel 2.11.0" "X Version 11"|' -e 's|__xservername__|Xorg|g' -e 's|__xconfigfile__|xorg.conf|g' -e 's|__projectroot__|/usr/local|g' -e 's|__appmansuffix__|1|g' -e 's|__drivermansuffix__|4|g' -e 's|__adminmansuffix__|8|g' -e 's|__miscmansuffix__|7|g' -e 's|__filemansuffix__|5|g' < intel.man > intel.4
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/man'
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0'
make[1]: Leaving directory `/temp/xf86-video-intel-2.11.0'
linux@linux:/temp/xf86-video-intel-2.11.0$
```

---

### Post by mockingbird on 2010-04-26
Ha ha!  What do you know.  I think the upgrade was successful.  The make install exited similarly to the make which worried me a little bit (I hoped I wouldn't reboot into a broken system), but it seems to have worked.  Wrote a bunch of .lo files somewhere and the good news:

The scrolling in firefox is smoother!!

Any way I can definitively check the version?

Thanks

---

### Post by klemes on 2010-04-26
Seems your compilation went OK(did not give any errors)
Regarding your second question the answer is simply yes but a neat little trick would be to  do a sudo checkinstall rather than a sudo make install.You will need the checkinstall package of course but this will try and make a .deb package of your drivers (xserver-xorg-video-intel ....deb or xf86-video-intel...deb and also will try to install it as a deb package.So at any time you can uninstall it with sudo dpkg -r package_name..and simply reinstall the repository drivers.
Try this instead and tell us how it went.:guitar:

---

### Post by klemes on 2010-04-26
Sorry did not seem to wrote the above post just in time...
Regarding your question I think the only way to confirm that you are using the new driver (intel_drv.so) which simply overwrote the older(official Lucid) one is to have a look at your /var/log/Xorg.0.log and search for the version number if it is reported somewhere...
Other than that glad you saw an improvement!!!!!!:popcorn::guitar:

---

### Post by mockingbird on 2010-04-26
Yes, thank you.

```
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.9.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
```

Definite increase in performance.  Alt-tabbing in Plasma is faster, everything is as it should be.  Good job Intel.  Lucid should have had this to begin with.

---

### Post by mockingbird on 2010-04-29
Just one question...  The make install is indicating that it´s replacing the intel_drv.so, so why is Xorg.0.log indicating version 2.9.1?

```
Making install in uxa
make[1]: Entering directory `/temp/xf86-video-intel-2.11.0/uxa'
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/uxa'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/uxa'
make[1]: Leaving directory `/temp/xf86-video-intel-2.11.0/uxa'
Making install in src
make[1]: Entering directory `/temp/xf86-video-intel-2.11.0/src'
Making install in xvmc
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
Making install in shader
make[3]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
Making install in mc
make[4]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make  install-am
make[5]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[5]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[4]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
Making install in vld
make[4]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make  install-am
make[5]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
make[4]: Entering directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
make[3]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/xvmc'
Making install in render_program
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make  install-am
make[3]: Entering directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make[4]: Entering directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make[3]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/src/render_program'
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/src'
make[3]: Entering directory `/temp/xf86-video-intel-2.11.0/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   intel_drv.la '/usr/local/lib/xorg/modules/drivers'
libtool: install: /usr/bin/install -c .libs/intel_drv.so /usr/local/lib/xorg/modules/drivers/intel_drv.so
libtool: install: /usr/bin/install -c .libs/intel_drv.lai /usr/local/lib/xorg/modules/drivers/intel_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/temp/xf86-video-intel-2.11.0/src'
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/src'
make[1]: Leaving directory `/temp/xf86-video-intel-2.11.0/src'
Making install in man
make[1]: Entering directory `/temp/xf86-video-intel-2.11.0/man'
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man4" || /bin/mkdir -p "/usr/local/share/man/man4"
 /usr/bin/install -c -m 644 intel.4 '/usr/local/share/man/man4'
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0/man'
make[1]: Leaving directory `/temp/xf86-video-intel-2.11.0/man'
make[1]: Entering directory `/temp/xf86-video-intel-2.11.0'
make[2]: Entering directory `/temp/xf86-video-intel-2.11.0'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/temp/xf86-video-intel-2.11.0'
make[1]: Leaving directory `/temp/xf86-video-intel-2.11.0'
```

It´s definitely installed, I know it, the performance is much better.  I deleted the Xorg.0.log file and rebooted to see what a fresh one would output.

Is this just an oversight on Intel´s part?

---

### Post by dels on 2010-05-24
can someone share the compiled deb for **xf86-video-intel 2.11.0**?

---

### Post by franjesus on 2010-05-24
Here:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by bankey on 2010-09-12
> **dels said:**
> can someone share the compiled deb for **xf86-video-intel 2.11.0**?

I can share the 2.12.0..
xf86-video-intel-2.12.0.deb

build @ 2.6.31-22-generic #64-Ubuntu SMP Tue Aug 24 09:31:57 UTC 2010 i686 GNU/Linux

I ran update just before compiling today.
good luck.. 

you can also build 2.12.0 from intel,but I needed to patch a few files
[https://patchwork.kernel.org/patch/119964/](https://patchwork.kernel.org/patch/119964/)

also install the requisites as noted at the intelsite:
[http://intellinuxgraphics.org/2010Q2.html](http://intellinuxgraphics.org/2010Q2.html)
In my case I had to compile Libdrm: libdrm-2.4.21 release  too..

---

