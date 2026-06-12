---
title: "Problems after update/crash"
date: 2012-02-29
forum: General Help
---

### Post by dave2001 on 2012-02-29
After a recent notification from update-manager, I downloaded the security/suggested updates and rebooted.. walked away without seeing if it loaded up right. A bit later, I was working on some electrical wiring in another room, and flipped the breaker off. I didn't remember that the outlet the desktop is plugged into is also on the same breaker, so the power got cut to it as well. 

I went to turn it on again... normal Bios screen, then: BSOD!

I've been running 11.04 on an old Dell Dimension 2350, with an added nvidia Geforce 8400GS graphics card. The rest is stock except for a new hard-drive. 

I tried rebooting and switching to the on-board graphics-processor via bios, to see if the nvidia was causing problem... got a little further. Now the normal "Ubuntu" loading screen appears, log-in normally, then the desktop loads. BUT the desktop has no icons, bars, etc. (using classic). I can't even open a prompt with alt+F2. The mouse works but clicking has no effect (there's not really anything to click on anyway, just the wallpaper). Pressing ctrl+alt+backspace to restart X gives me another non-responsive black screen. Only way I can get out of it is the RSEIUB sequence.

Would love suggestions! I can't just do a re-install from scratch for various reasons. I need to fix the current installation. Thanks in advance for any help!

---

### Post by imachavel on 2012-02-29
Very strange. Blue screened. You found out it wasn't ram but was the video interface adapter? What did you do switch from expansion slot gpu to onboard? Lsmod in the terminal please, looks like your driver was installed for the expansion card gpu and not onboard, and that Ubuntu is now runnin in some type of safe mode with a generic driver. I'm just guessing of course. But the hdd booted, and now Linux OS has loaded, boot sector and grub are fine. Could be something else is corrupted, and that the issues are of course unrelated. 

What model is your pc, I need to know the mobo and onboard gpu. For sure your blue screen was gpu expansion slot added in hardware failure?

---

### Post by dave2001 on 2012-02-29
Thanks for the interest Imachavel! :D
Sorry for not being specific.. initially I was getting a BLACK screen o' death. 

Yes, I switched from an expansion slot nvidia 8400gs to the onboard integrated graphics, and managed to login normaly, and get a desktop (albeit a completely non-responsive one).

The computer info is: (what i can remember of it, since I'm not at home)
Maker: Dell
Model: Dimension 2350
Onboard Graphics: Integrated Intel 845GL chip.
CPU: Pentium 4 (don't remember freq)
Memory: 1GB


I think your right about the nvidia driver getting messed up somehow, and Ubuntu then defaulted to the onboard intel chip. However, I think that's not working because the intel driver has bugs with the 845GL chips. That's why I got the nvidia card in the first place. 

I'm not sure how to get a terminal since the desktop environment is completely non-responsive. When I'm at home tomorrow, I'll try to get a tty prompt instead of booting into desktop enviro, then post any headway I make.

---

### Post by raja.genupula on 2012-03-01
ok please do this ```
unity--reset
```in terminal and reboot. If this wont help reinstall your graphics drivers .

---

### Post by dave2001 on 2012-03-01
Thanks for the suggestion Raja,
Maybe I wasn't clear somehow, so I'll restate

Once again,
My desktop environment is *completely* non-responsive after logging in. I can't open a terminal. I can't open an Alt+F2 window. I can't open anything. There aren't even any icons or task bars to click on. The *only* thing I can do is move the mouse.

Also as stated earlier, I'm using the "classic desktop". Unity sucks a fat one on old hardware. So i doubt resetting Unity will do much.

---

### Post by raja.genupula on 2012-03-02
Hi , here we go 
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by dave2001 on 2012-03-02
Thanks again for the suggestion Raja. It's not very useful to me though because; I don't use Unity. I hate Unity and think it was a poor move for Ubuntu. I use the "Classic Desktop" option at the login page, which is the old gnome desktop. I'm pretty sure I even uninstalled Unity right after I first installed 11.04, but that was a long time ago, right after release.

From my work so far I have determined it's probably a software related graphics problem. I can get to a tty prompt by starting Ubuntu in recovery mode at the grub menu. I'm just not sure where to go from there. I've checked to make sure all packages are upgraded and not damaged.

On a side note (I don't know if this has anything to do with the problem) I was using Emerald as my window manager. I complied it from source on my system, and it was working flawlessly for several months with the repository versions of compiz and ccsm.

---

### Post by thebigbry on 2012-03-03
Interesting, I have no helpful input but am having similar issues so i will be watching.

I do not mean to highjack thread but will piggy back for right now. because I think this is similar enough.

 I have an OLD laptop that was not working well so I put Ubuntu dual booting with windows for my daughter. It was very slow VERY so she never used it. I finally decided to just load Ubuntu and let it have the entire machine. I used my previous version disc that I had. I know it works because it is what I run on my main computer.
 This worked kind of. it made it load faster and works pretty good. Only problem is sometimes it will just stop responding. you can move the mouse but can not click anything and no popup bubble will appear like when hovering over the menu bar. No keyboard or reset nothing. Only power it down with physical power button. and then sometimes/randomly after loading it will again not respond. You can move the mouse but can not click. The login screen is their but the cursor is not flashing in the box. Again only thing to do is power reset. and again it may or may not work. loading the disc to check for errors would not work either.
This was all the previous version of Ubuntu I then decided to go and check for updates. I then loaded the newest version 11.10 and loaded it on. I chose replace current version,  loaded it up and have the same results minus the times it works. I have yet to get a working load. every time it is the same reuslts as before. Move the mouse but no other responses.

---

### Post by raja.genupula on 2012-03-03
@thebigbry please start a new thread for better solution to your problem.

---

### Post by raja.genupula on 2012-03-03
@op from that recovery mode , choose failsafeX mode and then from there reinstall graphics drivers .

---

### Post by dave2001 on 2012-03-03
> **raja.genupula said:**
> @op from that recovery mode , choose failsafeX mode and then from there reinstall graphics drivers .

Yep, tried that before I bothered to post here. I get the same non-responsive desktop even in failsafe graphics mode.

I guess I'll just try reinstalling the graphics drivers via tty prompt.

---

