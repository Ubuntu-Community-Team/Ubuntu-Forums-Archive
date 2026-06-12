---
title: "Program can't find libraries"
date: 2010-02-15
forum: General Help
---

### Post by conmat on 2010-02-15
Karmic 64-bit
Lenovo T400 (using Intel graphics and Ubuntu drivers)

I am trying to install google earth with synaptic package manager.  I let synaptic install GE and everything seems O.K.  The only window that appears is the synaptic window that says the installation is complete.  When I try to start GE by clicking on the launcher in applications>internet>GE I get the GE splashscreen for a few seconds and then nothing happens.

When I try to start GE from the terminal I get:
/usr/lib32/googleearth/googleearth-bin: error while loading shared libraries: libQtWebKit.so.4: wrong ELF class: ELFCLASS64

googleearth-bin is here:
/usr/lib32/googleearth
Also these libraries:

drivers.ini                 libgdal.so.1           liblayout.so
googleearth-bin             libge_net.so           libmath.so
gpsbabel                    libgeobase.so          libmeasure.so
ImporterGlobalSettings.ini  libgeobaseutils.so     libminizip.so
ImporterUISettings.ini      libGLU.so.1            libmoduleframework.so
kh20                        libgoogleearth_lib.so  libnavigate.so
kvw                         libgooglesearch.so     libnss_mdns4_minimal.so.2
lang                        libgps.so              libport.so
libalchemyext.so            libicudata.so.38       libproj.so.0
libapiloader.so             libicuuc.so.38         libQtWebKit.so.4
libauth.so                  libIGAttrs.so          libQtWebKit.so.4.bak
libbase.so                  libIGCore.so           librender.so
libbasicingest.so           libIGExportCommon.so   libreporting.so
libcollada.so               libIGGfx.so            libwmsbase.so
libcommon.so                libIGMath.so           PCOptimizations.ini
libcomponentframework.so    libIGOpt.so            plugins
libcurl.so.4                libIGSg.so             qt.conf
libevll.so                  libIGUtils.so          resources
libflightsim.so             libinput_plugin.so     shaders
libfusioncommon.so          liblayer.so           

I read some posts and I have ia-32libs installed.

When I enter this command:
ldd /usr/lib32/googleearth/googleearth-bin

I get this:
    linux-gate.so.1 =>  (0xf771e000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf76db000)
    libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf75e9000)
    libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf73b6000)
    libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf6a18000)
    libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf6902000)
    libQtWebKit.so.4 => not found
    libgoogleearth_lib.so => not found
    libm.so.6 => /lib32/libm.so.6 (0xf68db000)
    libc.so.6 => /lib32/libc.so.6 (0xf6796000)
    /lib/ld-linux.so.2 (0xf771f000)
    libbase.so => not found
    libgeobase.so => not found
    libz.so.1 => /usr/lib32/libz.so.1 (0xf677f000)
    libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6779000)
    librt.so.1 => /lib32/librt.so.1 (0xf6770000)
    libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf66ba000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf66a0000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf669c000)
    libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6682000)
    libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf665a000)
    libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf65db000)
    libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf659c000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6593000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6578000)
    libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf656e000)
    libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6541000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6531000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6401000)
    libpcre.so.3 => /lib32/libpcre.so.3 (0xf63d0000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf637d000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6379000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf6374000)
    libexpat.so.1 => /lib32/libexpat.so.1 (0xf634c000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf632e000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6329000)

What is going on????

 libQtWebKit.so.4 => not found?????

There is a symbolic link libQtWebKit.so.4 =>  /usr/lib/libQtWebKit.so.4.5.2

Any suggestions are appreciated!!!

---

### Post by gordintoronto on 2010-02-15
Try this web site:
[https://help.ubuntu.com/community/GoogleEarth#Troubleshooting](https://help.ubuntu.com/community/GoogleEarth#Troubleshooting)

---

