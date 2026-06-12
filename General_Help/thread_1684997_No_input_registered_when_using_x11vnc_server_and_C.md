---
title: "No input registered when using x11vnc server and Chicken of the VNC"
date: 2011-02-10
forum: General Help
---

### Post by s73v3r on 2011-02-10
I'm using Ubuntu 10.04, and I'm trying to VNC into my Ubuntu box from my MBP. I can connect just fine, however, I am unable to register any mouse clicks or keyboard input on the resulting desktop. 

I'm launching it as follows:

x11vnc -nomodtweak -scale 9/10

I can log in using my Windows box and UltraVNC and use input with no problem.

---

### Post by krunge on 2011-02-10
Add -dk and -dp to the x11vnc cmdline and then watch for the keyboard and pointer events to be processed.  Is x11vnc receiving them?

Attach the FULL (no trimming) x11vnc output from that experiment to this thread and I will have a look.

---

### Post by s73v3r on 2011-02-11
Here you go. It looks like it is getting events. 

```
Last login: Wed Feb  9 20:00:44 on ttys002
Zoidberg:~ stevo$ vncviewer
-bash: vncviewer: command not found
Zoidberg:~ stevo$ ssh -l professor 192.168.1.134
professor@192.168.1.134's password: 
Linux Professor 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
6 updates are security updates.

*** System restart required ***
Last login: Fri Feb 11 00:16:28 2011 from 192.168.1.1
professor@Professor:~$ ./x11vnc-0.9.13/x11vnc/x11vnc -nomodtweak -dk -dp -scale 9/10
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
#@    http://www.karlrunge.com/x11vnc/#tunnelling            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    http://www.karlrunge.com/x11vnc/faq.html#faq-passwd    @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  'nopw' on a line in your ~/.x11vncrc file.               @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
11/02/2011 00:20:11 x11vnc version: 0.9.13 lastmod: 2011-01-02  pid: 22722
11/02/2011 00:20:11 XOpenDisplay("") failed.
11/02/2011 00:20:11 Trying again with XAUTHLOCALHOSTNAME=localhost ...
11/02/2011 00:20:11 
11/02/2011 00:20:11 *** XOpenDisplay failed. No -display or DISPLAY.
11/02/2011 00:20:11 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
11/02/2011 00:20:11 *** 1 2 3 4 
11/02/2011 00:20:15 *** XOpenDisplay of ":0" successful.
11/02/2011 00:20:15 
11/02/2011 00:20:15 Using X display :0
11/02/2011 00:20:15 rootwin: 0x106 reswin: 0x6600001 dpy: 0x1eeaa30
11/02/2011 00:20:15 
11/02/2011 00:20:15 ------------------ USEFUL INFORMATION ------------------
11/02/2011 00:20:15 
11/02/2011 00:20:15 Wireframing: -wireframe mode is in effect for window moves.
11/02/2011 00:20:15   If this yields undesired behavior (poor response, painting
11/02/2011 00:20:15   errors, etc) it may be disabled:
11/02/2011 00:20:15    - use '-nowf' to disable wireframing completely.
11/02/2011 00:20:15    - use '-nowcr' to disable the Copy Rectangle after the
11/02/2011 00:20:15      moved window is released in the new position.
11/02/2011 00:20:15   Also see the -help entry for tuning parameters.
11/02/2011 00:20:15   You can press 3 Alt_L's (Left "Alt" key) in a row to 
11/02/2011 00:20:15   repaint the screen, also see the -fixscreen option for
11/02/2011 00:20:15   periodic repaints.
11/02/2011 00:20:15   Note: '-scale' is on and this can cause more problems.
11/02/2011 00:20:15 GrabServer control via XTEST.
11/02/2011 00:20:15 
11/02/2011 00:20:15 Scroll Detection: -scrollcopyrect mode is in effect to
11/02/2011 00:20:15   use RECORD extension to try to detect scrolling windows
11/02/2011 00:20:15   (induced by either user keystroke or mouse input).
11/02/2011 00:20:15   If this yields undesired behavior (poor response, painting
11/02/2011 00:20:15   errors, etc) it may be disabled via: '-noscr'
11/02/2011 00:20:15   Also see the -help entry for tuning parameters.
11/02/2011 00:20:15   You can press 3 Alt_L's (Left "Alt" key) in a row to 
11/02/2011 00:20:15   repaint the screen, also see the -fixscreen option for
11/02/2011 00:20:15   periodic repaints.
11/02/2011 00:20:15   Note: '-scale' is on and this can cause more problems.
11/02/2011 00:20:15 X FBPM extension not supported.
11/02/2011 00:20:15 X display is capable of DPMS.
11/02/2011 00:20:15 --------------------------------------------------------
11/02/2011 00:20:15 
11/02/2011 00:20:15 Default visual ID: 0x21
11/02/2011 00:20:15 Read initial data from X display into framebuffer.
11/02/2011 00:20:15 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5120
11/02/2011 00:20:15 scaling screen: 1280x1024 -> 1152x921
11/02/2011 00:20:15 scaling screen: scale_fac_x=0.90000 scale_fac_y=0.90000
11/02/2011 00:20:15 
11/02/2011 00:20:15 X display :0.0 is 32bpp depth=24 true color
11/02/2011 00:20:15 
11/02/2011 00:20:15 Autoprobing TCP port 
11/02/2011 00:20:15 Autoprobing selected port 5900
11/02/2011 00:20:15 Listening also on IPv6 port 5900 (socket 10)
11/02/2011 00:20:15 Xinerama: Library libXinerama is not available to determine
11/02/2011 00:20:15 Xinerama: the head geometries, consider using -blackout
11/02/2011 00:20:15 Xinerama: if the screen is non-rectangular.
11/02/2011 00:20:15 fb read rate: 301 MB/sec
11/02/2011 00:20:15 fast read: reset -wait  ms to: 10
11/02/2011 00:20:15 fast read: reset -defer ms to: 10
11/02/2011 00:20:15 The X server says there are 10 mouse buttons.
11/02/2011 00:20:15 screen setup finished.
11/02/2011 00:20:15 
11/02/2011 00:20:15 WARNING: You are running x11vnc WITHOUT a password.  See
11/02/2011 00:20:15 WARNING: the warning message printed above for more info.
11/02/2011 00:20:15 

The VNC desktop is:      Professor:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

11/02/2011 00:20:33 Got connection from client 192.168.1.135
11/02/2011 00:20:33   other clients:
11/02/2011 00:20:33 Disabled X server key autorepeat.
11/02/2011 00:20:33   to force back on run: 'xset r on' (3 times)
11/02/2011 00:20:33 incr accepted_client=1 for 192.168.1.135:53592  sock=11
11/02/2011 00:20:33 Client Protocol Version 3.8
11/02/2011 00:20:33 Protocol version sent 3.8, using 3.8
11/02/2011 00:20:33 rfbProcessClientSecurityType: executing handler for type 1
11/02/2011 00:20:33 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
11/02/2011 00:20:33 XQueryPointer:     x: 188, y:  91)
11/02/2011 00:20:33 Pixel format for client 192.168.1.135:
11/02/2011 00:20:33   32 bpp, depth 24, little endian
11/02/2011 00:20:33   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
11/02/2011 00:20:33 no translation needed
11/02/2011 00:20:33 rfbProcessClientNormalMessage: ignoring unsupported encoding type zlibhex
11/02/2011 00:20:33 Using ZRLE encoding for client 192.168.1.135
11/02/2011 00:20:33 client 1 network rate 2749.0 KB/sec (13007.9 eff KB/sec)
11/02/2011 00:20:33 client 1 latency:  1.2 ms
11/02/2011 00:20:33 dt1: 0.2540, dt2: 0.0729 dt3: 0.0012 bytes: 896906
11/02/2011 00:20:33 link_rate: LR_LAN - 1 ms, 2749 KB/s
11/02/2011 00:20:33 client_set_net: 192.168.1.135  0.0155
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 896, y: 704) dx: 896 dy: 704 dt: 23.4817 t: 23.4817
11/02/2011 00:20:34 calling XTestFakeMotionEvent(995, 782)  23.4818
11/02/2011 00:20:34 XQueryPointer:     x: 995, y: 782)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 896, y: 694) dx:   0 dy: -10 dt: 0.0609 t: 23.5426
11/02/2011 00:20:34 calling XTestFakeMotionEvent(995, 771)  23.5427
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 893, y: 685) dx:  -3 dy:  -9 dt: 0.0004 t: 23.5430
11/02/2011 00:20:34 calling XTestFakeMotionEvent(992, 761)  23.5430
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 887, y: 665) dx:  -6 dy: -20 dt: 0.0015 t: 23.5445
11/02/2011 00:20:34 calling XTestFakeMotionEvent(985, 739)  23.5445
11/02/2011 00:20:34 XQueryPointer:     x: 985, y: 739)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 879, y: 634) dx:  -8 dy: -31 dt: 0.0082 t: 23.5527
11/02/2011 00:20:34 calling XTestFakeMotionEvent(976, 704)  23.5528
11/02/2011 00:20:34 XQueryPointer:     x: 976, y: 704)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 868, y: 587) dx: -11 dy: -47 dt: 0.0530 t: 23.6057
11/02/2011 00:20:34 calling XTestFakeMotionEvent(964, 652)  23.6058
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 859, y: 530) dx:  -9 dy: -57 dt: 0.0003 t: 23.6061
11/02/2011 00:20:34 calling XTestFakeMotionEvent(954, 589)  23.6061
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 852, y: 474) dx:  -7 dy: -56 dt: 0.0014 t: 23.6075
11/02/2011 00:20:34 calling XTestFakeMotionEvent(946, 527)  23.6075
11/02/2011 00:20:34 XQueryPointer:     x: 946, y: 527)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 848, y: 441) dx:  -4 dy: -33 dt: 0.0082 t: 23.6157
11/02/2011 00:20:34 calling XTestFakeMotionEvent(942, 490)  23.6157
11/02/2011 00:20:34 XQueryPointer:     x: 942, y: 490)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 843, y: 403) dx:  -5 dy: -38 dt: 0.0588 t: 23.6745
11/02/2011 00:20:34 calling XTestFakeMotionEvent(936, 448)  23.6746
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 837, y: 357) dx:  -6 dy: -46 dt: 0.0003 t: 23.6749
11/02/2011 00:20:34 calling XTestFakeMotionEvent(930, 396)  23.6749
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 834, y: 335) dx:  -3 dy: -22 dt: 0.0013 t: 23.6761
11/02/2011 00:20:34 calling XTestFakeMotionEvent(926, 372)  23.6762
11/02/2011 00:20:34 XQueryPointer:     x: 926, y: 372)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 830, y: 305) dx:  -4 dy: -30 dt: 0.0082 t: 23.6843
11/02/2011 00:20:34 calling XTestFakeMotionEvent(922, 339)  23.6844
11/02/2011 00:20:34 XQueryPointer:     x: 922, y: 339)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 828, y: 280) dx:  -2 dy: -25 dt: 0.0428 t: 23.7272
11/02/2011 00:20:34 calling XTestFakeMotionEvent(920, 311)  23.7272
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 825, y: 261) dx:  -3 dy: -19 dt: 0.0105 t: 23.7377
11/02/2011 00:20:34 calling XTestFakeMotionEvent(916, 290)  23.7377
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 823, y: 245) dx:  -2 dy: -16 dt: 0.0016 t: 23.7393
11/02/2011 00:20:34 calling XTestFakeMotionEvent(914, 272)  23.7393
11/02/2011 00:20:34 XQueryPointer:     x: 914, y: 272)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 233) dx:  -1 dy: -12 dt: 0.0446 t: 23.7838
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 259)  23.7839
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 222) dx:   0 dy: -11 dt: 0.0106 t: 23.7944
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 246)  23.7945
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 209) dx:   0 dy: -13 dt: 0.0022 t: 23.7967
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 232)  23.7967
11/02/2011 00:20:34 XQueryPointer:     x: 913, y: 232)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 196) dx:   0 dy: -13 dt: 0.0276 t: 23.8243
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 217)  23.8244
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 180) dx:   0 dy: -16 dt: 0.0106 t: 23.8349
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 200)  23.8349
11/02/2011 00:20:34 XQueryPointer:     x: 913, y: 200)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 822, y: 165) dx:   0 dy: -15 dt: 0.0100 t: 23.8449
11/02/2011 00:20:34 calling XTestFakeMotionEvent(913, 183)  23.8449
11/02/2011 00:20:34 XQueryPointer:     x: 913, y: 183)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 820, y: 154) dx:  -2 dy: -11 dt: 0.0306 t: 23.8755
11/02/2011 00:20:34 calling XTestFakeMotionEvent(911, 171)  23.8755
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 819, y: 142) dx:  -1 dy: -12 dt: 0.0003 t: 23.8757
11/02/2011 00:20:34 calling XTestFakeMotionEvent(910, 157)  23.8758
11/02/2011 00:20:34 XQueryPointer:     x: 910, y: 157)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 818, y: 134) dx:  -1 dy:  -8 dt: 0.0190 t: 23.8948
11/02/2011 00:20:34 calling XTestFakeMotionEvent(908, 148)  23.8949
11/02/2011 00:20:34 XQueryPointer:     x: 908, y: 148)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 817, y: 125) dx:  -1 dy:  -9 dt: 0.0390 t: 23.9337
11/02/2011 00:20:34 calling XTestFakeMotionEvent(907, 138)  23.9338
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 817, y: 120) dx:   0 dy:  -5 dt: 0.0003 t: 23.9341
11/02/2011 00:20:34 calling XTestFakeMotionEvent(907, 133)  23.9341
11/02/2011 00:20:34 XQueryPointer:     x: 907, y: 133)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 817, y: 118) dx:   0 dy:  -2 dt: 0.0189 t: 23.9529
11/02/2011 00:20:34 calling XTestFakeMotionEvent(907, 131)  23.9530
11/02/2011 00:20:34 XQueryPointer:     x: 907, y: 131)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 817, y: 117) dx:   0 dy:  -1 dt: 0.0663 t: 24.0192
11/02/2011 00:20:34 calling XTestFakeMotionEvent(907, 130)  24.0193
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 817, y: 116) dx:   0 dy:  -1 dt: 0.0003 t: 24.0196
11/02/2011 00:20:34 calling XTestFakeMotionEvent(907, 128)  24.0196
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 819, y: 114) dx:   2 dy:  -2 dt: 0.0013 t: 24.0209
11/02/2011 00:20:34 calling XTestFakeMotionEvent(910, 126)  24.0209
11/02/2011 00:20:34 XQueryPointer:     x: 910, y: 126)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 821, y: 109) dx:   2 dy:  -5 dt: 0.0191 t: 24.0400
11/02/2011 00:20:34 calling XTestFakeMotionEvent(912, 121)  24.0400
11/02/2011 00:20:34 XQueryPointer:     x: 912, y: 121)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 827, y:  94) dx:   6 dy: -15 dt: 0.0596 t: 24.0996
11/02/2011 00:20:34 calling XTestFakeMotionEvent(918, 104)  24.0996
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 835, y:  71) dx:   8 dy: -23 dt: 0.0107 t: 24.1102
11/02/2011 00:20:34 calling XTestFakeMotionEvent(927, 78)  24.1103
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 840, y:  53) dx:   5 dy: -18 dt: 0.0011 t: 24.1114
11/02/2011 00:20:34 calling XTestFakeMotionEvent(933, 58)  24.1114
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 847, y:  33) dx:   7 dy: -20 dt: 0.0002 t: 24.1116
11/02/2011 00:20:34 calling XTestFakeMotionEvent(941, 36)  24.1116
11/02/2011 00:20:34 XQueryPointer:     x: 941, y:  36)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 853, y:  21) dx:   6 dy: -12 dt: 0.0114 t: 24.1230
11/02/2011 00:20:34 calling XTestFakeMotionEvent(947, 23)  24.1231
11/02/2011 00:20:34 XQueryPointer:     x: 947, y:  23)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 858, y:  16) dx:   5 dy:  -5 dt: 0.0571 t: 24.1801
11/02/2011 00:20:34 calling XTestFakeMotionEvent(953, 17)  24.1802
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 863, y:  12) dx:   5 dy:  -4 dt: 0.0003 t: 24.1804
11/02/2011 00:20:34 calling XTestFakeMotionEvent(958, 13)  24.1804
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 867, y:   9) dx:   4 dy:  -3 dt: 0.0015 t: 24.1819
11/02/2011 00:20:34 calling XTestFakeMotionEvent(963, 10)  24.1819
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 869, y:   9) dx:   2 dy:   0 dt: 0.0013 t: 24.1831
11/02/2011 00:20:34 calling XTestFakeMotionEvent(965, 10)  24.1832
11/02/2011 00:20:34 XQueryPointer:     x: 965, y:  10)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 871, y:   8) dx:   2 dy:  -1 dt: 0.0175 t: 24.2007
11/02/2011 00:20:34 calling XTestFakeMotionEvent(967, 8)  24.2008
11/02/2011 00:20:34 XQueryPointer:     x: 967, y:   8)
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 873, y:   8) dx:   2 dy:   0 dt: 0.0553 t: 24.2560
11/02/2011 00:20:34 calling XTestFakeMotionEvent(970, 8)  24.2561
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 874, y:   8) dx:   1 dy:   0 dt: 0.0003 t: 24.2563
11/02/2011 00:20:34 calling XTestFakeMotionEvent(971, 8)  24.2564
11/02/2011 00:20:34 # pointer(mask: 0x0, x: 875, y:   8) dx:   1 dy:   0 dt: 0.0014 t: 24.2577
11/02/2011 00:20:34 calling XTestFakeMotionEvent(972, 8)  24.2578
11/02/2011 00:20:34 XQueryPointer:     x: 972, y:   8)
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   6) dx:   0 dy:  -2 dt: 0.2684 t: 24.5261
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 6)  24.5262
11/02/2011 00:20:35 XQueryPointer:     x: 972, y:   6)
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   5) dx:   0 dy:  -1 dt: 0.0111 t: 24.5372
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 5)  24.5372
11/02/2011 00:20:35 XQueryPointer:     x: 972, y:   5)
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   4) dx:   0 dy:  -1 dt: 0.0564 t: 24.5936
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 4)  24.5937
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   3) dx:   0 dy:  -1 dt: 0.0106 t: 24.6042
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 3)  24.6042
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   2) dx:   0 dy:  -1 dt: 0.0027 t: 24.6069
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 2)  24.6069
11/02/2011 00:20:35 XQueryPointer:     x: 972, y:   2)
11/02/2011 00:20:35 # pointer(mask: 0x0, x: 875, y:   1) dx:   0 dy:  -1 dt: 0.0070 t: 24.6139
11/02/2011 00:20:35 calling XTestFakeMotionEvent(972, 1)  24.6139
11/02/2011 00:20:35 XQueryPointer:     x: 972, y:   1)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 857, y:   3) dx: -18 dy:   2 dt: 3.3639 t: 27.9778
11/02/2011 00:20:38 calling XTestFakeMotionEvent(952, 3)  27.9779
11/02/2011 00:20:38 XQueryPointer:     x: 952, y:   3)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 856, y:   5) dx:  -1 dy:   2 dt: 0.0199 t: 27.9977
11/02/2011 00:20:38 calling XTestFakeMotionEvent(951, 5)  27.9978
11/02/2011 00:20:38 XQueryPointer:     x: 951, y:   5)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 856, y:   6) dx:   0 dy:   1 dt: 0.0480 t: 28.0457
11/02/2011 00:20:38 calling XTestFakeMotionEvent(951, 6)  28.0458
11/02/2011 00:20:38 XQueryPointer:     x: 951, y:   6)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 856, y:   5) dx:   0 dy:  -1 dt: 0.1727 t: 28.2184
11/02/2011 00:20:38 calling XTestFakeMotionEvent(951, 5)  28.2185
11/02/2011 00:20:38 XQueryPointer:     x: 951, y:   5)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 856, y:   4) dx:   0 dy:  -1 dt: 0.0677 t: 28.2861
11/02/2011 00:20:38 calling XTestFakeMotionEvent(951, 4)  28.2862
11/02/2011 00:20:38 XQueryPointer:     x: 951, y:   4)
11/02/2011 00:20:38 # pointer(mask: 0x0, x: 855, y:   3) dx:  -1 dy:  -1 dt: 0.0652 t: 28.3513
11/02/2011 00:20:38 calling XTestFakeMotionEvent(950, 3)  28.3513
11/02/2011 00:20:39 XQueryPointer:     x: 950, y:   3)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 853, y:   3) dx:  -2 dy:   0 dt: 0.0176 t: 28.3689
11/02/2011 00:20:39 calling XTestFakeMotionEvent(947, 3)  28.3689
11/02/2011 00:20:39 XQueryPointer:     x: 947, y:   3)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 850, y:   3) dx:  -3 dy:   0 dt: 0.0496 t: 28.4185
11/02/2011 00:20:39 calling XTestFakeMotionEvent(944, 3)  28.4186
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 844, y:   7) dx:  -6 dy:   4 dt: 0.0003 t: 28.4188
11/02/2011 00:20:39 calling XTestFakeMotionEvent(937, 7)  28.4188
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 835, y:  13) dx:  -9 dy:   6 dt: 0.0014 t: 28.4202
11/02/2011 00:20:39 calling XTestFakeMotionEvent(927, 14)  28.4203
11/02/2011 00:20:39 XQueryPointer:     x: 927, y:  14)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 828, y:  19) dx:  -7 dy:   6 dt: 0.0083 t: 28.4286
11/02/2011 00:20:39 calling XTestFakeMotionEvent(920, 21)  28.4286
11/02/2011 00:20:39 XQueryPointer:     x: 920, y:  21)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 824, y:  24) dx:  -4 dy:   5 dt: 0.0563 t: 28.4849
11/02/2011 00:20:39 calling XTestFakeMotionEvent(915, 26)  28.4850
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 819, y:  29) dx:  -5 dy:   5 dt: 0.0106 t: 28.4955
11/02/2011 00:20:39 calling XTestFakeMotionEvent(910, 32)  28.4956
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 816, y:  33) dx:  -3 dy:   4 dt: 0.0002 t: 28.4957
11/02/2011 00:20:39 calling XTestFakeMotionEvent(906, 36)  28.4958
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 812, y:  38) dx:  -4 dy:   5 dt: 0.0022 t: 28.4980
11/02/2011 00:20:39 calling XTestFakeMotionEvent(902, 42)  28.4980
11/02/2011 00:20:39 XQueryPointer:     x: 902, y:  42)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 809, y:  42) dx:  -3 dy:   4 dt: 0.0458 t: 28.5437
11/02/2011 00:20:39 calling XTestFakeMotionEvent(898, 46)  28.5438
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 804, y:  48) dx:  -5 dy:   6 dt: 0.0003 t: 28.5440
11/02/2011 00:20:39 calling XTestFakeMotionEvent(893, 53)  28.5441
11/02/2011 00:20:39 XQueryPointer:     x: 893, y:  53)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 797, y:  58) dx:  -7 dy:  10 dt: 0.0400 t: 28.5840
11/02/2011 00:20:39 calling XTestFakeMotionEvent(885, 64)  28.5841
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 791, y:  67) dx:  -6 dy:   9 dt: 0.0003 t: 28.5844
11/02/2011 00:20:39 calling XTestFakeMotionEvent(878, 74)  28.5844
11/02/2011 00:20:39 XQueryPointer:     x: 878, y:  74)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 786, y:  76) dx:  -5 dy:   9 dt: 0.0396 t: 28.6239
11/02/2011 00:20:39 calling XTestFakeMotionEvent(873, 84)  28.6240
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 782, y:  83) dx:  -4 dy:   7 dt: 0.0003 t: 28.6242
11/02/2011 00:20:39 calling XTestFakeMotionEvent(868, 92)  28.6243
11/02/2011 00:20:39 XQueryPointer:     x: 868, y:  92)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 777, y:  95) dx:  -5 dy:  12 dt: 0.0389 t: 28.6632
11/02/2011 00:20:39 calling XTestFakeMotionEvent(863, 105)  28.6633
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 774, y: 101) dx:  -3 dy:   6 dt: 0.0003 t: 28.6635
11/02/2011 00:20:39 calling XTestFakeMotionEvent(860, 112)  28.6635
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 769, y: 109) dx:  -5 dy:   8 dt: 0.0002 t: 28.6637
11/02/2011 00:20:39 calling XTestFakeMotionEvent(854, 121)  28.6637
11/02/2011 00:20:39 XQueryPointer:     x: 854, y: 121)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 767, y: 113) dx:  -2 dy:   4 dt: 0.0388 t: 28.7024
11/02/2011 00:20:39 calling XTestFakeMotionEvent(852, 125)  28.7025
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 764, y: 121) dx:  -3 dy:   8 dt: 0.0003 t: 28.7027
11/02/2011 00:20:39 calling XTestFakeMotionEvent(848, 134)  28.7028
11/02/2011 00:20:39 XQueryPointer:     x: 848, y: 134)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 762, y: 127) dx:  -2 dy:   6 dt: 0.0395 t: 28.7422
11/02/2011 00:20:39 calling XTestFakeMotionEvent(846, 141)  28.7423
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 760, y: 132) dx:  -2 dy:   5 dt: 0.0003 t: 28.7426
11/02/2011 00:20:39 calling XTestFakeMotionEvent(844, 146)  28.7426
11/02/2011 00:20:39 XQueryPointer:     x: 844, y: 146)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 759, y: 137) dx:  -1 dy:   5 dt: 0.0279 t: 28.7705
11/02/2011 00:20:39 calling XTestFakeMotionEvent(843, 152)  28.7706
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 757, y: 141) dx:  -2 dy:   4 dt: 0.0106 t: 28.7811
11/02/2011 00:20:39 calling XTestFakeMotionEvent(841, 156)  28.7811
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 756, y: 146) dx:  -1 dy:   5 dt: 0.0002 t: 28.7814
11/02/2011 00:20:39 calling XTestFakeMotionEvent(840, 162)  28.7814
11/02/2011 00:20:39 XQueryPointer:     x: 840, y: 162)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 755, y: 150) dx:  -1 dy:   4 dt: 0.0209 t: 28.8022
11/02/2011 00:20:39 calling XTestFakeMotionEvent(838, 166)  28.8023
11/02/2011 00:20:39 XQueryPointer:     x: 838, y: 166)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 154) dx:  -1 dy:   4 dt: 0.0185 t: 28.8207
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 171)  28.8208
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 156) dx:   0 dy:   2 dt: 0.0106 t: 28.8313
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 173)  28.8314
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 173)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 158) dx:   0 dy:   2 dt: 0.0210 t: 28.8523
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 175)  28.8524
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 175)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 159) dx:   0 dy:   1 dt: 0.0290 t: 28.8813
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 176)  28.8814
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 160) dx:   0 dy:   1 dt: 0.0003 t: 28.8816
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 177)  28.8816
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 177)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 162) dx:   0 dy:   2 dt: 0.0277 t: 28.9093
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 180)  28.9093
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 180)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 163) dx:   0 dy:   1 dt: 0.0385 t: 28.9477
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 181)  28.9478
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 181)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 162) dx:   0 dy:  -1 dt: 0.1644 t: 29.1121
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 180)  29.1122
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 180)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 754, y: 160) dx:   0 dy:  -2 dt: 0.0199 t: 29.1320
11/02/2011 00:20:39 calling XTestFakeMotionEvent(837, 177)  29.1321
11/02/2011 00:20:39 XQueryPointer:     x: 837, y: 177)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 752, y: 158) dx:  -2 dy:  -2 dt: 0.0543 t: 29.1863
11/02/2011 00:20:39 calling XTestFakeMotionEvent(835, 175)  29.1863
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 747, y: 154) dx:  -5 dy:  -4 dt: 0.0003 t: 29.1866
11/02/2011 00:20:39 calling XTestFakeMotionEvent(830, 171)  29.1866
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 739, y: 150) dx:  -8 dy:  -4 dt: 0.0015 t: 29.1881
11/02/2011 00:20:39 calling XTestFakeMotionEvent(821, 166)  29.1881
11/02/2011 00:20:39 XQueryPointer:     x: 821, y: 166)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 731, y: 146) dx:  -8 dy:  -4 dt: 0.0081 t: 29.1962
11/02/2011 00:20:39 calling XTestFakeMotionEvent(812, 162)  29.1962
11/02/2011 00:20:39 XQueryPointer:     x: 812, y: 162)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 724, y: 140) dx:  -7 dy:  -6 dt: 0.0594 t: 29.2556
11/02/2011 00:20:39 calling XTestFakeMotionEvent(804, 155)  29.2557
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 719, y: 136) dx:  -5 dy:  -4 dt: 0.0104 t: 29.2661
11/02/2011 00:20:39 calling XTestFakeMotionEvent(798, 151)  29.2661
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 717, y: 133) dx:  -2 dy:  -3 dt: 0.0002 t: 29.2663
11/02/2011 00:20:39 calling XTestFakeMotionEvent(796, 147)  29.2663
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 716, y: 130) dx:  -1 dy:  -3 dt: 0.0014 t: 29.2677
11/02/2011 00:20:39 calling XTestFakeMotionEvent(795, 144)  29.2678
11/02/2011 00:20:39 XQueryPointer:     x: 795, y: 144)
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 716, y: 129) dx:   0 dy:  -1 dt: 0.0465 t: 29.3142
11/02/2011 00:20:39 calling XTestFakeMotionEvent(795, 143)  29.3143
11/02/2011 00:20:39 # pointer(mask: 0x0, x: 716, y: 128) dx:   0 dy:  -1 dt: 0.0003 t: 29.3145
11/02/2011 00:20:39 calling XTestFakeMotionEvent(795, 142)  29.3146
11/02/2011 00:20:39 XQueryPointer:     x: 795, y: 142)
11/02/2011 00:20:40 # pointer(mask: 0x1, x: 716, y: 128) dx:   0 dy:   0 dt: 0.6123 t: 29.9268
11/02/2011 00:20:40 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:40 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:40 calling XTestFakeButtonEvent(1, 1)  29.9275
11/02/2011 00:20:40 # pointer(mask: 0x0, x: 716, y: 128) dx:   0 dy:   0 dt: 0.0014 t: 29.9283
11/02/2011 00:20:40 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:40 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:40 calling XTestFakeButtonEvent(1, 0)  29.9284
11/02/2011 00:20:41 # keyboard(down, 0xff0d "Return") uip=0  31.2413
11/02/2011 00:20:41 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:41 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", down)
11/02/2011 00:20:41 calling XTestFakeKeyEvent(36, 1)  31.2424
11/02/2011 00:20:42 # keyboard(up, 0xff0d "Return") uip=0  31.3598
11/02/2011 00:20:42 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:42 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", up)
11/02/2011 00:20:42 calling XTestFakeKeyEvent(36, 0)  31.3599
11/02/2011 00:20:43 created selwin: 0x660002c
11/02/2011 00:20:43 # keyboard(down, 0xff0d "Return") uip=0  32.5267
11/02/2011 00:20:43 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:43 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", down)
11/02/2011 00:20:43 calling XTestFakeKeyEvent(36, 1)  32.5272
11/02/2011 00:20:43 # keyboard(up, 0xff0d "Return") uip=0  32.6303
11/02/2011 00:20:43 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:43 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", up)
11/02/2011 00:20:43 calling XTestFakeKeyEvent(36, 0)  32.6305
11/02/2011 00:20:43 # pointer(mask: 0x0, x: 715, y: 128) dx:  -1 dy:   0 dt: 3.3794 t: 33.3076
11/02/2011 00:20:43 calling XTestFakeMotionEvent(794, 142)  33.3077
11/02/2011 00:20:43 XQueryPointer:     x: 794, y: 142)
11/02/2011 00:20:43 # pointer(mask: 0x0, x: 711, y: 128) dx:  -4 dy:   0 dt: 0.0200 t: 33.3276
11/02/2011 00:20:43 calling XTestFakeMotionEvent(790, 142)  33.3277
11/02/2011 00:20:43 XQueryPointer:     x: 790, y: 142)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 705, y: 129) dx:  -6 dy:   1 dt: 0.0479 t: 33.3755
11/02/2011 00:20:44 calling XTestFakeMotionEvent(783, 143)  33.3756
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 699, y: 131) dx:  -6 dy:   2 dt: 0.0105 t: 33.3861
11/02/2011 00:20:44 calling XTestFakeMotionEvent(776, 145)  33.3861
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 687, y: 136) dx: -12 dy:   5 dt: 0.0027 t: 33.3888
11/02/2011 00:20:44 calling XTestFakeMotionEvent(763, 151)  33.3888
11/02/2011 00:20:44 XQueryPointer:     x: 763, y: 151)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 658, y: 146) dx: -29 dy:  10 dt: 0.0070 t: 33.3958
11/02/2011 00:20:44 calling XTestFakeMotionEvent(731, 162)  33.3958
11/02/2011 00:20:44 XQueryPointer:     x: 731, y: 162)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 635, y: 149) dx: -23 dy:   3 dt: 0.0203 t: 33.4161
11/02/2011 00:20:44 calling XTestFakeMotionEvent(705, 165)  33.4161
11/02/2011 00:20:44 XQueryPointer:     x: 705, y: 165)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 604, y: 152) dx: -31 dy:   3 dt: 0.0193 t: 33.4354
11/02/2011 00:20:44 calling XTestFakeMotionEvent(671, 168)  33.4355
11/02/2011 00:20:44 XQueryPointer:     x: 671, y: 168)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 560, y: 154) dx: -44 dy:   2 dt: 0.0392 t: 33.4746
11/02/2011 00:20:44 calling XTestFakeMotionEvent(622, 171)  33.4746
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 538, y: 154) dx: -22 dy:   0 dt: 0.0003 t: 33.4749
11/02/2011 00:20:44 calling XTestFakeMotionEvent(597, 171)  33.4749
11/02/2011 00:20:44 XQueryPointer:     x: 597, y: 171)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 496, y: 150) dx: -42 dy:  -4 dt: 0.0195 t: 33.4944
11/02/2011 00:20:44 calling XTestFakeMotionEvent(551, 166)  33.4944
11/02/2011 00:20:44 XQueryPointer:     x: 551, y: 166)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 461, y: 143) dx: -35 dy:  -7 dt: 0.0324 t: 33.5267
11/02/2011 00:20:44 calling XTestFakeMotionEvent(512, 158)  33.5268
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 439, y: 137) dx: -22 dy:  -6 dt: 0.0003 t: 33.5271
11/02/2011 00:20:44 calling XTestFakeMotionEvent(487, 152)  33.5271
11/02/2011 00:20:44 XQueryPointer:     x: 487, y: 152)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 413, y: 128) dx: -26 dy:  -9 dt: 0.0187 t: 33.5457
11/02/2011 00:20:44 calling XTestFakeMotionEvent(458, 142)  33.5459
11/02/2011 00:20:44 XQueryPointer:     x: 458, y: 142)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 396, y: 120) dx: -17 dy:  -8 dt: 0.0388 t: 33.5845
11/02/2011 00:20:44 calling XTestFakeMotionEvent(440, 133)  33.5846
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 379, y: 112) dx: -17 dy:  -8 dt: 0.0003 t: 33.5848
11/02/2011 00:20:44 calling XTestFakeMotionEvent(421, 124)  33.5848
11/02/2011 00:20:44 XQueryPointer:     x: 421, y: 124)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 367, y: 107) dx: -12 dy:  -5 dt: 0.0188 t: 33.6037
11/02/2011 00:20:44 calling XTestFakeMotionEvent(407, 118)  33.6037
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 356, y: 102) dx: -11 dy:  -5 dt: 0.0106 t: 33.6143
11/02/2011 00:20:44 calling XTestFakeMotionEvent(395, 113)  33.6143
11/02/2011 00:20:44 XQueryPointer:     x: 395, y: 113)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 348, y:  98) dx:  -8 dy:  -4 dt: 0.0205 t: 33.6348
11/02/2011 00:20:44 calling XTestFakeMotionEvent(386, 108)  33.6348
11/02/2011 00:20:44 XQueryPointer:     x: 386, y: 108)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 342, y:  94) dx:  -6 dy:  -4 dt: 0.0178 t: 33.6525
11/02/2011 00:20:44 calling XTestFakeMotionEvent(380, 104)  33.6526
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 333, y:  88) dx:  -9 dy:  -6 dt: 0.0106 t: 33.6632
11/02/2011 00:20:44 calling XTestFakeMotionEvent(370, 97)  33.6632
11/02/2011 00:20:44 XQueryPointer:     x: 370, y:  97)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 327, y:  82) dx:  -6 dy:  -6 dt: 0.0206 t: 33.6837
11/02/2011 00:20:44 calling XTestFakeMotionEvent(363, 91)  33.6838
11/02/2011 00:20:44 XQueryPointer:     x: 363, y:  91)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 322, y:  76) dx:  -5 dy:  -6 dt: 0.0185 t: 33.7022
11/02/2011 00:20:44 calling XTestFakeMotionEvent(357, 84)  33.7023
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 320, y:  72) dx:  -2 dy:  -4 dt: 0.0106 t: 33.7128
11/02/2011 00:20:44 calling XTestFakeMotionEvent(355, 80)  33.7129
11/02/2011 00:20:44 XQueryPointer:     x: 355, y:  80)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 317, y:  67) dx:  -3 dy:  -5 dt: 0.0204 t: 33.7332
11/02/2011 00:20:44 calling XTestFakeMotionEvent(352, 74)  33.7333
11/02/2011 00:20:44 XQueryPointer:     x: 352, y:  74)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 316, y:  64) dx:  -1 dy:  -3 dt: 0.0186 t: 33.7518
11/02/2011 00:20:44 calling XTestFakeMotionEvent(351, 71)  33.7519
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  62) dx:  -1 dy:  -2 dt: 0.0106 t: 33.7624
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 68)  33.7625
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  68)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  60) dx:   0 dy:  -2 dt: 0.0207 t: 33.7832
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 66)  33.7832
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  66)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  59) dx:   0 dy:  -1 dt: 0.0180 t: 33.8012
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 65)  33.8012
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  65)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  58) dx:   0 dy:  -1 dt: 0.0387 t: 33.8398
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 64)  33.8399
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  64)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  57) dx:   0 dy:  -1 dt: 0.0113 t: 33.8511
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 63)  33.8512
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  63)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  56) dx:   0 dy:  -1 dt: 0.0991 t: 33.9502
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 62)  33.9503
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  62)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  54) dx:   0 dy:  -2 dt: 0.0107 t: 33.9608
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 60)  33.9609
11/02/2011 00:20:44 XQueryPointer:     x: 350, y:  60)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  52) dx:   0 dy:  -2 dt: 0.0548 t: 34.0157
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 57)  34.0157
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  49) dx:   0 dy:  -3 dt: 0.0104 t: 34.0261
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 54)  34.0261
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 315, y:  47) dx:   0 dy:  -2 dt: 0.0005 t: 34.0265
11/02/2011 00:20:44 calling XTestFakeMotionEvent(350, 52)  34.0267
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 316, y:  45) dx:   1 dy:  -2 dt: 0.0027 t: 34.0292
11/02/2011 00:20:44 calling XTestFakeMotionEvent(351, 50)  34.0293
11/02/2011 00:20:44 XQueryPointer:     x: 351, y:  50)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 316, y:  43) dx:   0 dy:  -2 dt: 0.0362 t: 34.0654
11/02/2011 00:20:44 calling XTestFakeMotionEvent(351, 47)  34.0655
11/02/2011 00:20:44 XQueryPointer:     x: 351, y:  47)
11/02/2011 00:20:44 # pointer(mask: 0x0, x: 316, y:  42) dx:   0 dy:  -1 dt: 0.0632 t: 34.1286
11/02/2011 00:20:44 calling XTestFakeMotionEvent(351, 46)  34.1287
11/02/2011 00:20:44 XQueryPointer:     x: 351, y:  46)
11/02/2011 00:20:45 # pointer(mask: 0x1, x: 316, y:  42) dx:   0 dy:   0 dt: 0.3084 t: 34.4369
11/02/2011 00:20:45 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:45 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:45 calling XTestFakeButtonEvent(1, 1)  34.4375
11/02/2011 00:20:45 # pointer(mask: 0x0, x: 316, y:  42) dx:   0 dy:   0 dt: 0.3040 t: 34.7409
11/02/2011 00:20:45 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:45 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:45 calling XTestFakeButtonEvent(1, 0)  34.7410
11/02/2011 00:20:45 # pointer(mask: 0x1, x: 316, y:  42) dx:   0 dy:   0 dt: 0.5444 t: 35.2853
11/02/2011 00:20:45 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:45 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:45 calling XTestFakeButtonEvent(1, 1)  35.2861
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 321, y:  42) dx:   5 dy:   0 dt: 0.2616 t: 35.5470
11/02/2011 00:20:46 calling XTestFakeMotionEvent(356, 46)  35.5470
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 336, y:  42) dx:  15 dy:   0 dt: 0.0509 t: 35.5979
11/02/2011 00:20:46 calling XTestFakeMotionEvent(373, 46)  35.5980
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 365, y:  42) dx:  29 dy:   0 dt: 0.0005 t: 35.5984
11/02/2011 00:20:46 calling XTestFakeMotionEvent(405, 46)  35.5984
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 394, y:  45) dx:  29 dy:   3 dt: 0.0257 t: 35.6241
11/02/2011 00:20:46 calling XTestFakeMotionEvent(437, 50)  35.6241
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 416, y:  48) dx:  22 dy:   3 dt: 0.0004 t: 35.6244
11/02/2011 00:20:46 calling XTestFakeMotionEvent(462, 53)  35.6245
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 426, y:  49) dx:  10 dy:   1 dt: 0.0275 t: 35.6519
11/02/2011 00:20:46 calling XTestFakeMotionEvent(473, 54)  35.6520
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 442, y:  51) dx:  16 dy:   2 dt: 0.0004 t: 35.6523
11/02/2011 00:20:46 calling XTestFakeMotionEvent(491, 56)  35.6524
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 456, y:  52) dx:  14 dy:   1 dt: 0.0270 t: 35.6793
11/02/2011 00:20:46 calling XTestFakeMotionEvent(506, 57)  35.6794
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 466, y:  54) dx:  10 dy:   2 dt: 0.0004 t: 35.6797
11/02/2011 00:20:46 calling XTestFakeMotionEvent(517, 60)  35.6798
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 472, y:  55) dx:   6 dy:   1 dt: 0.0269 t: 35.7067
11/02/2011 00:20:46 calling XTestFakeMotionEvent(524, 61)  35.7067
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 476, y:  56) dx:   4 dy:   1 dt: 0.0051 t: 35.7118
11/02/2011 00:20:46 calling XTestFakeMotionEvent(528, 62)  35.7119
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 479, y:  56) dx:   3 dy:   0 dt: 0.0277 t: 35.7395
11/02/2011 00:20:46 calling XTestFakeMotionEvent(532, 62)  35.7396
11/02/2011 00:20:46 # pointer(mask: 0x1, x: 480, y:  57) dx:   1 dy:   1 dt: 0.0058 t: 35.7454
11/02/2011 00:20:46 calling XTestFakeMotionEvent(533, 63)  35.7454
11/02/2011 00:20:46 XQueryPointer:     x: 533, y:  63)
11/02/2011 00:20:46 # pointer(mask: 0x0, x: 480, y:  57) dx:   0 dy:   0 dt: 0.1678 t: 35.9131
11/02/2011 00:20:46 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:46 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:46 calling XTestFakeButtonEvent(1, 0)  35.9133
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 481, y:  57) dx:   1 dy:   0 dt: 1.4883 t: 37.4014
11/02/2011 00:20:48 calling XTestFakeMotionEvent(534, 63)  37.4015
11/02/2011 00:20:48 XQueryPointer:     x: 534, y:  63)
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 486, y:  57) dx:   5 dy:   0 dt: 0.0196 t: 37.4211
11/02/2011 00:20:48 calling XTestFakeMotionEvent(540, 63)  37.4211
11/02/2011 00:20:48 XQueryPointer:     x: 540, y:  63)
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 497, y:  61) dx:  11 dy:   4 dt: 0.0437 t: 37.4648
11/02/2011 00:20:48 calling XTestFakeMotionEvent(552, 67)  37.4649
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 510, y:  65) dx:  13 dy:   4 dt: 0.0106 t: 37.4754
11/02/2011 00:20:48 calling XTestFakeMotionEvent(566, 72)  37.4755
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 525, y:  70) dx:  15 dy:   5 dt: 0.0014 t: 37.4769
11/02/2011 00:20:48 calling XTestFakeMotionEvent(583, 77)  37.4769
11/02/2011 00:20:48 XQueryPointer:     x: 583, y:  77)
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 541, y:  75) dx:  16 dy:   5 dt: 0.0486 t: 37.5254
11/02/2011 00:20:48 calling XTestFakeMotionEvent(601, 83)  37.5255
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 557, y:  79) dx:  16 dy:   4 dt: 0.0106 t: 37.5361
11/02/2011 00:20:48 calling XTestFakeMotionEvent(618, 87)  37.5361
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 570, y:  82) dx:  13 dy:   3 dt: 0.0005 t: 37.5365
11/02/2011 00:20:48 calling XTestFakeMotionEvent(633, 91)  37.5367
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 579, y:  84) dx:   9 dy:   2 dt: 0.0026 t: 37.5391
11/02/2011 00:20:48 calling XTestFakeMotionEvent(643, 93)  37.5392
11/02/2011 00:20:48 XQueryPointer:     x: 643, y:  93)
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 596, y:  88) dx:  17 dy:   4 dt: 0.0623 t: 37.6014
11/02/2011 00:20:48 calling XTestFakeMotionEvent(662, 97)  37.6015
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 605, y:  91) dx:   9 dy:   3 dt: 0.0106 t: 37.6121
11/02/2011 00:20:48 calling XTestFakeMotionEvent(672, 101)  37.6121
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 610, y:  93) dx:   5 dy:   2 dt: 0.0003 t: 37.6123
11/02/2011 00:20:48 calling XTestFakeMotionEvent(677, 103)  37.6123
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 617, y:  97) dx:   7 dy:   4 dt: 0.0015 t: 37.6138
11/02/2011 00:20:48 calling XTestFakeMotionEvent(685, 107)  37.6138
11/02/2011 00:20:48 XQueryPointer:     x: 685, y: 107)
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 619, y:  98) dx:   2 dy:   1 dt: 0.0600 t: 37.6738
11/02/2011 00:20:48 calling XTestFakeMotionEvent(687, 108)  37.6739
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 622, y:  99) dx:   3 dy:   1 dt: 0.0003 t: 37.6741
11/02/2011 00:20:48 calling XTestFakeMotionEvent(691, 110)  37.6742
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 623, y: 100) dx:   1 dy:   1 dt: 0.0002 t: 37.6743
11/02/2011 00:20:48 calling XTestFakeMotionEvent(692, 111)  37.6744
11/02/2011 00:20:48 XQueryPointer:     x: 692, y: 111)
11/02/2011 00:20:48 # pointer(mask: 0x1, x: 623, y: 100) dx:   0 dy:   0 dt: 0.4194 t: 38.0938
11/02/2011 00:20:48 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:48 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:48 calling XTestFakeButtonEvent(1, 1)  38.0944
11/02/2011 00:20:48 # pointer(mask: 0x0, x: 623, y: 100) dx:   0 dy:   0 dt: 0.0108 t: 38.1046
11/02/2011 00:20:48 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:48 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:48 calling XTestFakeButtonEvent(1, 0)  38.1047
11/02/2011 00:20:50 # keyboard(down, 0xff0d "Return") uip=0  39.4237
11/02/2011 00:20:50 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:50 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", down)
11/02/2011 00:20:50 calling XTestFakeKeyEvent(36, 1)  39.4242
11/02/2011 00:20:50 # keyboard(up, 0xff0d "Return") uip=0  39.5348
11/02/2011 00:20:50 keyboard(): KeySym 0xff0d "Return" -> KeyCode 0x24
11/02/2011 00:20:50 XTestFakeKeyEvent(dpy, keycode=0x24 "Return", up)
11/02/2011 00:20:50 calling XTestFakeKeyEvent(36, 0)  39.5349
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 621, y: 101) dx:  -2 dy:   1 dt: 2.0782 t: 40.1828
11/02/2011 00:20:50 calling XTestFakeMotionEvent(690, 112)  40.1829
11/02/2011 00:20:50 XQueryPointer:     x: 690, y: 112)
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 612, y: 101) dx:  -9 dy:   0 dt: 0.0101 t: 40.1929
11/02/2011 00:20:50 calling XTestFakeMotionEvent(680, 112)  40.1930
11/02/2011 00:20:50 XQueryPointer:     x: 680, y: 112)
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 595, y: 101) dx: -17 dy:   0 dt: 0.0701 t: 40.2629
11/02/2011 00:20:50 calling XTestFakeMotionEvent(661, 112)  40.2630
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 567, y:  98) dx: -28 dy:  -3 dt: 0.0003 t: 40.2633
11/02/2011 00:20:50 calling XTestFakeMotionEvent(630, 108)  40.2633
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 532, y:  84) dx: -35 dy: -14 dt: 0.0002 t: 40.2634
11/02/2011 00:20:50 calling XTestFakeMotionEvent(591, 93)  40.2635
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 492, y:  68) dx: -40 dy: -16 dt: 0.0015 t: 40.2649
11/02/2011 00:20:50 calling XTestFakeMotionEvent(546, 75)  40.2650
11/02/2011 00:20:50 XQueryPointer:     x: 546, y:  75)
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 465, y:  58) dx: -27 dy: -10 dt: 0.0090 t: 40.2739
11/02/2011 00:20:50 calling XTestFakeMotionEvent(516, 64)  40.2740
11/02/2011 00:20:50 XQueryPointer:     x: 516, y:  64)
11/02/2011 00:20:50 # pointer(mask: 0x0, x: 414, y:  46) dx: -51 dy: -12 dt: 0.0673 t: 40.3412
11/02/2011 00:20:50 calling XTestFakeMotionEvent(460, 51)  40.3413
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 389, y:  42) dx: -25 dy:  -4 dt: 0.0106 t: 40.3518
11/02/2011 00:20:51 calling XTestFakeMotionEvent(432, 46)  40.3518
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 357, y:  40) dx: -32 dy:  -2 dt: 0.0006 t: 40.3524
11/02/2011 00:20:51 calling XTestFakeMotionEvent(396, 44)  40.3525
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 327, y:  37) dx: -30 dy:  -3 dt: 0.0014 t: 40.3538
11/02/2011 00:20:51 calling XTestFakeMotionEvent(363, 41)  40.3539
11/02/2011 00:20:51 XQueryPointer:     x: 363, y:  41)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 302, y:  35) dx: -25 dy:  -2 dt: 0.0191 t: 40.3729
11/02/2011 00:20:51 calling XTestFakeMotionEvent(335, 38)  40.3729
11/02/2011 00:20:51 XQueryPointer:     x: 335, y:  38)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 279, y:  31) dx: -23 dy:  -4 dt: 0.0390 t: 40.4119
11/02/2011 00:20:51 calling XTestFakeMotionEvent(310, 34)  40.4120
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 261, y:  26) dx: -18 dy:  -5 dt: 0.0005 t: 40.4125
11/02/2011 00:20:51 calling XTestFakeMotionEvent(290, 28)  40.4125
11/02/2011 00:20:51 XQueryPointer:     x: 290, y:  28)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 245, y:  23) dx: -16 dy:  -3 dt: 0.0129 t: 40.4254
11/02/2011 00:20:51 calling XTestFakeMotionEvent(272, 25)  40.4254
11/02/2011 00:20:51 XQueryPointer:     x: 272, y:  25)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 232, y:  20) dx: -13 dy:  -3 dt: 0.0091 t: 40.4345
11/02/2011 00:20:51 calling XTestFakeMotionEvent(257, 22)  40.4346
11/02/2011 00:20:51 XQueryPointer:     x: 257, y:  22)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 220, y:  18) dx: -12 dy:  -2 dt: 0.0146 t: 40.4491
11/02/2011 00:20:51 calling XTestFakeMotionEvent(244, 20)  40.4492
11/02/2011 00:20:51 XQueryPointer:     x: 244, y:  20)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 209, y:  15) dx: -11 dy:  -3 dt: 0.0185 t: 40.4676
11/02/2011 00:20:51 calling XTestFakeMotionEvent(232, 16)  40.4677
11/02/2011 00:20:51 XQueryPointer:     x: 232, y:  16)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 199, y:  13) dx: -10 dy:  -2 dt: 0.0388 t: 40.5065
11/02/2011 00:20:51 calling XTestFakeMotionEvent(221, 14)  40.5065
11/02/2011 00:20:51 XQueryPointer:     x: 221, y:  14)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 192, y:  10) dx:  -7 dy:  -3 dt: 0.0113 t: 40.5177
11/02/2011 00:20:51 calling XTestFakeMotionEvent(213, 11)  40.5178
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 189, y:   7) dx:  -3 dy:  -3 dt: 0.0004 t: 40.5182
11/02/2011 00:20:51 calling XTestFakeMotionEvent(210, 7)  40.5182
11/02/2011 00:20:51 XQueryPointer:     x: 210, y:   7)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 184, y:   2) dx:  -5 dy:  -5 dt: 0.0181 t: 40.5363
11/02/2011 00:20:51 calling XTestFakeMotionEvent(204, 2)  40.5364
11/02/2011 00:20:51 XQueryPointer:     x: 204, y:   2)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 182, y:   1) dx:  -2 dy:  -1 dt: 0.0388 t: 40.5751
11/02/2011 00:20:51 calling XTestFakeMotionEvent(202, 1)  40.5752
11/02/2011 00:20:51 XQueryPointer:     x: 202, y:   1)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:   7) dx: -11 dy:   6 dt: 0.3022 t: 40.8772
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 7)  40.8773
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:   7)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  10) dx:   0 dy:   3 dt: 0.0203 t: 40.8975
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 11)  40.8976
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  11)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  11) dx:   0 dy:   1 dt: 0.0483 t: 40.9458
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 12)  40.9459
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  12) dx:   0 dy:   1 dt: 0.0107 t: 40.9565
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 13)  40.9566
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  13)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  13) dx:   0 dy:   1 dt: 0.1194 t: 41.0759
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 14)  41.0760
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  14)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  14) dx:   0 dy:   1 dt: 0.0660 t: 41.1419
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 15)  41.1420
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  15)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  15) dx:   0 dy:   1 dt: 0.0191 t: 41.1611
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 16)  41.1612
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  16)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 171, y:  16) dx:   0 dy:   1 dt: 0.0549 t: 41.2160
11/02/2011 00:20:51 calling XTestFakeMotionEvent(190, 17)  41.2160
11/02/2011 00:20:51 XQueryPointer:     x: 190, y:  17)
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 173, y:  16) dx:   2 dy:   0 dt: 0.0673 t: 41.2832
11/02/2011 00:20:51 calling XTestFakeMotionEvent(192, 17)  41.2833
11/02/2011 00:20:51 # pointer(mask: 0x0, x: 174, y:  16) dx:   1 dy:   0 dt: 0.0003 t: 41.2835
11/02/2011 00:20:51 calling XTestFakeMotionEvent(193, 17)  41.2836
11/02/2011 00:20:51 # pointer(mask: 0x1, x: 174, y:  16) dx:   0 dy:   0 dt: 0.0002 t: 41.2837
11/02/2011 00:20:51 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:51 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:51 calling XTestFakeButtonEvent(1, 1)  41.2842
11/02/2011 00:20:51 XQueryPointer:     x: 193, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 174, y:  16) dx:   0 dy:   0 dt: 0.1454 t: 41.4291
11/02/2011 00:20:52 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:52 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:52 calling XTestFakeButtonEvent(1, 0)  41.4292
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 173, y:  16) dx:  -1 dy:   0 dt: 0.5227 t: 41.9518
11/02/2011 00:20:52 calling XTestFakeMotionEvent(192, 17)  41.9519
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 171, y:  16) dx:  -2 dy:   0 dt: 0.0106 t: 41.9624
11/02/2011 00:20:52 calling XTestFakeMotionEvent(190, 17)  41.9625
11/02/2011 00:20:52 XQueryPointer:     x: 190, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 167, y:  16) dx:  -4 dy:   0 dt: 0.0479 t: 42.0103
11/02/2011 00:20:52 calling XTestFakeMotionEvent(185, 17)  42.0104
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 163, y:  16) dx:  -4 dy:   0 dt: 0.0004 t: 42.0106
11/02/2011 00:20:52 calling XTestFakeMotionEvent(181, 17)  42.0107
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 159, y:  16) dx:  -4 dy:   0 dt: 0.0015 t: 42.0122
11/02/2011 00:20:52 calling XTestFakeMotionEvent(176, 17)  42.0122
11/02/2011 00:20:52 XQueryPointer:     x: 176, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 157, y:  16) dx:  -2 dy:   0 dt: 0.0186 t: 42.0308
11/02/2011 00:20:52 calling XTestFakeMotionEvent(174, 17)  42.0309
11/02/2011 00:20:52 XQueryPointer:     x: 174, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 156, y:  16) dx:  -1 dy:   0 dt: 0.0536 t: 42.0844
11/02/2011 00:20:52 calling XTestFakeMotionEvent(173, 17)  42.0845
11/02/2011 00:20:52 XQueryPointer:     x: 173, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 154, y:  16) dx:  -2 dy:   0 dt: 0.0331 t: 42.1175
11/02/2011 00:20:52 calling XTestFakeMotionEvent(171, 17)  42.1176
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 153, y:  16) dx:  -1 dy:   0 dt: 0.0113 t: 42.1288
11/02/2011 00:20:52 calling XTestFakeMotionEvent(170, 17)  42.1289
11/02/2011 00:20:52 XQueryPointer:     x: 170, y:  17)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 152, y:  15) dx:  -1 dy:  -1 dt: 0.0557 t: 42.1845
11/02/2011 00:20:52 calling XTestFakeMotionEvent(168, 16)  42.1846
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 150, y:  15) dx:  -2 dy:   0 dt: 0.0003 t: 42.1848
11/02/2011 00:20:52 calling XTestFakeMotionEvent(166, 16)  42.1848
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 149, y:  14) dx:  -1 dy:  -1 dt: 0.0002 t: 42.1850
11/02/2011 00:20:52 calling XTestFakeMotionEvent(165, 15)  42.1850
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 148, y:  14) dx:  -1 dy:   0 dt: 0.0015 t: 42.1864
11/02/2011 00:20:52 calling XTestFakeMotionEvent(164, 15)  42.1865
11/02/2011 00:20:52 XQueryPointer:     x: 164, y:  15)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 147, y:  14) dx:  -1 dy:   0 dt: 0.0664 t: 42.2528
11/02/2011 00:20:52 calling XTestFakeMotionEvent(163, 15)  42.2529
11/02/2011 00:20:52 XQueryPointer:     x: 163, y:  15)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 146, y:  14) dx:  -1 dy:   0 dt: 0.0660 t: 42.3189
11/02/2011 00:20:52 calling XTestFakeMotionEvent(162, 15)  42.3190
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 145, y:  14) dx:  -1 dy:   0 dt: 0.0015 t: 42.3203
11/02/2011 00:20:52 calling XTestFakeMotionEvent(161, 15)  42.3204
11/02/2011 00:20:52 XQueryPointer:     x: 161, y:  15)
11/02/2011 00:20:52 # pointer(mask: 0x0, x: 143, y:  14) dx:  -2 dy:   0 dt: 0.0190 t: 42.3393
11/02/2011 00:20:52 calling XTestFakeMotionEvent(158, 15)  42.3394
11/02/2011 00:20:52 XQueryPointer:     x: 158, y:  15)
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 143, y:  13) dx:   0 dy:  -1 dt: 0.1653 t: 42.5046
11/02/2011 00:20:53 calling XTestFakeMotionEvent(158, 14)  42.5046
11/02/2011 00:20:53 XQueryPointer:     x: 158, y:  14)
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 143, y:  12) dx:   0 dy:  -1 dt: 0.0954 t: 42.5999
11/02/2011 00:20:53 calling XTestFakeMotionEvent(158, 13)  42.6000
11/02/2011 00:20:53 XQueryPointer:     x: 158, y:  13)
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 142, y:  12) dx:  -1 dy:   0 dt: 0.0211 t: 42.6211
11/02/2011 00:20:53 calling XTestFakeMotionEvent(157, 13)  42.6212
11/02/2011 00:20:53 # pointer(mask: 0x1, x: 142, y:  12) dx:   0 dy:   0 dt: 0.0013 t: 42.6224
11/02/2011 00:20:53 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:53 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:53 calling XTestFakeButtonEvent(1, 1)  42.6231
11/02/2011 00:20:53 XQueryPointer:     x: 157, y:  13)
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 142, y:  12) dx:   0 dy:   0 dt: 0.1845 t: 42.8069
11/02/2011 00:20:53 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:53 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:53 calling XTestFakeButtonEvent(1, 0)  42.8070
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 141, y:  11) dx:  -1 dy:  -1 dt: 0.4929 t: 43.2998
11/02/2011 00:20:53 calling XTestFakeMotionEvent(156, 12)  43.2999
11/02/2011 00:20:53 XQueryPointer:     x: 156, y:  12)
11/02/2011 00:20:53 # pointer(mask: 0x0, x: 136, y:  11) dx:  -5 dy:   0 dt: 0.0203 t: 43.3201
11/02/2011 00:20:53 calling XTestFakeMotionEvent(151, 12)  43.3202
11/02/2011 00:20:53 XQueryPointer:     x: 151, y:  12)
11/02/2011 00:20:54 # pointer(mask: 0x0, x: 128, y:  11) dx:  -8 dy:   0 dt: 0.0444 t: 43.3645
11/02/2011 00:20:54 calling XTestFakeMotionEvent(142, 12)  43.3646
11/02/2011 00:20:54 # pointer(mask: 0x0, x: 119, y:  11) dx:  -9 dy:   0 dt: 0.0106 t: 43.3751
11/02/2011 00:20:54 calling XTestFakeMotionEvent(132, 12)  43.3752
11/02/2011 00:20:54 # pointer(mask: 0x0, x: 112, y:  13) dx:  -7 dy:   2 dt: 0.0014 t: 43.3765
11/02/2011 00:20:54 calling XTestFakeMotionEvent(124, 14)  43.3766
11/02/2011 00:20:54 XQueryPointer:     x: 124, y:  14)
11/02/2011 00:20:54 # pointer(mask: 0x0, x: 103, y:  14) dx:  -9 dy:   1 dt: 0.0471 t: 43.4236
11/02/2011 00:20:54 calling XTestFakeMotionEvent(114, 15)  43.4237
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  94, y:  16) dx:  -9 dy:   2 dt: 0.0003 t: 43.4239
11/02/2011 00:20:54 calling XTestFakeMotionEvent(104, 17)  43.4240
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  88, y:  16) dx:  -6 dy:   0 dt: 0.0002 t: 43.4241
11/02/2011 00:20:54 calling XTestFakeMotionEvent(97, 17)  43.4241
11/02/2011 00:20:54 XQueryPointer:     x:  97, y:  17)
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  82, y:  16) dx:  -6 dy:   0 dt: 0.0095 t: 43.4337
11/02/2011 00:20:54 calling XTestFakeMotionEvent(91, 17)  43.4337
11/02/2011 00:20:54 XQueryPointer:     x:  91, y:  17)
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  76, y:  16) dx:  -6 dy:   0 dt: 0.0693 t: 43.5029
11/02/2011 00:20:54 calling XTestFakeMotionEvent(84, 17)  43.5030
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  71, y:  16) dx:  -5 dy:   0 dt: 0.0003 t: 43.5032
11/02/2011 00:20:54 calling XTestFakeMotionEvent(78, 17)  43.5033
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  68, y:  16) dx:  -3 dy:   0 dt: 0.0002 t: 43.5034
11/02/2011 00:20:54 calling XTestFakeMotionEvent(75, 17)  43.5034
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  66, y:  16) dx:  -2 dy:   0 dt: 0.0014 t: 43.5049
11/02/2011 00:20:54 calling XTestFakeMotionEvent(73, 17)  43.5049
11/02/2011 00:20:54 XQueryPointer:     x:  73, y:  17)
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  65, y:  16) dx:  -1 dy:   0 dt: 0.0190 t: 43.5238
11/02/2011 00:20:54 calling XTestFakeMotionEvent(72, 17)  43.5239
11/02/2011 00:20:54 XQueryPointer:     x:  72, y:  17)
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  64, y:  16) dx:  -1 dy:   0 dt: 0.0520 t: 43.5758
11/02/2011 00:20:54 calling XTestFakeMotionEvent(71, 17)  43.5759
11/02/2011 00:20:54 XQueryPointer:     x:  71, y:  17)
11/02/2011 00:20:54 # pointer(mask: 0x1, x:  64, y:  16) dx:   0 dy:   0 dt: 0.4492 t: 44.0250
11/02/2011 00:20:54 pointer(): mask change: mask: 0x0 -> 0x1 button: 1
11/02/2011 00:20:54 pointer(): sending button 1 down (event 1)
11/02/2011 00:20:54 calling XTestFakeButtonEvent(1, 1)  44.0256
11/02/2011 00:20:54 # pointer(mask: 0x0, x:  64, y:  16) dx:   0 dy:   0 dt: 0.2085 t: 44.2335
11/02/2011 00:20:54 pointer(): mask change: mask: 0x1 -> 0x0 button: 1
11/02/2011 00:20:54 pointer(): sending button 1 up (event 1)
11/02/2011 00:20:54 calling XTestFakeButtonEvent(1, 0)  44.2336
11/02/2011 00:20:55 # pointer(mask: 0x0, x:  63, y:  16) dx:  -1 dy:   0 dt: 0.5869 t: 44.8204
11/02/2011 00:20:55 calling XTestFakeMotionEvent(70, 17)  44.8204
11/02/2011 00:20:55 XQueryPointer:     x:  70, y:  17)
11/02/2011 00:20:55 # pointer(mask: 0x0, x:  51, y:  19) dx: -12 dy:   3 dt: 0.0197 t: 44.8401
11/02/2011 00:20:55 calling XTestFakeMotionEvent(56, 21)  44.8401
11/02/2011 00:20:55 XQueryPointer:     x:  56, y:  21)
11/02/2011 00:20:55 # pointer(mask: 0x0, x:  33, y:  24) dx: -18 dy:   5 dt: 0.0130 t: 44.8531
11/02/2011 00:20:55 calling XTestFakeMotionEvent(36, 26)  44.8532
11/02/2011 00:20:55 XQueryPointer:     x:  36, y:  26)
11/02/2011 00:20:58 client_count: 0
11/02/2011 00:20:58 Restored X server key autorepeat to: 1
11/02/2011 00:20:58 viewer exited.
11/02/2011 00:20:58 deleted 40 tile_row polling images.
professor@Professor:~$ 

```

---

### Post by krunge on 2011-02-11
> **s73v3r said:**
> Here you go. It looks like it is getting events. 

Thanks.  Yes it is getting the events and using XTestFakeMotionEvent, XTestFakeButtonEvent, and XTestFakeKeyEvent to try to synthetically inject them into the X server.  I wonder if XTEST is broken on your system somehow?

Did you say the mouse motion works?  

Does this happen if you use a 'failsafe' desktop login?  (i.e. no gnome, kde, etc.)  Try it and see if you can inject button clicks and keystrokes.

Also start up the 'xev' program from the failsafe terminal. Then move the mouse into the little xev square window and see if it is getting the button clicks and keystrokes (it prints the events to stdout.)

---

### Post by s73v3r on 2011-02-12
Do you want me to log in through the VNC session? Or should I go over to the machine and do the log in there? Normally when I VNC, the desktop session is already logged in.

Mouse motion does work, by the way.

---

### Post by krunge on 2011-02-12
> **s73v3r said:**
> Do you want me to log in through the VNC session? Or should I go over to the machine and do the log in there? Normally when I VNC, the desktop session is already logged in.
Oh, get the log file any way you like.  I find '-o log.txt' handy but do whatever works well for you.

Remember to do failsafe with no desktop.  Don't just do a simpler desktop than kde or gnome, might as well go straight to a naked X server via failsafe.
> 
Mouse motion does work, by the way.
That is a very useful piece of info. Not sure yet how to interpret it.

---

### Post by asmoore82 on 2011-02-12
> **s73v3r said:**
> I can log in using my Windows box and UltraVNC and use input with no problem.
:-k UltraVNC works fine, Chicken of the VNC doesn't and
you all are looking for a problem with x11vnc? :shock:

Chicken of the VNC looks abandoned: [http://sourceforge.net/projects/cotvnc/files/cotvnc/](http://sourceforge.net/projects/cotvnc/files/cotvnc/)

I knew a Mac server admin who once tried Chicken of the VNC as a
supplement to Apple Remote Desktop. He never got it to work.
That's Jobs' Garden: pay to play, pay to stay, pay up or go away.

P.S. Googling "vnc mac" turns up a lot of junk, but this gem
(if it's true): [http://www.ihackintosh.com/2009/04/how-to-connect-vnc-server-in-mac-osx-leopard/](http://www.ihackintosh.com/2009/04/how-to-connect-vnc-server-in-mac-osx-leopard/)

---

