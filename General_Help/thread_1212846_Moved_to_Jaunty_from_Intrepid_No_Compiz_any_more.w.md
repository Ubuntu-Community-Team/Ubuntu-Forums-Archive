---
title: "Moved to Jaunty from Intrepid No Compiz any more.why?"
date: 2009-07-14
forum: General Help
---

### Post by ravindukelum on 2009-07-14
Now I'm Using ubuntu 9.04 64x and my graphic card is nvidia 7150 and I know it enabled and supports my 1200x800 resolution .

But the problem is I can not enable compiz extra effects.
I tried enable using compiz icon and also from System->Preference->appearance. but I can not enable effects.
Even Cairo dock and Avant not working.

Then I tried in terminal $ compiz -fusion then it gives, "no glx found".
I think there is no OpenGL support,
But I installed my graphic drivers again with Envy and It did nothing and got drivers from nvidia site and tried also with out any result.
I installed all the nvidia from synpatic also but I can not enable extra effects like it was in ubuntu 8.10.

Is that true in ubuntu jaunty I can't get effects working?,heard from some blog and is there a way to get compiz extra effects back.

---

### Post by elliotn on 2009-07-14
Same goes with me, my card is a SiS

---

### Post by ravindukelum on 2009-07-14
> **elliotn said:**
> Same goes with me, my card is a SiS

I heard the problem with 2.6.28 kernel ? I don't know well bro..

---

### Post by ravindukelum on 2009-07-16
Here are outputs of,
[LIST=1]
[*]$compiz --replace
[*]$gksu nvidia settings
[*]$glxinfo | grep render
[/LIST] 

1. ```
ravindu@ravindu-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
libpng error: Read Error
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 4319
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libxslt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/libm.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/libm.so.6
Reading symbols from /lib/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/libuuid.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /usr/lib/libGLcore.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux-x86-64.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /usr/lib/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libprotobuf.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.3
Reading symbols from /lib/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0x7fe224624780 (LWP 4319)]
Loaded symbols for /lib/libpthread.so.0
Reading symbols from /usr/lib/libstdc++.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compizconfig/backends/libini.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libglib.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/libglib-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /usr/lib/compiz/libwidget.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwidget.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libwater.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libscreenshot.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libclone.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libclone.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libfadedesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfadedesktop.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/librsvg-2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgio-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libdirectfb-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirectfb-1.0.so.0
Reading symbols from /usr/lib/libfusion-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfusion-1.0.so.0
Reading symbols from /usr/lib/libdirect-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirect-1.0.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libsnap.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsnap.so
Reading symbols from /usr/lib/compiz/libsplash.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsplash.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libbicubic.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libbicubic.so
Reading symbols from /usr/lib/compiz/libmblur.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libcommands.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcommands.so
Reading symbols from /usr/lib/compiz/libsnow.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsnow.so
Reading symbols from /usr/lib/compiz/libwobbly.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libvideo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libobs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libobs.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libelements.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libelements.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libwallpaper.so...(no debugging symbols found)..Undefined command: "-e".  Try "help".
.done.
Loaded symbols for /usr/lib/compiz/libwallpaper.so
Reading symbols from /usr/lib/compiz/libfade.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libopacify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopacify.so
Reading symbols from /usr/lib/compiz/libmove.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so

(no debugging symbols found)
0x00007fe2228968f5 in waitpid () from /lib/libc.so.6
(gdb) (gdb) 
Thread 1 (Thread 0x7fe224624780 (LWP 4319)):
#0  0x00007fe2228968f5 in waitpid () from /lib/libc.so.6
#1  0x00007fe22282e2d1 in ?? () from /lib/libc.so.6
#2  0x00007fe2183cd879 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007fe222821fb5 in raise () from /lib/libc.so.6
#5  0x00007fe222823bc3 in abort () from /lib/libc.so.6
#6  0x00007fe21c08abcd in png_create_read_struct_2 ()
   from /usr/lib/libpng12.so.0
#7  0x0000000000000000 in ?? ()
#0  0x00007fe2228968f5 in waitpid () from /lib/libc.so.6
(gdb) 
(gdb) 
(gdb) #0  0x00007fe2228968f5 in waitpid () from /lib/libc.so.6
#1  0x00007fe22282e2d1 in ?? () from /lib/libc.so.6
#2  0x00007fe2183cd879 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007fe222821fb5 in raise () from /lib/libc.so.6
#5  0x00007fe222823bc3 in abort () from /lib/libc.so.6
#6  0x00007fe21c08abcd in png_create_read_struct_2 ()
   from /usr/lib/libpng12.so.0
#7  0x0000000000000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 4319

[CRASH_HANDLER]: "/tmp/compiz_crash-4319.out" created!




```

2. ```
ravindu@ravindu-laptop:~$ gksudo nvidia-settings
ERROR: Cannot open display 'ravindu-laptop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line
       34 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 47 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on
       line 48 of configuration file '/root/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on
       line 49 of configuration file '/root/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 50
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).




```


3. ```
ravindu@ravindu-laptop:~$  glxinfo | grep rende
direct rendering: Yes
OpenGL renderer string: GeForce 7150M / nForce 630M/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
```

---

### Post by 3rdalbum on 2009-07-16
Your problem is that Compiz is crashing, but I don't know why.

If you have the Compiz "unsupported" plugins package, try removing it.

---

### Post by ravindukelum on 2009-07-18
:D
Solved reinstalled glx for nvidia-185.

sudo apt-get install nvidia-glx-185

---

