---
title: "Intel graphics: Blank screen on bootup after 'i915: no option &quot;modeset&quot; '."
date: 2010-05-06
forum: General Help
---

### Post by ida.noeman on 2010-05-06
I get a blank screen on boot using my laptop.

I have tried removing "quiet splash" for "i915.modeset=0 xforcevesa", but I get the message "i915: no option 'modeset' ", and then it goes blank as before.

I'm not sure whether I actually have a 915 chipset or not, all I know is that I have a 4-year-old intel integrated graphics chip.  

Any help?  This is getting very frustrating =[

---

### Post by -humanaut- on 2010-05-06
Try to login and hit ctrl+alt+f1 and see if you can get to a TTY console and set NOMODESET

---

### Post by ida.noeman on 2010-05-06
I tried that. I can't get a console.  Also nomodeset when set in grub does nothing as well.

---

### Post by Catharsis on 2010-05-06
Try adding "i915.modeset=1" instead of "i915.modeset=0 xforcevesa".

You can also try "xforcevesa noapic noapci nosplash irqpoll".

If you can boot into your laptop with another install or LiveCD, you can check which graphics card you have with "lspci | grep VGA" in a terminal.

---

### Post by ida.noeman on 2010-05-06
Those options behave the same.

My graphics card is 82852/855GM.

I can boot in recovery mode -> limited graphics mode.  Backed up all my files...

---

### Post by Catharsis on 2010-05-06
How did your install become unbootable? Did you recently upgrade to Lucid?

That's good that you can get through Recovery Mode. You could try making it fix your graphics or take a look through the logs for oddities (Xorg.0.log and dmesg are good ones).

---

### Post by ida.noeman on 2010-05-06
Yeah, I should have said that.  10.04 broke everything =/  And for some reason my Linux Mint install disk and usb drive don't work either.

---

### Post by Catharsis on 2010-05-06
i855 is known to be broken on Lucid, which is why it's giving you so many problems. See:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Along with the above, you can try:

```
Xorg -configure
```
```
sudo dpkg-reconfigure xserver-xorg
```

You can try updating your intel driver:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

You can also try updating to the mainline kernel:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
```

Some people also have problems with the nVidia drivers competing with the intel ones after the upgrade; remove them with:
```
sudo apt-get --purge remove nvidia*
```
Just be careful to read what it wants to remove first.

Or it could have been a bad upgrade. Any error messages or other oddities?

---

### Post by ida.noeman on 2010-05-06
Thanks!  That worked =]  I love you guys.

---

### Post by Catharsis on 2010-05-06
Excellent! Grats on your new LTS :)

Do you mind saying which fix worked for you?

---

### Post by BambooClaw on 2010-05-07
I had the same problem, Intel 855GM chipset.  

What fixed it for me was upgrading to the mainline kernel 'v2.6.34-rc6-lucid', thank you for suggestion - Catharsis.

---

### Post by Catharsis on 2010-05-07
I should note that upgrading to a mainline kernel is really a last resort. 

1) It doesn't have ubuntu-specific kernel patches such as ureadahead (which is responsible for the lightning-fast boot).

2) Proprietary graphics drivers (from System->Administration->Hardware Drivers, i.e. nVidia, Broadcom) can't be enabled.

3) It doesn't automatically update to a new kernel version, so you constantly have to check upstream for security and stability releases.

4) For me at least, graphics performance is actually noticeably worse on my i855 with 2.6.34-rc6 compared to 2.6.32-22 with KMS enabled (i915.modeset=1).

But hey, your system boots. Huzzah, right?

---

### Post by ida.noeman on 2010-05-07
Hehe, I didn't do it too scientifically.  The Vesa driver didn't give me the screen resolution I wanted, but the Intel driver did.  I also did solution (A) in the link and updated the kernel at the same time though...

---

### Post by pulli on 2010-05-11
I had a similar issue with the onboard Intel graphics card in my old compaq presario booting in to 10.04. The monitor blinks a couple of times at the purple booting screen and then the screen goes blank. I got 'no input signal' message on the monitor and no response to console switching or what so ever.

**The work around** was
1. Select 'Recovery mode' at the GRUB menu
2. In the subsequent menu, select console (with or w/o networking) option
3. log-in
4. Issue startx command and the screen come alive with X

**Fix** (or what worked for me: *may not the best solution!*)
Once you are in the gnome
1. Start shell (do not try to play around with the x at this point, I had it frozen when tried)
2. go to /etc/X11
3. sudo cp xorg.conf.* xorg.conf (this will copy the graphics safe recovery mode xorg.conf to the real one which was never created by the system in the first place.)
4. restart in to normal boot

---

### Post by lightstream on 2010-05-11
I also have onboard Intel graphics, GMA 3150 graphics controller on the Intel D510MO Desktop Board. This is a fairly recent motherboard, with a built-in dual-core Intel Atom, but the graphics are rather underspecified.

It wouldn't boot once Lucid was installed - all I got was black and white flickers going up and down the screen, but I could get a TTY with Ctrl-Alt-F1. Also using **i915.modeset=0** partly fixed the issue and allowed me to boot into X ok.

However I can't access all the monitor's resolutions still - specifically it appears limited to 60Hz which I find hard on the eyes.

Anyway I'll try some of the other fixes on this thread and see if that will get me any further. I'll post back my results!

---

### Post by marbss on 2010-05-12
> **Catharsis said:**
> 

You can also try updating to the mainline kernel:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
```



Upgrading the kernal worked on my IBM thinkpad x40 2371-E8U.  Thanks Catharsis!  

I tried the re-enable KMS ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)) after doing a clean install with the ubuntu 10.04 alternate cd. Re-enabling KMS got my display back without having to boot to recovery mode, however I a few days later I realised I could not view divx/xvid avi files (after installing the Ubuntu restricted extras).    I tried all the other methods Catharsis mentioned but did not have any luck.  The kernal update worked.  

I'm glad Catharsis posted this workaround/fix, however I'm a bit disappointed that my clean installs did not go as smooth as Ubuntu 9.xx.  Next time, I will wait until the first normal release after the new LTS before upgrading/installing.

---

### Post by ida.noeman on 2010-05-12
I got it working.  I'm using the Intel driver, not Vesa, since Vesa didn't give me the correct screen resolution.

---

### Post by marbss on 2010-05-13
> **ida.noeman said:**
> I got it working.  I'm using the Intel driver, not Vesa, since Vesa didn't give me the correct screen resolution.

can you play avi/divx/xvid properly?

---

### Post by piratebill on 2010-05-17
> **marbss said:**
> can you play avi/divx/xvid properly?

I cant.  Although with the new driver compiz is running better than it ever has before.  X freezes when ever I try to play video now, even flash.  anyone got a fix?

---

