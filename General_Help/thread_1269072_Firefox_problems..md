---
title: "Firefox problems."
date: 2009-09-17
forum: General Help
---

### Post by Transmutation on 2009-09-17
Hi, I'm new to these forums and I don't know if I've come to the right place but I've been having problems with my Mozilla Firefox web browser, it keeps closing at random times same with all my other apps and it is getting really annoying.  Is there anyway I can fix this?

---

### Post by undecim on 2009-09-17
Are firefox and your other apps closing at the same time, or at different random times?

---

### Post by Transmutation on 2009-09-17
Usually at the same time, and if not at the same time like just a few seconds after.

---

### Post by undecim on 2009-09-17
Try running firefox from a terminal (Applications > Accessories > Terminal, then type "firefox" and press enter) and see what output you get when it crashes (if your terminal doesn't close along with it)

---

### Post by Transmutation on 2009-09-17
Okay I'll try it right now.

---

### Post by Transmutation on 2009-09-17
Nope, it still crashes.

---

### Post by undecim on 2009-09-17
Was there any meaningful text displayed in the terminal (or did the terminal close?)

---

### Post by Transmutation on 2009-09-17
My terminal closed.  I could try one more time.

---

### Post by jerrrys on 2009-09-17
If im getting this right this happens when your on FF and not when your on desktop programs..
 Are you running compiz?  Try disabling compiz and see if there is an improvement.

---

### Post by Transmutation on 2009-09-17
Whats compiz?  And now for some reason my computer won't boot up at times and when I log out it says error something about some graphics and to contact an administrator and stuff.  My computer is really messing up now!  I really need help on this now.  Does my computer have a virus or something?

---

### Post by undecim on 2009-09-17
In my experience, problems with compiz generally crash X server or just compiz dies and you have no window manager, but might as well try it.

You can disable compiz by going to appearance settings (System > Preferences > Appearance) and clicking on the "Visual Effects" tab and choosing "none"

You can also hit Alt+F2 and type "metacity --replace" if you want to disable compiz only for this session.

---

### Post by Transmutation on 2009-09-17
daniel@daniel-desktop:~$ firefox
Segmentation fault
daniel@daniel-desktop:~$ firefox
Segmentation fault

^Just got that from my terminal.  Firefox crashed twice on me right now and thats what I got.

---

### Post by undecim on 2009-09-17
> **Transmutation said:**
> Whats compiz? And now for some reason my computer won't boot up at times and when I log out it says error something about some graphics and to contact an administrator and stuff. My computer is really messing up now! I really need help on this now. Does my computer have a virus or something?

I seriously doubt that it has a virus. You don't just "get" viruses in Ubuntu unless you install them (i.e. someone tricks you into running a command to download a virus, and even then, it still needs your password to do so).

Given the error message when you log out, it seems that it is a graphics error (I'd bet you have an ATI graphics card), so we should start by disabling compiz.

Have you install the proprietary hardware drivers (System > Administration > Hardware Drivers) for your card? Those drivers give me problems at times, so unless you play a lot of games, or really love to show off your visual effects, its probably best to disable the proprietary drivers for your graphics card, and disable compiz (see my previous post)

---

### Post by oldsoundguy on 2009-09-17
first off, your computer does not have a virus unless you found one somewhere on a private site and installed it yourself.

Try playing some tunes from a cd and NOT being on line.  IF it crashes again, I would take your install cd and boot to it and run the memory test as it sounds as if a memory stick may be at fault.

Not everything that goes wrong in Ubuntu (or any operating system for that matter) can be blamed on the software.

---

### Post by jerrrys on 2009-09-17
also should link this tread to

[http://ubuntuforums.org/showthread.php?t=1267111](http://ubuntuforums.org/showthread.php?t=1267111)

---

### Post by Transmutation on 2009-09-17
> **undecim said:**
> I seriously doubt that it has a virus. You don't just "get" viruses in Ubuntu unless you install them (i.e. someone tricks you into running a command to download a virus, and even then, it still needs your password to do so).

Given the error message when you log out, it seems that it is a graphics error (I'd bet you have an ATI graphics card), so we should start by disabling compiz.

Have you install the proprietary hardware drivers (System > Administration > Hardware Drivers) for your card? Those drivers give me problems at times, so unless you play a lot of games, or really love to show off your visual effects, its probably best to disable the proprietary drivers for your graphics card, and disable compiz (see my previous post)

It says no proprietary drivers are in use on this system.  And I don't play games, I use it to watch videos and work.  I rarely get on to play games.  And I'll disable compiz right now.

---

### Post by Transmutation on 2009-09-17
And I don't have any visual effects on, its on none and actually has been.  So what could be the problem!?  Oh and I don't know if you saw my other post but when Firefox closed my terminal said "Segmentation Fault"

---

### Post by Transmutation on 2009-09-17
daniel@daniel-desktop:~$ firefox
*** glibc detected *** /usr/lib/firefox-3.0.14/firefox: double free or corruption (!prev): 0x0b089000 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d94604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d965b6]
/usr/lib/libnspr4.so(PR_Free+0x27)[0xb7c57c07]
/usr/lib/libplds4.so[0xb7fd8daf]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb734dac2]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb73449dd]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7957a59]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7957892]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7337b61]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7338cb6]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7341cde]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb73489f1]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb734909c]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7344af5]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb798e130]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb798e19b]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb798bc50]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb795c4dc]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb78df3c0]
/usr/lib/xulrunner-1.9.0.13/libxul.so[0xb7773ce4]
/usr/lib/xulrunner-1.9.0.13/libxul.so(XRE_main+0x1d6b)[0xb71d19ab]
/usr/lib/firefox-3.0.14/firefox[0x80491ab]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d3b775]
/usr/lib/firefox-3.0.14/firefox[0x8048d11]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:01 1704563    /usr/lib/firefox-3.0.14/firefox
0804f000-08050000 r--p 00006000 08:01 1704563    /usr/lib/firefox-3.0.14/firefox
08050000-08051000 rw-p 00007000 08:01 1704563    /usr/lib/firefox-3.0.14/firefox
0825b000-0b68b000 rw-p 0825b000 00:00 0          [heap]
abb60000-abb61000 ---p abb60000 00:00 0 
abb61000-ac361000 rwxp abb61000 00:00 0 
ac45a000-ac4da000 r--p 00000000 08:01 1763521    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
ac4da000-ac572000 r--p 00000000 08:01 1763456    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ac578000-ac5be000 r--p 00000000 08:01 9732180    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
ac5fa000-ac63e000 r--p 00000000 08:01 9732182    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
ac63e000-ae6c0000 rw-p ac63e000 00:00 0 
ae6d4000-ae6f3000 r--p 00000000 08:01 9732164    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
ae6f3000-ae6fa000 r-xp 00000000 08:01 1625266    /usr/lib/libkrb5support.so.0.1
ae6fa000-ae6fb000 r--p 00006000 08:01 1625266    /usr/lib/libkrb5support.so.0.1
ae6fb000-ae6fc000 rw-p 00007000 08:01 1625266    /usr/lib/libkrb5support.so.0.1
ae6fc000-ae71e000 r-xp 00000000 08:01 1625258    /usr/lib/libk5crypto.so.3.1
ae71e000-ae71f000 r--p 00022000 08:01 1625258    /usr/lib/libk5crypto.so.3.1
ae71f000-ae720000 rw-p 00023000 08:01 1625258    /usr/lib/libk5crypto.so.3.1
ae720000-ae7af000 r-xp 00000000 08:01 1625264    /usr/lib/libkrb5.so.3.3
ae7af000-ae7b1000 r--p 0008e000 08:01 1625264    /usr/lib/libkrb5.so.3.3
ae7b1000-ae7b2000 rw-p 00090000 08:01 1625264    /usr/lib/libkrb5.so.3.3
ae7b2000-ae7c8000 r-xp 00000000 08:01 1622941    /usr/lib/libsasl2.so.2.0.22
ae7c8000-ae7c9000 r--p 00015000 08:01 1622941    /usr/lib/libsasl2.so.2.0.22
ae7c9000-ae7ca000 rw-p 00016000 08:01 1622941    /usr/lib/libsasl2.so.2.0.22
ae7ca000-ae8fd000 r-xp 00000000 08:01 7473501    /lib/i686/cmov/libcrypto.so.0.9.8
ae8fd000-ae905000 r--p 00132000 08:01 7473501    /lib/i686/cmov/libcrypto.so.0.9.8
ae905000-ae912000 rw-p 0013a000 08:01 7473501    /lib/i686/cmov/libcrypto.so.0.9.8
ae912000-ae916000 rw-p ae912000 00:00 0 
ae916000-ae958000 r-xp 00000000 08:01 7473502    /lib/i686/cmov/libssl.so.0.9.8
ae958000-ae959000 ---p 00042000 08:01 7473502    /lib/i686/cmov/libssl.so.0.9.8
ae959000-ae95a000 r--p 00042000 08:01 7473502    /lib/i686/cmov/libssl.so.0.9.8
ae95a000-ae95d000 rw-p 00043000 08:01 7473502    /lib/i686/cmov/libssl.so.0.9.8
ae95d000-ae986000 r-xp 00000000 08:01 1625113    /usr/lib/libgssapi_krb5.so.2.2
ae986000-ae987000 r--p 00028000 08:01 1625113    /usr/lib/libgssapi_krb5.so.2.2
ae987000-ae988000 rw-p 00029000 08:01 1625113    /usr/lib/libgssapi_krb5.so.2.2
ae988000-ae9c8000 r-xp 00000000 08:01 1625275    /usr/lib/libldap_r-2.4.so.2.4.1
ae9c8000-ae9c9000 ---p 00040000 08:01 1625275    /usr/lib/libldap_r-2.4.so.2.4.1
ae9c9000-ae9ca000 r--p 00040000 08:01 1625275    /usr/lib/libldap_r-2.4.so.2.4.1
ae9ca000-ae9cb000 rw-p 00041000 08:01 1625275    /usr/lib/libldap_r-2.4.so.2.4.1
ae9cb000-ae9cc000 rw-p ae9cb000 00:00 0 
ae9cc000-ae9fc000 r-xp 00000000 08:01 1625238    /usr/lib/libidn.so.11.5.39
ae9fc000-ae9fd000 ---p 00030000 08:01 1625238    /usr/lib/libidn.so.11.5.39
ae9fd000-ae9fe000 r--p 00030000 08:01 1625238    /usr/lib/libidn.so.11.5.39
ae9fe000-ae9ff000 rw-p 00031000 08:01 1625238    /usr/lib/libidn.so.11.5.39
ae9ff000-aea00000 ---p ae9ff000 00:00 0 
aea00000-af200000 rwxp aea00000 00:00 0 
af200000-af2fe000 rw-p af200000 00:00 0 
af2fe000-af300000 ---p af2fe000 00:00 0 
af307000-af313000 r-xp 00000000 08:01 1625270    /usr/lib/liblber-2.4.so.2.4.1
af313000-af314000 r--p 0000b000 08:01 1625270    /usr/lib/liblber-2.4.so.2.4.1
af314000-af315000 rw-p 0000c000 08:01 1625270    /usr/lib/liblber-2.4.so.2.4.1
af315000-af351000 r-xp 00000000 08:01 1623355    /usr/lib/libcurl.so.4.1.0
af351000-af352000 r--p 0003c000 08:01 1623355    /usr/lib/libcurl.so.4.1.0
af352000-af353000 rw-p 0003d000 08:01 1623355    /usr/lib/libcurl.so.4.1.0
af387000-af3d8000 r--p 00000000 08:01 1763460    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
af3d8000-af3f0000 r-xp 00000000 08:01 1712542    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
af3f0000-af3f1000 r--p 00018000 08:01 1712542    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
af3f1000-af3f2000 rw-p 00019000 08:01 1712542    /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
af3f2000-af409000 r-xp 00000000 08:01 1712541    /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
af409000-af40a000 r--p 00016000 08:01 1712541    /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
af40a000-af40b000 rw-p 00017000 08:01 1712541    /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
af40b000-af41d000 r-xp 00000000 08:01 1712544    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
af41d000-af41e000 r--p 00011000 08:01 1712544    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
af41e000-af41f000 rw-p 00012000 08:01 1712544    /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
af41f000-af437000 r--s 00000000 08:01 1712633    /usr/share/mime/mime.cache
af437000-af439000 r-xp 00000000 08:01 1625572    /usr/lib/libtotem-plparser-mini.so.12.2.5
af439000-af43a000 r--p 00001000 08:01 1625572    /usr/lib/libtotem-plparser-mini.so.12.2.5
af43a000-af43b000 rw-p 00002000 08:01 1625572    /usr/lib/libtotem-plparser-mini.so.12.2.5
af44e000-af4a3000 r-xp 00000000 08:01 1625368    /usr/lib/liboil-0.3.so.0.3.0
af4a3000-af4a4000 r--p 00054000 08:01 1625368    /usr/lib/liboil-0.3.so.0.3.0
af4a4000-af4bb000 rw-p 00055000 08:01 1625368    /usr/lib/liboil-0.3.so.0.3.0
af4bb000-af4bd000 rw-p af4bb000 00:00 0 
af4bd000-af561000 r-xp 00000000 08:01 1626118    /usr/lib/libxvidcore.so.4.1
af561000-af562000 rw-p 000a3000 08:01 1626118    /usr/lib/libxvidcore.so.4.1
af562000-af5d5000 rw-p af562000 00:00 0 
af5d5000-af668000 r-xp 00000000 08:01 1626117    /usr/lib/libx264.so.65
af668000-af669000 r--p 00093000 08:01 1626117    /usr/lib/libx264.so.65
af669000-af66a000 rw-p 00094000 08:01 1626117    /usr/lib/libx264.so.65
af66a000-af66c000 rw-p af66a000 00:00 0 
af66c000-af677000 r-xp 00000000 08:01 1625602    /usr/lib/libvorbisenc.so.2.0.3
af677000-af678000 r--p 0000a000 08:01 1625602    /usr/lib/libvorbisenc.so.2.0.3
af678000-af766000 rw-p 0000b000 08:01 1625602    /usr/lib/libvorbisenc.so.2.0.3
af766000-af7b5000 r-xp 00000000 08:01 1625563    /usr/lib/libtheora.so.0.3.4
af7b5000-af7b6000 r--p 0004e000 08:01 1625563    /usr/lib/libtheora.so.0.3.4
af7b6000-af7b7000 rw-p 0004f000 08:01 1625563    /usr/lib/libtheora.so.0.3.4
af7b7000-af7cc000 r-xp 00000000 08:01 1625535    /usr/lib/libspeex.so.1.5.0
af7cc000-af7cd000 r--p 00014000 08:01 1625535    /usr/lib/libspeex.so.1.5.0
af7cd000-af7ce000 rw-p 00015000 08:01 1625535    /usr/lib/libspeex.so.1.5.0
af7ce000-af83b000 r-xp 00000000 08:01 1625494    /usr/lib/libschroedinger-1.0.so.0.1.0
af83b000-af83c000 r--p 0006d000 08:01 1625494    /usr/lib/libschroedinger-1.0.so.0.1.0
af83c000-af83d000 rw-p 0006e000 08:01 1625494    /usr/lib/libschroedinger-1.0.so.0.1.0
af83d000-af83e000 rw-p af83d000 00:00 0 
af83e000-af880000 r-xp 00000


^Ummmm what in the world does that mean!?!?!?!?!?

---

### Post by jerrrys on 2009-09-17
"Segmentation Fault"; memory management?  do not pass goal, return to post #14

---

### Post by undecim on 2009-09-17
All that stuff is just details about the crash, which is useful when someone discovers a software bug because they can submit that to the developers (kind of like the crash reports windows asks you to send, except if you send this in, something actually gets done about it if its a software issue.)

though at this point, I would definitely agree with oldsoundguy that this is a problem with faulty hardware. Try booting your ubuntu CD and running the memory test option (from the menu that "try ubuntu" option) as he suggested in post #14.

---

