---
title: "Upgrading to 11.10 breaks VNC (vino)"
date: 2011-10-15
forum: General Help
---

### Post by bigclaw on 2011-10-15
Hello,

I just upgraded my 11.04 32-bit system to 11.10, and my VNC server (vino) is not auto-starting anymore. In my Desktop Sharing panel, I have it as anybody can view and control my desktop and there is no need to enter a password.

If I try to manually execute vino-server on the command line, I get a vino-server 2464 WARNING: The desktop sharing service is not enabled, so it should not be run.

I am at a loss. Everything worked perfectly with 11.04. Is there a separate step to enable this "desktop sharing service" maybe? Where can I find it in the UI?

Thanks!

---

### Post by gabhroo on 2011-10-15
I am having the exact same issue.

---

### Post by jecos on 2011-10-16
This is a pretty damn HUGE BUG!   

and..
Not only is Unity the biggest piece of garbage ubuntu developers have ever pushed out. How the hell is Unity different or better than Gnome 3?  it's pretty much the same thing. Duplicating efforts and making linux more and more unstable on the Desktop is not the way to go.

---

### Post by bigclaw on 2011-10-16
Hi, I figured it out somewhat, I think. The VNC (vino-server) daemon is only started if you use gnome, it seems. I used gnome in 11.04 and switched to Unity in 11.10. 

I followed the instructions to have a gnome-fallback package installed and logged in using that. Now VNC works again.

Now I just have to figure out how to automatically log into gnome, not Unity.

In my opinion, this continues to be one of the reasons Linux/Ubuntu is still not ready for prime time. It's 95% there, but stuff like this just doesn't make a whole lot of sense to an average user. The Desktop Sharing control panel mentions nothing about gnome or Unity. How do you expect the user to realize the difference? If Unity is the default way to work with Ubuntu, how come VNC is not fixed to the extent it's workable with Unity?

---

### Post by conualfy on 2011-10-16
Bigclaw is right. I also came from Windows and there are lots of small issues that little by little take away the pleasure and fun of working with a computer. I think Unity is a major breakthrough as Gnome desktop was very space inefficient on our modern wide screens.

But these issues should have priority instead of any other upcoming revolution. Fix everything that is not working right, make the user want to chose Ubuntu for it's simple and elegant way of working, clean and not with overlapping icons on desktop, clean and simple way of installing-uninstalling programs (it's not working very well in Oneiric), allow the user to minimize window(s) from taskbar, allow user to easily restore minimized window from taskbar (no extra click) etc.

---

### Post by bigclaw on 2011-10-16
OMG. Finally found a way to get some sane VNC sessions back!

1. Install gnome classic: sudo apt-get install gnome-session-fallback

2. Change the default session to gnome classic: sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic

Restart and rejoice.

FWIW, I also tried the new gnome 3 by installing gnome-shell. It gets my VNC daemon (vino-server) back, but my clients all have problems with its Activities menu (clicking on the UI don't do anything most of the time). Probably some 3D trick that my VNC clients aren't able to handle yet.

Gnome-classic will do for me for now.

Almost, almost went back to Windows 7. Ubuntu, consider this your fair warning. :)

---

### Post by crjackson on 2011-10-16
> **bigclaw said:**
> OMG. Finally found a way to get some sane VNC sessions back!

1. Install gnome classic: sudo apt-get install gnome-session-fallback

2. Change the default session to gnome classic: sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic

Restart and rejoice.

FWIW, I also tried the new gnome 3 by installing gnome-shell. It gets my VNC daemon (vino-server) back, but my clients all have problems with its Activities menu (clicking on the UI don't do anything most of the time). Probably some 3D trick that my VNC clients aren't able to handle yet.

Gnome-classic will do for me for now.

Almost, almost went back to Windows 7. Ubuntu, consider this your fair warning. :)

I'm not happy with Unity in it's current state either, and it broke both VNC and Network shares for me. I'm expecting this to be worked out over the next 30-60 days but if not, I too will make the fallback session my default on all systems.

Maybe a fix will be out soon...  I didn't have this trouble with the beta versions.

---

### Post by antgod on 2011-10-18
I've having a diferent issue about the same thing...
vino just breaks...

```

to@gandalf:~$ vncserver

New 'X' desktop is gandalf:1

Starting applications specified in /home/to/.vnc/xstartup
Log file is /home/to/.vnc/gandalf:1.log

to@gandalf:~$ *** glibc detected *** /usr/lib/vino/vino-server: malloc(): memory corruption: 0x0948e708 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ebc2)[0x3b30bc2]
/lib/i386-linux-gnu/libc.so.6(+0x7055e)[0x3b3255e]
/lib/i386-linux-gnu/libc.so.6(__libc_malloc+0x68)[0x3b34498]
/usr/lib/libminiupnpc.so.5(GetUPNPUrls+0x9b)[0x2c821b]
/usr/lib/libminiupnpc.so.5(UPNP_GetValidIGD+0x153)[0x2c8cb3]
/usr/lib/vino/vino-server[0x805baec]
/usr/lib/vino/vino-server[0x805c037]
/usr/lib/vino/vino-server[0x80564f3]
/usr/lib/vino/vino-server[0x80543aa]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9988)[0x673988]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9aad)[0x673aad]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9d89)[0x673d89]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_simple_async_result_complete+0xbf)[0x61aaef]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb0ea8)[0x66aea8]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_simple_async_result_complete+0xbf)[0x61aaef]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x60c1b)[0x61ac1b]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x3f110)[0x95c110]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x1df)[0x96025f]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x43990)[0x960990]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x14b)[0x960f9b]
/usr/lib/vino/vino-server[0x805087e]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x3adb113]
/usr/lib/vino/vino-server[0x8050975]
======= Memory map: ========
00110000-0011c000 r-xp 00000000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011c000-0011d000 r--p 0000b000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011d000-0011e000 rw-p 0000c000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011e000-00125000 r-xp 00000000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00125000-00126000 r--p 00006000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00126000-00127000 rw-p 00007000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00127000-0012c000 r-xp 00000000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
0012c000-0012d000 r--p 00004000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
0012d000-0012e000 rw-p 00005000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
00130000-00131000 r-xp 00000000 00:00 0          [vdso]
00131000-001f8000 r-xp 00000000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001f8000-001f9000 r--p 000c7000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001f9000-001fa000 rw-p 000c8000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001fa000-001fc000 rw-p 00000000 00:00 0
001fc000-0021f000 r-xp 00000000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
0021f000-00220000 r--p 00022000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00220000-00221000 rw-p 00023000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00221000-0026e000 r-xp 00000000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
0026e000-0026f000 r--p 0004d000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
0026f000-00270000 rw-p 0004e000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00270000-00281000 r-xp 00000000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00281000-00282000 r--p 00010000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00282000-00283000 rw-p 00011000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00283000-002a5000 r-xp 00000000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a5000-002a6000 r--p 00022000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a6000-002a7000 rw-p 00023000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a7000-002bd000 r-xp 00000000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002bd000-002be000 r--p 00015000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002be000-002bf000 rw-p 00016000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002bf000-002c1000 rw-p 00000000 00:00 0
002c1000-002c3000 r-xp 00000000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c3000-002c4000 r--p 00001000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c4000-002c5000 rw-p 00002000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c5000-002cd000 r-xp 00000000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002cd000-002ce000 r--p 00007000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002ce000-002cf000 rw-p 00008000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002cf000-002d3000 r-xp 00000000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d3000-002d4000 r--p 00003000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d4000-002d5000 rw-p 00004000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d5000-002da000 r-xp 00000000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002da000-002db000 r--p 00005000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002db000-002dc000 rw-p 00006000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002dc000-002de000 r-xp 00000000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002de000-002df000 r--p 00001000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002df000-002e0000 rw-p 00002000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002e0000-002f7000 r-xp 00000000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f7000-002f8000 r--p 00016000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f8000-002f9000 rw-p 00017000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f9000-002fb000 rw-p 00000000 00:00 0
002fb000-0030c000 r-xp 00000000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030c000-0030d000 r--p 00010000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030d000-0030e000 rw-p 00011000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030e000-00321000 r-xp 00000000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00321000-00322000 r--p 00012000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00322000-00323000 rw-p 00013000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00323000-0032e000 r-xp 00000000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
0032e000-0032f000 r--p 0000a000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
0032f000-00330000 rw-p 0000b000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00330000-00333000 r-xp 00000000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00333000-00334000 r--p 00002000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00334000-00335000 rw-p 00003000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00335000-00337000 r-xp 00000000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00337000-00338000 r--p 00001000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00338000-00339000 rw-p 00002000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
0033b000-003b1000 r-xp 00000000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b1000-003b3000 r--p 00075000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b3000-003b4000 rw-p 00077000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b4000-003d1000 r-xp 00000000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d1000-003d3000 r--p 0001c000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d3000-003d4000 rw-p 0001e000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d4000-003f2000 r-xp 00000000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f2000-003f3000 r--p 0001d000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f3000-003f4000 rw-p 0001e000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f4000-003fb000 r-xp 00000000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fb000-003fc000 r--p 00006000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fc000-003fd000 rw-p 00007000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fd000-003ff000 r-xp 00000000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
003ff000-00400000 r--p 00001000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00400000-00401000 rw-p 00002000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00403000-005b1000 r-xp 00000000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b1000-005b2000 ---p 001ae000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b2000-005b5000 r--p 001ae000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b5000-005b9000 rw-p 001b1000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b9000-005ba000 rw-p 00000000 00:00 0
005ba000-006fc000 r-xp 00000000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006fc000-006fe000 r--p 00142000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006fe000-006ff000 rw-p 00144000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006ff000-00700000 rw-p 00000000 00:00 0
00700000-00782000 r-xp 00000000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00782000-00783000 r--p 00081000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00783000-00785000 rw-p 00082000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00785000-00793000 r-xp 00000000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00793000-00794000 r--p 0000d000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00794000-00795000 rw-p 0000e000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00798000-0079e000 r-xp 00000000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
0079e000-0079f000 r--p 00005000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
0079f000-007a0000 rw-p 00006000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
007a0000-0084a000 r-xp 00000000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084a000-0084b000 ---p 000aa000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084b000-0084f000 r--p 000aa000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084f000-00850000 rw-p 000ae000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
00850000-00859000 r-xp 00000000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00859000-0085a000 r--p 00008000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0085a000-0085b000 rw-p 00009000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0085b000-00863000 r-xp 00000000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00863000-00864000 r--p 00007000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00864000-00865000 rw-p 00008000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0

```

---

### Post by mathuin on 2011-10-18
> **antgod said:**
> I've having a diferent issue about the same thing...
vino just breaks...

```

to@gandalf:~$ vncserver

New 'X' desktop is gandalf:1

Starting applications specified in /home/to/.vnc/xstartup
Log file is /home/to/.vnc/gandalf:1.log

to@gandalf:~$ *** glibc detected *** /usr/lib/vino/vino-server: malloc(): memory corruption: 0x0948e708 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ebc2)[0x3b30bc2]
/lib/i386-linux-gnu/libc.so.6(+0x7055e)[0x3b3255e]
/lib/i386-linux-gnu/libc.so.6(__libc_malloc+0x68)[0x3b34498]
/usr/lib/libminiupnpc.so.5(GetUPNPUrls+0x9b)[0x2c821b]
/usr/lib/libminiupnpc.so.5(UPNP_GetValidIGD+0x153)[0x2c8cb3]
/usr/lib/vino/vino-server[0x805baec]
/usr/lib/vino/vino-server[0x805c037]
/usr/lib/vino/vino-server[0x80564f3]
/usr/lib/vino/vino-server[0x80543aa]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9988)[0x673988]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9aad)[0x673aad]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb9d89)[0x673d89]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_simple_async_result_complete+0xbf)[0x61aaef]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0xb0ea8)[0x66aea8]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_simple_async_result_complete+0xbf)[0x61aaef]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x60c1b)[0x61ac1b]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x3f110)[0x95c110]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x1df)[0x96025f]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x43990)[0x960990]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x14b)[0x960f9b]
/usr/lib/vino/vino-server[0x805087e]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x3adb113]
/usr/lib/vino/vino-server[0x8050975]
======= Memory map: ========
00110000-0011c000 r-xp 00000000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011c000-0011d000 r--p 0000b000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011d000-0011e000 rw-p 0000c000 08:02 1709214    /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
0011e000-00125000 r-xp 00000000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00125000-00126000 r--p 00006000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00126000-00127000 rw-p 00007000 08:02 1709166    /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00127000-0012c000 r-xp 00000000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
0012c000-0012d000 r--p 00004000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
0012d000-0012e000 rw-p 00005000 08:02 1706732    /usr/lib/libXtst.so.6.1.0
00130000-00131000 r-xp 00000000 00:00 0          [vdso]
00131000-001f8000 r-xp 00000000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001f8000-001f9000 r--p 000c7000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001f9000-001fa000 rw-p 000c8000 08:02 1709234    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
001fa000-001fc000 rw-p 00000000 00:00 0
001fc000-0021f000 r-xp 00000000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
0021f000-00220000 r--p 00022000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00220000-00221000 rw-p 00023000 08:02 1709255    /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00221000-0026e000 r-xp 00000000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
0026e000-0026f000 r--p 0004d000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
0026f000-00270000 rw-p 0004e000 08:02 1709302    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00270000-00281000 r-xp 00000000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00281000-00282000 r--p 00010000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00282000-00283000 rw-p 00011000 08:02 1709212    /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00283000-002a5000 r-xp 00000000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a5000-002a6000 r--p 00022000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a6000-002a7000 rw-p 00023000 08:02 1709325    /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0
002a7000-002bd000 r-xp 00000000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002bd000-002be000 r--p 00015000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002be000-002bf000 rw-p 00016000 08:02 1709127    /usr/lib/i386-linux-gnu/libICE.so.6.3.0
002bf000-002c1000 rw-p 00000000 00:00 0
002c1000-002c3000 r-xp 00000000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c3000-002c4000 r--p 00001000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c4000-002c5000 rw-p 00002000 08:02 1709178    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
002c5000-002cd000 r-xp 00000000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002cd000-002ce000 r--p 00007000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002ce000-002cf000 rw-p 00008000 08:02 1707185    /usr/lib/libminiupnpc.so.5
002cf000-002d3000 r-xp 00000000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d3000-002d4000 r--p 00003000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d4000-002d5000 rw-p 00004000 08:02 1709184    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
002d5000-002da000 r-xp 00000000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002da000-002db000 r--p 00005000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002db000-002dc000 rw-p 00006000 08:02 1709232    /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11000.2
002dc000-002de000 r-xp 00000000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002de000-002df000 r--p 00001000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002df000-002e0000 rw-p 00002000 08:02 1709190    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
002e0000-002f7000 r-xp 00000000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f7000-002f8000 r--p 00016000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f8000-002f9000 rw-p 00017000 08:02 3408865    /lib/i386-linux-gnu/libpthread-2.13.so
002f9000-002fb000 rw-p 00000000 00:00 0
002fb000-0030c000 r-xp 00000000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030c000-0030d000 r--p 00010000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030d000-0030e000 rw-p 00011000 08:02 1709182    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0030e000-00321000 r-xp 00000000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00321000-00322000 r--p 00012000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00322000-00323000 rw-p 00013000 08:02 3408888    /lib/i386-linux-gnu/libz.so.1.2.3.4
00323000-0032e000 r-xp 00000000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
0032e000-0032f000 r--p 0000a000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
0032f000-00330000 rw-p 0000b000 08:02 1709376    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00330000-00333000 r-xp 00000000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00333000-00334000 r--p 00002000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00334000-00335000 rw-p 00003000 08:02 1709294    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00335000-00337000 r-xp 00000000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00337000-00338000 r--p 00001000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00338000-00339000 rw-p 00002000 08:02 1709174    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
0033b000-003b1000 r-xp 00000000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b1000-003b3000 r--p 00075000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b3000-003b4000 rw-p 00077000 08:02 1706923    /usr/lib/libgdk-3.so.0.200.0
003b4000-003d1000 r-xp 00000000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d1000-003d3000 r--p 0001c000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d3000-003d4000 rw-p 0001e000 08:02 1709208    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
003d4000-003f2000 r-xp 00000000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f2000-003f3000 r--p 0001d000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f3000-003f4000 rw-p 0001e000 08:02 1709286    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
003f4000-003fb000 r-xp 00000000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fb000-003fc000 r--p 00006000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fc000-003fd000 rw-p 00007000 08:02 1709192    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
003fd000-003ff000 r-xp 00000000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
003ff000-00400000 r--p 00001000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00400000-00401000 rw-p 00002000 08:02 1709466    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00403000-005b1000 r-xp 00000000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b1000-005b2000 ---p 001ae000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b2000-005b5000 r--p 001ae000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b5000-005b9000 rw-p 001b1000 08:02 1707374    /usr/lib/libtelepathy-glib.so.0.61.0
005b9000-005ba000 rw-p 00000000 00:00 0
005ba000-006fc000 r-xp 00000000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006fc000-006fe000 r--p 00142000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006fe000-006ff000 rw-p 00144000 08:02 1709290    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
006ff000-00700000 rw-p 00000000 00:00 0
00700000-00782000 r-xp 00000000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00782000-00783000 r--p 00081000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00783000-00785000 rw-p 00082000 08:02 3408828    /lib/i386-linux-gnu/libgcrypt.so.11.7.0
00785000-00793000 r-xp 00000000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00793000-00794000 r--p 0000d000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00794000-00795000 rw-p 0000e000 08:02 1709188    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00798000-0079e000 r-xp 00000000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
0079e000-0079f000 r--p 00005000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
0079f000-007a0000 rw-p 00006000 08:02 1709355    /usr/lib/i386-linux-gnu/libnotify.so.4.0.0
007a0000-0084a000 r-xp 00000000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084a000-0084b000 ---p 000aa000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084b000-0084f000 r--p 000aa000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
0084f000-00850000 rw-p 000ae000 08:02 1709300    /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
00850000-00859000 r-xp 00000000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00859000-0085a000 r--p 00008000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0085a000-0085b000 rw-p 00009000 08:02 1709176    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
0085b000-00863000 r-xp 00000000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00863000-00864000 r--p 00007000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00864000-00865000 rw-p 00008000 08:02 1709462    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0

```

I get the same thing as antgod when I try to use vino.

Jack.

---

### Post by rarmstr on 2011-10-19
I have the same issue.

---

### Post by Perryg on 2011-10-19
Actually I solved this issue by installing x11vnc instead. Since Unity and Gnome3 use accelerated and or compositing the client would not be able to use or even see most of the remote desktop with vino. Since x11vnc supports framebuffers and transmits the actual video that x is showing on the remote screen it works well.  To simplify matters of startup I created a small script and put it in the startup folder.  Not as easy to setup as vino but it is going to be the way to go in the near future.

---

### Post by andost on 2011-10-20
Hi

I have a headless server (Acer H340 upgraded from Windows Home Server to Ubuntu 11.10) so i needed to get this working.

Did a little digging...

1. apt-get install tightvncserver

2. add the following to /etc/lightdm/lightdm.conf
```
[VNCServer]
enabled=true

```

3. restart lightdm 

then you can log in with VNC right away. Hope this helps :)

---

### Post by sirhalos on 2011-10-20
This worked for me but how do you change the default settings for the VNC Server (geometry and color) doing it this way? I know how to do it from command line but where are the defaults stored?


> **andost said:**
> Hi

2. add the following to /etc/lightdm/lightdm.conf
```
[VNCServer]
enabled=true

```

3. restart lightdm 

then you can log in with VNC right away. Hope this helps :)

---

### Post by Audiosears on 2011-10-26
This is driving me clean off the deep end, so I'll do my best to present info clearly here:

I've tried things earlier in this thread without any success yet.  I just upgraded from 11.04 to 11.10 (surprisingly w/o grub, samba, apache or networking breaking at all - that's a first), and so help me God I can't get any manner of VNC to resume working.

I used to use RealVNC's viewer from Windows to remote into 11.04 w/o issue, and after the upgrade this is no longer working.  Initially a 'netstat -ln -A inet' revealed that there was nothing listening on port 5900, and running 'vino-server' from the command line throws back 'Command not found'.  Vino is installed, and I performed an 'apt-get remove vino' and 'apt-get install vino' without any change.

I also tried adding [VNCServer] enabled=true to lightdm.conf, no change.  Tried having the server boot into an account with gnome rather than unity, no change.

I also installed vnc4server and x11vnc and cannot get either of them to accept an initial password.  After installing either of them and running 'vnc4server' or 'vncserver' from command line, they ask for a password.  No matter what I give them, they report 'inappropriate ioctrl for device' or 'password too short' respectively.  I don't know if this a syntax problem on my part, but no information anywhere seems to specify this.  In various instructions they all say something like '...apt-get install <whatever> and you will be prompted for an initial password.  Put it in.  Then <blah blah>...'.

I need to be able to remote in to fix a couple other things and I'm getting absolutely nowhere.  I'm willing to use whatever someone recommends, preferably something that worked as simply as before.

My preferred setup is to either have the server auto-login to an account on startup (which can then be remoted into), or just start the server w/o needing an auto-login, provided your average vnc client can login and start a session w/o user intervention on the server side.

---

### Post by Audiosears on 2011-10-26
OK, I got it.  AFAIK, Vino is still broken as of the 11.10 upgrade, but I was able to get x11vnc working after finding this ([source]("http://mlepicki.com/?p=10")):

**********************************
First of all, I&#8217;ve installed x11vnc:
apt-get install x11vnc

Then, I&#8217;ve created /etc/init/x11vnc.conf file:
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

After restart, x11vnc shoud listen on vnc startard port &#8211; 5900.

This script is of course based on upstart event mechanism. Lightdm emits login-session-start event (you can find it in lightdm.conf), and we start x11vnc when this event is emited &#8211; that&#8217;s first line of x11vnc.conf file.
*****************************

I created the upstart config file, rebooted (still having my server auto-login) and I was then able to vnc back in

---

### Post by Perryg on 2011-10-26
My experience with upgrades are not good at all.  I did upgrade from 11.04 to 11.10 and started having all kinds of issues.  I finally just installed new and 99% of my issues went away.  

Now back to your issue.  If you have installed x11vnc, you can test that it works or not by starting it in a terminal. This will bypass any configuration issues or passwords.  Just type x11vnc and see if you can then access it via a VNC client.  If it works then you are going to need to configure a startup script and put it in the startup folder.

Don't leave it like that though as it is not secure at all and anyone could actually access your unit.

---

### Post by pmamatsis on 2011-10-26
Hi to all,
   i am also one of the persons who upgraded my ubuntu server box and now i cannot get vino to work. Is there any way to make it work or we need to install x11vnc ? :confused:

Best regards.

---

### Post by Audiosears on 2011-10-26
pma,

Looks like some folks have gotten Vino to work right, though I was one of the ones who could not.  I did get x11vnc to work (see above post), but ONLY after applying the upstart script another user suggested, then rebooting.

---

### Post by satanselbow on 2011-10-26
installed x11vnc and and can now get in through my android without any superflous scripting ;)

vino is well broken AFAIK - not the first time either... pretty poor for a default client :(

---

### Post by pmamatsis on 2011-10-26
Hi my friend [Audiosears]("http://ubuntuforums.org/member.php?u=463462"),
   who have fixed vino after update to ubuntu server 11.10 ? Actually i am thinking of removing completely the compiz and the unity and have only the barebone Gnome 3 and give vino another try. How do you think guys ???

Best regards.

---

### Post by Slim Odds on 2011-10-26
> **bigclaw said:**
> <cut>
Almost, almost went back to Windows 7. Ubuntu, consider this your fair warning. :)

They are shaking in their boots....

Glad you got your problem fixed.

---

### Post by Audiosears on 2011-10-28
pma,

Well, I THOUGHT I had a good fix, but the problem was that with tightvncserver I couldn't get it to produce a full gnome desktop (e.g. no menus, etc).  I ended up going with x11vnc again, only this time I actually got it to work :P (refer to [http://ubuntuforums.org/showthread.php?t=1860295&page=3](http://ubuntuforums.org/showthread.php?t=1860295&page=3))

This is also assuming you are ok with having your server auto-login to an account on startup.  If you have gnome-session-fallback installed this should log you into a Gnome session.

(1) uninstall any vnc related packages you have, including vino / vinagre.  I use Webmin (which btw is an indispensable linux utility, especially if X breaks and you can't log in) so I can search for packages with 'vnc' in them and remove them.  It may also help to do an autoremove to purge any associated packages no longer relevant.  This step may not be necessary but it may help to get rid of other vnc-related packages that may interfere.
   *sudo apt-get remove vino vinagre -y*
   *sudo apt-get autoremove -y*

(2) remove any init or init.d startup scripts you may have put in via previous attempts / kill any vnc processes

(3) reinstall vino / vinagre and associated packages, as well as x11vnc
    *sudo apt-get install vino vinagre x11vnc*

(4) run x11vnc to set your connect password (this has to be done in a terminal rather than something like Webmin).  Remember what user account you are running this in (usually root or something like systemsadmin)
   *sudo x11vnc -storepasswd*

    You will be prompted to enter a password and verify it.  It will want to place the p/w in <user directory>/vnc/passwd, which you can have it do.

(5) tell x11vnc to store the default passwd in a general location
   *x11vnc -storepasswd in /etc/x11vnc.pass*

(6) find the password you created in step 4 and copy it over the new file you just created

(7) create a startup script for x11vnc so it executes when your machine starts.  Create it as /etc/init/x11vnc.conf with the following code:

  ```
start on login-session-start

  script
    x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900
  end script
```

(8) reboot, and you should then be able to use something like vncviewer or tightvncviewer to remote into your ubuntu box, which should require the password you entered in step 4. You should see your desktop as if you logged directly in!

---

### Post by diablo75 on 2011-10-30
Hey guys, I'm hoping in here because I'm in the same boat and have some information that might be a clue/hint about why VNC is broken.

I was trying to get my system setup to listen for incoming connections on an alternative port number, because I have more than one computer and I need to connect to either via the Internet when I'm away.

I was running a fresh install of 11.04 for about a month before the 11.10 upgrade came out and did have the alternative port working, by using the method of editing settings in gconf-editor.  Under /desktop/gnome/remote_access I noticed that every single key has a warning at the bottom that says "This key has no scheme".  I've never see that before.  What does that mean?

[IMG]http://i.imgur.com/v5fiv.png[/IMG]

---

### Post by nergaldicuthah on 2011-10-31
> This is also assuming you are ok with having your server auto-login to  an account on startup.  If you have gnome-session-fallback installed  this should log you into a Gnome session.Hi (as the starter of the above referenced thread) I thought I should let you know that the point of our thread was to get rid of the autologin need.

the script we came up with there (as quoted in this thread)
```

start on login-session-start
    script
     x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900
    end script
```
starts when LightDM starts
thus you actually get the login screen and can thusly sign in as which ever account you want. you do not need to have autologin set.

I'm also not sure yet if 
> *sudo apt-get install vino vinagre*is needed, I'm 85% sure it isn't though.

I assume you can run a similar script in upstart for tight, but maybe not.  Vino and desktop sharing are just for already logged on users, so it didn't meet our purposes; that is why that solution is for X11VNC.  I really don't know if you'll be able to get vino to work right in 11.10.  Maybe the development team will fix it.

---

### Post by iposner on 2011-11-03
I've got two machines running 11.10 - the x86 vino works correctly; the x64 vino reports that the connection has been closed. Both are patched up to date.

---

### Post by Audiosears on 2011-11-03
Can't really confirm for sure, but it does feel like X11vnc is palpably superior to vino as far as the quality of the connection on a LAN is concerned.  Using Vino previously, typically desktop lag using a remote client was 2-3 times what it is for me currently, so ultimately good did come out of a few days of frustration :)

Now if I can just get the Backup Exec RALUS agent to work again :P

Also, nerald, thanks for the tip - I'd rather avoid using an autologin if I can avoid it - I probably left it in by accident trying to get Vino to work :P

---

### Post by Morbidos on 2011-11-24
I found the solution and it's so easy...

i have posted the answer at my [blog]("http://www.nordic-vikings.net/?p=1017") 

Morb.

---

### Post by Kse on 2011-11-27
Morbidos solution worked for me.  Thanks.  :KS

---

### Post by crjackson on 2011-11-28
> **Morbidos said:**
> I found the solution and it's so easy...

i have posted the answer at my [blog]("http://www.nordic-vikings.net/?p=1017") 

Morb.


Doesn't work for me...

---

### Post by heian on 2011-12-01
hi,

This solution didn't work for me too.

Even right after a clean install it doesn't work here.

---

### Post by ext1jdh on 2011-12-11
> **Audiosears said:**
> 
**********************************
First of all, I’ve installed x11vnc:
apt-get install x11vnc

Then, I’ve created /etc/init/x11vnc.conf file:
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

After restart, x11vnc shoud listen on vnc startard port – 5900.

This script is of course based on upstart event mechanism. Lightdm emits login-session-start event (you can find it in lightdm.conf), and we start x11vnc when this event is emited – that’s first line of x11vnc.conf file.
*****************************

I've got a few 11.04 boxes, and one that was 11.04 upgraded to 11.10 which still works normally. I did the same with another machine today and it worked fine for a while before failing. This method worked for me. Cheers

---

### Post by ron43e on 2011-12-24
To JECOS, take a deep breath buddy.  Ubuntu is free.  Calm down your complaints a little.  Wow.

---

### Post by dchen on 2012-01-05
> **Audiosears said:**
> OK, I got it.  AFAIK, Vino is still broken as of the 11.10 upgrade, but I was able to get x11vnc working after finding this ([source]("http://mlepicki.com/?p=10")):

**********************************
First of all, I’ve installed x11vnc:
apt-get install x11vnc

Then, I’ve created /etc/init/x11vnc.conf file:
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

After restart, x11vnc shoud listen on vnc startard port – 5900.

This script is of course based on upstart event mechanism. Lightdm emits login-session-start event (you can find it in lightdm.conf), and we start x11vnc when this event is emited – that’s first line of x11vnc.conf file.
*****************************

I created the upstart config file, rebooted (still having my server auto-login) and I was then able to vnc back in

Hi Audiosears,

I was able to connect to the remote Ubuntu server with x11vnc installed and configured as you mentioned in the thread ONLY IF I HAVE AN USER ALREADY LOGGIN IN THE SERVER !  If the user in the remote x11vnc server logged off, then I can't connect to remote Ubuntu x11vnc server !!!  It said the connection refused from my vnc client i.e. Chichen of the VNC running from a Mac.  How do you connect to the remote x11vnc server which CURRENTLY NO USER WAS LOGGED ON in the remote server ??   does this have something to do the lightdm.conf or users.conf or keys.conf files under /etc/lightdm ? if yes, then how ?

Thx!

---

### Post by diablo75 on 2012-01-05
I just wanted to drop in and say I've been "working around" this issue with xvnc4viewer by uninstalling it and replacing it with xtightvncviewer.  It's not as good, primarily because the menu you get with the F8 key while running the viewer is sparse.  The biggest thing I used to do with the menu in xvnc4viewer was change the color/compression options to something a little more lightweight due to bandwidth/speed issues.  I can still do that with xtightvncviewer but I have to enter the option from the command line.

After replacing xvnc4viewer with xtightvncviewer the "vncviewer" alias updates itself, so at the command line I can just type:

vncviewer -listen -bgr233

The bgr233 option is a tightvnc option that reduces the colors and bandwidth usage so the above command gets me by.

But the other thing I hate about this viewer is the way it handles full screen mode.  If I'm viewing a remote desktop using a resolution that's higher than mine, it doesn't auto-scroll when I move the mouse to the edge.  Instead, I have to click on these clunky scroll bars at the edges that don't actually scroll.  You left click to make it go one way and right click to make it go the other way.  Not very smooth... but like I said, this was something I chose to do to get buy while the devs for xvnc4 get their stuff fixed.

---

### Post by dchen on 2012-01-06
Hi Audiosears,

I followed the script you mentioned above and was able to get x11vnc working ONLY IF I HAVE AN USER ALREADY LOGGED IN THE REMOTE Ubuntu x11vnc server ! If there is no login user in the Ubuntu server then I can't connect to the x11vnc server from an vnc client such as Chicken of the VNC in Mac, and got Connection refused!  How can you configure x11vnc so that I can connect to the x11vnc server without any user intervention on the server side ?
You mentioned about the Lightdm, doe sit has something to do with the lightdm.conf, users.conf, and keys.conf files under /etc/lightdm ?

thx.

---

### Post by dchen on 2012-01-07
It's my typo on the x11vnc command option line...., problem solved!

---

### Post by reverentsentinel on 2012-01-27
**(Solved) vnc4server on Ubuntu 11.10 (Oneiric Ocelot)**

                                               Posted on [January 27, 2012]("http://divyad.wordpress.com/2012/01/27/solved-vnc4server-on-ubuntu-11-1-oneiric-ocelot/")                                             
                                               Im posting this because I spent a lot of time trying multiple  things to get vnc4server up and going on the Ubuntu 11.1 system. Most  people suggest using x11vnc, which does work out of the box but does not  support multiple users.
 vnc4server is great, and up and running finally!
 Here are the steps:
 
[LIST]
[*]Install vnc4server
[LIST]
[*] sudo apt-get install vnc4server
[/LIST]
 
[/LIST]
 
[LIST]
[*]Install gdm and gnome-panel (This installs the gnome-classic.sessions session file in [COLOR=black][FONT=&quot]/usr/share/gnome-session/sessions/)[/FONT][/COLOR]:
[LIST]
[*] sudo apt-get install gdm
[*]- When asked to choose the default session manager, choose*** lightdm***
[*]sudo apt-get install gnome-panel
[/LIST]
 
[/LIST]
 
[LIST]
[*]When you launch vnc4server for the first time, you will be asked to set a password and a **/home/<user>/.vnc/xstartup** will be created for you.
[*]- vnc4server Example command: vnc4server -geometry 1024x768 :1 (creates a VNC instance of size 1024x768 an display 1) You can then use a VNC viewer on the client side to connect (I use RealVNC viewer with "<server-name>:<display-number> to connect).
[*]We need to change the contents of the /home/<user-name>/.vnc/xstartup file to get things working properly.
[/LIST]
 
[LIST]
[*]Contents should look like this:
[/LIST]
 #!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
#exec /etc/X11/xinit/xinitrc
#. /etc/X11/xinit/xinitrc
gnome-session  --session=gnome-classic &
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

  
[LIST]
[*]unset SESSION_MANAGER : Gets rid of any errors like ***&#8220;Could not acquire name on session bus &#8220;***
[*]/usr/share/gnome-session/sessions will have a bunch of .session  files. You may use any of these  in your xstartup file.  For example:
[LIST]
[*]gnome-session &#8211;session=gnome-classic & gives your classic gnome
[*]gnome-session &#8211;session=ubuntu-2d & gives you Unity
[*]gnome-session &#8211;session=ubuntu & does not work!
[*]gnome-session & will not work because the default session is &#8220;ubuntu&#8221;
[/LIST]
 
[/LIST]

---

### Post by irvin on 2012-02-11
Here's a manual for 11.10 and x11vnc with SSH !

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

---

### Post by mwclark4453 on 2012-06-27
Suggestions in the thread mostly worked great. Since I'm on 12.04 using Unity, I found the following a big help:

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

It worked great with lightdm (Unity).

---

