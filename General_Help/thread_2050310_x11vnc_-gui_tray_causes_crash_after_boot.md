---
title: "x11vnc -gui tray causes crash after boot"
date: 2012-08-30
forum: General Help
---

### Post by Kryben on 2012-08-30
Hello,

I have set up a vnc server on my desktop (Lubuntu 12.04) that starts up after login in on the local desktop.

The vnc server is the latest x11vnc.
The script is /usr/bin/startvnc.sh with the following content:
```
#!/bin/sh
x11vnc -forever -display :0 -rfbauth ~/.x11vnc/passwd

```
and it executes from the file /etc/xdg/lxsession/Lubuntu/autostart

This works fine.

But, as soon as I add "-gui tray" at the end of the script, x11vnc fails.
It shows an x11vnc icon in the middle of the screen for about 2 seconds and then disappears with no error provided. Doing "ps aux | grep x11vnc" shows nothing, thus x11vnc has crashed.

The weird thing is, that whenever I run the script manually, everything works just fine. A tray icon is shown in the system tray and I'm able to connect remotely and such.

I've been searching the web for hours for a solution, but haven't found anything..

Does anyone know what happened? Or could have happened? As I have no clue.

Thanks! Kryben

---

### Post by krunge on 2012-09-08
Could you paste in the x11vnc output (perhaps capture via -o option) for the -gui tray failure into this thread?

---

### Post by MrDaveInUSA on 2012-09-24
I am using Xubuntu 12.04 and am getting this message as well.  It works great on the x64 version but fails in the 386 version.  Installed 0.9.12-1build1 via Synaptic.  I uninstalled / reinstalled on the 386 and that did not resolve the issue.  Error is present when you start via the menu as well as when you put in the -gui tray option.  
  
**************************************************
Message from starting from menu:
**************************************************

tail: cannot watch `/tmp/x11vnc.tray.s3Cdvi': No such file or directory
Error Message
tail: cannot watch `/tmp/x11vnc.tray.s3Cdvi': No such file or directory
    while executing
"close $channel"
    (procedure "read_client_info" line 25)
    invoked from within
"read_client_info $client_tail"
    (procedure "read_client_tail" line 5)
    invoked from within
"read_client_tail"

**************************************************
Contents of log file
**************************************************
###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!!        @#
#@                                                           @#
#@  This means anyone with network access to this computer   @#
#@  may be able to view and control your desktop.            @#
#@                                                           @#
#@ >>> If you did not mean to do this Press CTRL-C now!! <<< @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  You can create an x11vnc password file by running:       @#
#@                                                           @#
#@       x11vnc -storepasswd password /path/to/passfile      @#
#@  or   x11vnc -storepasswd /path/to/passfile               @#
#@  or   x11vnc -storepasswd                                 @#
#@                                                           @#
#@  (the last one will use ~/.vnc/passwd)                    @#
#@                                                           @#
#@  and then starting x11vnc via:                            @#
#@                                                           @#
#@      x11vnc -rfbauth /path/to/passfile                    @#
#@                                                           @#
#@  an existing ~/.vnc/passwd file from another VNC          @#
#@  application will work fine too.                          @#
#@                                                           @#
#@  You can also use the -passwdfile or -passwd options.     @#
#@  (note -passwd is unsafe if local users are not trusted)  @#
#@                                                           @#
#@  Make sure any -rfbauth and -passwdfile password files    @#
#@  cannot be read by untrusted users.                       @#
#@                                                           @#
#@  Use x11vnc -usepw to automatically use your              @#
#@  ~/.vnc/passwd or ~/.vnc/passwdfile password files.       @#
#@  (and prompt you to create ~/.vnc/passwd if neither       @#
#@  file exists.)  Under -usepw, x11vnc will exit if it      @#
#@  cannot find a password to use.                           @#
#@                                                           @#
#@                                                           @#
#@  Even with a password, the subsequent VNC traffic is      @#
#@  sent in the clear.  Consider tunnelling via ssh(1):      @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/faq.html#faq-passwd](http://www.karlrunge.com/x11vnc/faq.html#faq-passwd)    @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  'nopw' on a line in your ~/.x11vncrc file.               @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
23/09/2012 22:26:57 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2721
23/09/2012 22:26:57 Using X display :0.0
23/09/2012 22:26:57 rootwin: 0xaa reswin: 0x5400001 dpy: 0x8f46628
23/09/2012 22:26:57 
23/09/2012 22:26:57 ------------------ USEFUL INFORMATION ------------------
23/09/2012 22:26:57 X DAMAGE available on display, using it for polling hints.
23/09/2012 22:26:57   To disable this behavior use: '-noxdamage'
23/09/2012 22:26:57 
23/09/2012 22:26:57   Most compositing window managers like 'compiz' or 'beryl'
23/09/2012 22:26:57   cause X DAMAGE to fail, and so you may not see any screen
23/09/2012 22:26:57   updates via VNC.  Either disable 'compiz' (recommended) or
23/09/2012 22:26:57   supply the x11vnc '-noxdamage' command line option.
23/09/2012 22:26:57 
23/09/2012 22:26:57 Wireframing: -wireframe mode is in effect for window moves.
23/09/2012 22:26:57   If this yields undesired behavior (poor response, painting
23/09/2012 22:26:57   errors, etc) it may be disabled:
23/09/2012 22:26:57    - use '-nowf' to disable wireframing completely.
23/09/2012 22:26:57    - use '-nowcr' to disable the Copy Rectangle after the
23/09/2012 22:26:57      moved window is released in the new position.
23/09/2012 22:26:57   Also see the -help entry for tuning parameters.
23/09/2012 22:26:57   You can press 3 Alt_L's (Left "Alt" key) in a row to 
23/09/2012 22:26:57   repaint the screen, also see the -fixscreen option for
23/09/2012 22:26:57   periodic repaints.
23/09/2012 22:26:57 
23/09/2012 22:26:57 XFIXES available on display, resetting cursor mode
23/09/2012 22:26:57   to: '-cursor most'.
23/09/2012 22:26:57   to disable this behavior use: '-cursor arrow'
23/09/2012 22:26:57   or '-noxfixes'.
23/09/2012 22:26:57 using XFIXES for cursor drawing.
23/09/2012 22:26:57 GrabServer control via XTEST.
23/09/2012 22:26:57 
23/09/2012 22:26:57 Scroll Detection: -scrollcopyrect mode is in effect to
23/09/2012 22:26:57   use RECORD extension to try to detect scrolling windows
23/09/2012 22:26:57   (induced by either user keystroke or mouse input).
23/09/2012 22:26:57   If this yields undesired behavior (poor response, painting
23/09/2012 22:26:57   errors, etc) it may be disabled via: '-noscr'
23/09/2012 22:26:57   Also see the -help entry for tuning parameters.
23/09/2012 22:26:57   You can press 3 Alt_L's (Left "Alt" key) in a row to 
23/09/2012 22:26:57   repaint the screen, also see the -fixscreen option for
23/09/2012 22:26:57   periodic repaints.
23/09/2012 22:26:57 
23/09/2012 22:26:57 XKEYBOARD: number of keysyms per keycode 7 is greater
23/09/2012 22:26:57   than 4 and 51 keysyms are mapped above 4.
23/09/2012 22:26:57   Automatically switching to -xkb mode.
23/09/2012 22:26:57   If this makes the key mapping worse you can
23/09/2012 22:26:57   disable it with the "-noxkb" option.
23/09/2012 22:26:57   Also, remember "-remap DEAD" for accenting characters.
23/09/2012 22:26:57 
23/09/2012 22:26:57 X FBPM extension not supported.
23/09/2012 22:26:57 X display is capable of DPMS.
23/09/2012 22:26:57 --------------------------------------------------------
23/09/2012 22:26:57 
23/09/2012 22:26:57 Default visual ID: 0x21
23/09/2012 22:26:57 Read initial data from X display into framebuffer.
23/09/2012 22:26:57 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
23/09/2012 22:26:57 
23/09/2012 22:26:57 X display :0.0 is 32bpp depth=24 true color
23/09/2012 22:26:57 
23/09/2012 22:26:57 Autoprobing TCP port 
23/09/2012 22:26:57 Autoprobing selected port 5903
23/09/2012 22:26:57 Listening also on IPv6 port 5903 (socket 12)
23/09/2012 22:26:57 
23/09/2012 22:26:57 Xinerama is present and active (e.g. multi-head).
23/09/2012 22:26:57 Xinerama: number of sub-screens: 1
23/09/2012 22:26:57 Xinerama: no blackouts needed (only one sub-screen)
23/09/2012 22:26:57 
23/09/2012 22:26:58 fb read rate: 10 MB/sec
23/09/2012 22:26:58 The X server says there are 10 mouse buttons.
23/09/2012 22:26:58 screen setup finished.
23/09/2012 22:26:58 
23/09/2012 22:26:58 WARNING: You are running x11vnc WITHOUT a password.  See
23/09/2012 22:26:58 WARNING: the warning message printed above for more info.
23/09/2012 22:26:58 

The VNC desktop is:      Condo:3

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

23/09/2012 22:27:00 read X11VNC_REMOTE: ans=ping:Condo:0.0

---

