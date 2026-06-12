---
title: "NVidia Dual Screen"
date: 2006-04-10
forum: General Help
---

### Post by marc5000 on 2006-04-10
Hi, I am new to this, so please explain everything when replying! Thanks

Ok, so I have an NVidia Geforce  5500 (256) with the relevant NVidia drivers installed. And I managed to get my primary screen working, and the other one is off, which i expected. When I turn it on, obviously nothing comes up (no signal). I am aware that the xorg.conf needs to be configured. So can please someone help me, I really want dual screen back! 

Thanks 
Marc5000

---

### Post by frodon on 2006-04-10
Do you want to enable the TV-OUT output of your nvidia card ?
If yes you should read that : [http://doc.gwos.org/index.php/NvidiaTvOut](http://doc.gwos.org/index.php/NvidiaTvOut)

---

### Post by marc5000 on 2006-04-10
No no, on my graphics card, I have a VGA output, wich works fine as my primary display (19" Flat Screen) But on my DVi Output, no signal, which is what I expeted. I need to know how to enable the DVi output for my secondary display by configuring "xorg.conf" but I have no idea where to start ?!? :-k  Would be great if someone could lead me to a very easy explanation on how to do it. Please.

Marc5000

---

### Post by frodon on 2006-04-10
Ok, i think this is a more suitable guide, it should help you to start : [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

---

### Post by larytet on 2007-12-12
Ubuntu 7.10 supports dual head. Works with Nvidia on my laptop VAIO VGN-S460
I had some problems switching between the resolutions, but eventually got the setups to work with one and two screens. i did not touch X configuration files

---

### Post by O_Man_RA23 on 2008-02-07
Gday all,

I have an NVidia 7800 GTX by XFX running dual 19" Samsung 940n monitors.  I can get the primary monitor to work perfectly, but every time I try to run dual screens, the resolution goes wonky and the backplane for the screens becomes larger than the screens themselves (ie I can scroll around by putting the cursor on the edge of the screen, the whole picture does not fit in a screen).  I just tried the method linked which involves modifying the xorg.conf but was denied access to save anything in that directory.

I am running Ubuntu 7.10 Gutsy, and have the NVidia restricted drivers installed.  Both outputs are DVI, and I have not tried the SVideo out (but assume that just assimilates the primary screen)

I am a programmer by profession, but I program logic controllers and dabble in the black art of VBA.  I have also done some C and C++ as well as assembly and machine coding.  I have a bachelor's degree in Electrical/Electronic Engineering, and started programming etc from an early age, but did not make it my main focus.  This is the first time I have played with Linux, though I have been a fan of the OS for a long time, I have not until now had the ability to use it as I have always required Windoze compatible software for education purposes.

I eventually would like to run a VM session of WinXP (legitimate copy), but must get the system working first.  I am also having troubles with Flash and printers, but have not looked heavily into those, and they are problems for another thread.

So, if anyone has quick and easy pointers for what I may be doing wrong, or not doing, please let me know.  I dont get much time on my computer each day, but am trying my best to learn the layout and structure of Linux, as well as the Terminal commands (I used to be proficient in MSDOS)

:guitar:

---

