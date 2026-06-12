---
title: "install ATI Catalyst 10.2 in Karmic instructions"
date: 2010-02-18
forum: General Help
---

### Post by hankafyin on 2010-02-18
I dual boot on separate HHDs.  I have just done a fresh install with updates.  I installed the restricted driver from the repositories, and I get an error message from ati catalyst (administration).  Also I have "unsupported hardware" at the bottom of the screen.

Graphics card is a XFX ATI HD 5770 on this system, and I just sold 2 8800 GT's yesterday, and bought two more XFX HD 5770's for CF in my other system.

Please tell me I didn't do a bad thing, 'cause I was really groovin' on Ubuntu, that I just installed at the beginning of the week.

I was hoping to learn and adopt the whole open source concept.

I have tried many post, with no joy, and have resigned to bother someone for help. 

I am stopping at a fresh install with updates...until I get some assistance, or more patience.

---

### Post by pme 72 on 2010-02-19
The proprietary driver from the repositories is probably version 9.10 which may not have had support for your new card. I have read posts from series 5000 owners on the forum with similar concerns. Try using the Search function, upper right corner, and enter your card name.

---

### Post by chronniff on 2010-02-20
I have a 5770, and have been running ubuntu karmic with relatively no problems....however catalyst 10.2 caused me some major issues...I would stick with catalyst 10.1 since I was running it with no problems other than the usual tearing issues that I was able to rectify in tweaking compiz settings

---

### Post by salemboot on 2010-02-21
List the problems.

I have a 4200HD integrated into my motherboard.  10.2 Catalyst disposed of my ability to use compiz features.  But all my openGL based games work fine.  Nexiuz for instances.:popcorn:

To the original poster, which os did you install?  64bit or 32bit?

I usually download the .run file from ati.  sudo sh ati....run
wget "https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-2-x86.x86_64.run"
sudo sh ./ati*run


cross fingers and pray :)

---

### Post by chronniff on 2010-02-22
on 10.2 when I installed compiz definately crashes and x hangs on VT switching etc., which is where I gave up the first time.....yesterday I gave it the old second effort and I noticed that after compiz crashed, if went to through the appearance settings to enable desktop effects, it would search for the driver and find it, and compiz would run just fine no matter what settings I applied.  So from what I can tell after tinkering around with the settings for a while, it seems that if you keep the default ubuntu compiz settings, you can start startup the system without compiz crashing.....However if enable the desktop cube settings and try and  restart the system, compiz will crash every time on the next startup......I'm guessing there is some kind of bug going on between fglrx's opengl 3d acceleration and compiz's opengl 3d code....however I have noticed when running fgl_glxgears and various other 3d software, that 10.2's 3d acceleration is a good deal faster than on 10.1 (could just be the driver catching up to my new 5770) which would be fantatistic, except that it breaks the f___ing 3d desktop at the same time

---

### Post by Mega_Mike on 2010-03-01
> **salemboot said:**
> List the problems.

I have a 4200HD integrated into my motherboard.  10.2 Catalyst disposed of my ability to use compiz features.  But all my openGL based games work fine.  Nexiuz for instances.:popcorn:

To the original poster, which os did you install?  64bit or 32bit?

I usually download the .run file from ati.  sudo sh ati....run
wget "https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-2-x86.x86_64.run"
sudo sh ./ati*run


cross fingers and pray :)

Yup, I have a integrated HD 4200 as well.  10.2 completely broke Compiz.  Version 10.1 works fantastic once you jump thru the hoops to get the debian package generation script working.

---

### Post by salemboot on 2010-03-05
Boot into recovery mode

At startup before the grub loading menu appears, hit and hold the shift button.


choose Recovery mode.

Once booted choose root with networking.  

wget "https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-2-x86.x86_64.run"
sh ./ati*run

Follow the instructions choosing defaults.

Then type exit and choose normal boot.

Log in as yourself and type startx.

See if the effects are all working now.  Mine are.

---

### Post by salemboot on 2010-03-08
I've had to roll back to 10.1.
Compiz segfaults on Desktop Cube.
But oops look there is a pulseaudio reference.  I didn't notice it until this morning.

Mar  7 11:25:49 myhost kernel: [   43.075428] compiz.real[2363]: segfault at 1d9c000 ip 00007f441f1f469b sp 00007fff0e117f98 error 4 in libc-2.10.1.so[7f441f172000+166000]
Mar  7 11:34:56 myhost pulseaudio[2210]: ratelimit.c: 32 events suppressed
Mar  7 11:36:40 myhost kernel: [  694.096866] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.098351] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.099839] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.101351] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.102837] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.104311] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.105311] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.106795] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.108277] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_rs780.c at line: 53
Mar  7 11:36:40 myhost kernel: [  694.109761] Assertion failed in ../../../../.:

---

### Post by vertago1 on 2010-03-08
I use Kubuntu 9.10 x86_64 with kde 4.4.1 from the backports

When I installed catalyst 10.2, KDE couldn't get pasted the splash screen after logging in. I had to revert back to 10.1

---

### Post by MerlinW on 2010-03-13
I made a little script for myself, which installs the latest Catalyst driver.

Maybe can use somebody else too...
[ati-ccc-installer.sh]("http://merlinw.org/scripts/ati-ccc-installer.sh")

---

### Post by vertago1 on 2010-03-13
Does anyone get this error when trying to build the package?

> dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.IAJmEM

---

### Post by SeePU on 2010-03-15
I am wondering about the issues in fglrx (ATI proprietary driver) since I am considering the Radeon HD 5770 card.

I am concerned about issues related to watching video such as tearing.  Also, I read about when moving windows etc.  Can 'correct' configuration deal with these issues or avoid them entirely?

---

### Post by Mark Phelps on 2010-03-16
> **SeePU said:**
> I am wondering about the issues in fglrx (ATI proprietary driver) since I am considering the Radeon HD 5770 card.

I am concerned about issues related to watching video such as tearing.  Also, I read about when moving windows etc.  Can 'correct' configuration deal with these issues or avoid them entirely?

Not bashing anyone in this forum ... but the best place to go with detailed ATI card questions is the Phoronix forums.  They do a LOT of work with ATI cards and drivers.

---

### Post by JuLx6 on 2010-03-23
-

---

### Post by JuLx6 on 2010-03-23
> **vertago1 said:**
> Does anyone get this error when trying to build the package?

Yes, plus a lot of others. Anyone has a clue ?


dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.AnTBUw

---

### Post by vertago1 on 2010-03-23
I found out from phoronix that there was a missing symbolic link in the package building tools for ubuntu, but that didn't solve the problem I had.

> dh_link -p$(PKG_driver) usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1

---

### Post by JuLx6 on 2010-03-24
> **vertago1 said:**
> I found out from phoronix that there was a missing symbolic link in the package building tools for ubuntu, but that didn't solve the problem I had.

So where should I add that ?

---

### Post by sokam on 2010-03-24
I also have a 4200HD integrated into my motherboard.  It was the fry's special a couple weeks ago.  I am having this weird problem here:

[http://ubuntuforums.org/showthread.php?t=1432577](http://ubuntuforums.org/showthread.php?t=1432577)

Anyone else have the same issue?

---

### Post by lacktorium on 2010-03-25
> **JuLx6 said:**
> Yes, plus a lot of others. Anyone has a clue ?


dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.AnTBUw

I am having the same issue, any one have any idea's?

---

### Post by JuLx6 on 2010-03-25
> **lacktorium said:**
> I am having the same issue, any one have any idea's?

I finally managed to build the .debs, but I don't know exactly why nor how... I think what did it was disabling the proprietary driver, but I'm not sure since after I messed with the configuration Ubuntu kept booting in "basic graphic mode", or whatever that's called, and I tried several things to sort this out.

Anyway, now that the new 10.3 version of the driver is out, I'll have to do it again...

---

### Post by JuLx6 on 2010-03-25
No problem this time. Straight as Boot, dl new 10.3 driver, build .debs, install .debs, reboot...

---

### Post by John Wolf416 on 2010-03-25
It must be a common problem with HD5XXX Driver.
I have the same problem With my HD5450 but my other computer which has a HD4750 took the appropriate driver just fine. AMD (aka) ATI has a special forum for Unix users plus direct contact with Ubuntu liaisons. I expect updated drivers soon. The native drivers with Ubuntu support open GL but not 3D.

---

