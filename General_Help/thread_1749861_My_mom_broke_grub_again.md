---
title: "My mom broke grub *again*"
date: 2011-05-04
forum: General Help
---

### Post by nickajeglin on 2011-05-04
I'm using the info here to try to boot: [https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Right now I've tried every single combination of hdd and partition and the only commands that get me anywhere are these: 

```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

This loads a bunch of things that fly by generally too fast for me to read, then halts at a black screen that never loads up a prompt or an environment of any sort. Any other combination complains about partitions not existing, or drops me to some busybox thing, with an (initramfs) prompt. I'm almost sure I have the correct partition on the correct drive here, so does anyone have any ideas? 

ps, this isn't a dual boot system, it only has ubuntu on it.

---

### Post by deconstrained on 2011-05-04
If all she did was upgrade Ubuntu to 11.04...then she can't be faulted. The myriad post-installation hooks improperly reinstalled grub and built a non-functional initramfs when I upgraded as well. 

I can't think of anything an average user could do short of reinstalling Windows or "repairing" the MBR with a Windows tool that might damage/remove grub. Anyhow, to fix it you can either reinstall Ubuntu (waste of time, in my opinion) or rescue it with a livedisk and chrooting.

---

### Post by wilee-nilee on 2011-05-04
Here is a link that starts at the reload of grub2 from a live cd, there is the chroot option and another below it as well.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you get grub loaded and get a grub menu but still boot to a black screen, reboot, at the grub menu hit e use the arrow keys to navigate to the no splash, and replace it with nomodeset, the n hit crtl-x, then boot in at the command and run startx to start the desktop. This is a low graphics per session boot.

It may be a simple as a reloading of grub, and or the graphic drivers as well.

With a single install you may need to hold down the shift key for the menu to appear. Might be any key now not sure .

---

### Post by nickajeglin on 2011-05-08
Thanks wilee, I'll give the disk a try and hopefully an update-grub will fix it. I looked through that documentation a bit more and just realized that the grub command line can browse through the contents of those partitions, so that will take a lot of guesswork out of the equation if it's more complicated.

---

### Post by nickajeglin on 2011-05-11
All right. As of now, I've got it booting. I used the chroot method to get a grub menu then I did what wilee suggested with the nomodeset. Once I got booted I edited that change into grub.cfg (Which it says not to do by the way) So my question now is: What is nomodeset, why does it prevent the black screen issue, and will I have to rewrite the grub.cfg next time my mother upgrades?

---

### Post by nickajeglin on 2011-05-11
Wait. I found it here: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html) Sounds like nvidia is the culprit. Thanks for the help everyone.

---

### Post by drs305 on 2011-05-11
Once you install the video driver you shouldn't need the nomodeset option. 

However, if you do need to use it on a more permanent basis, rather than putting it in grub.cfg add it to the end of the "GRUB_CMDLINE_LINUX_DEFAULT=" line in /etc/default/grub. 

Run 'sudo update-grub' to include it in grub.cfg

---

### Post by nickajeglin on 2011-05-12
THANKS!
no more updating for me
Mom

---

