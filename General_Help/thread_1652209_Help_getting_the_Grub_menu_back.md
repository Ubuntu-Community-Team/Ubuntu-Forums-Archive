---
title: "Help getting the Grub menu back"
date: 2010-12-24
forum: General Help
---

### Post by kshaff03 on 2010-12-24
This is an existing 10.4 installation, I decided to install XFCE through the package manager, hoping to get a little bit better performance. After I rebooted, I was greeted with the Grub command prompt. Not sure if this triggered this issue or whether it is convenience.

I can boot into my system using the command line, however, I can't get Grub to use my menu again.  Grub version is 1.98 (which I guess makes it Grub2). I've tried grub-install and grub-upate, neither of which returns any errors, however, after rebooting I still see the command prompt. I have verified that the config file in /boot/grub/grub.cfg does exist and appears to be correct as far as I can tell.  

Is there something I need to do to tell grub to look at this config file and display the menu?

---

### Post by akand074 on 2010-12-24
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Hope this helps.

---

### Post by amsterdamharu on 2010-12-24
Can you run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") and post the results?

---

### Post by kshaff03 on 2010-12-24
Thanks for your replies.

amsterdamharu, 

I've attached the report. 


akand074,

I'll take a look at the link you've provided and I'll let you know if I make any progress.

Thanks again,

--Kevin

---

### Post by kshaff03 on 2010-12-24
> **akand074 said:**
> [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Hope this helps.


I took a look at the link. Since, I can actually boot into my system (grub works using the command line), I tried the suggestions referenced in the chroot method, which advised using grub-update and grub install /dev/sda. I had already tried that and have tried it again, but to no avail :-(

---

### Post by amsterdamharu on 2010-12-25
I bet you haven't tried chrooting into the system.

I've looked into the boot info script and here is how you can re-install grub and re-create the grub.cfg ([COLOR=Red]for people that found this post, don't copy these commands. This works for the op and his configuration. If you want help use the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") and post the output of that script first[/COLOR].)

Boot from a live CD and open a terminal (press alt + F2, type gnome-terminal and click run)
You can copy and paste multiple lines in the console, but the first time it will ask you for a password and ignores the rest of the lines so do it twice.

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
```Now post the output of the following command please.
```
ls -l /boot/grub/grub.cfg
```Then unmount and exit chroot

```
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/proc
umount /mnt/sys
exit
sudo umount /mnt
```Now reboot

---

### Post by kshaff03 on 2010-12-27
What's the point of chrooting into my system when I can boot into my system (using the grub command line)?

---

### Post by amsterdamharu on 2010-12-27
> What's the point of chrooting into my system

I don't know, maybe there is something screwy with your system that doesn't install grub correctly. As far as I can tell from the boot info script your grub.cfg is fine.

From what I can tell the grub.cfg is more or less the same as mine, only a different background image:
/usr/share/images/desktop-base/moreblue-orbit-grub.png
But I'm using mint so it takes a mint.png from boot.
Still if the image is missing or not supported would the if statement not just fail and use a different theme?

---

### Post by kshaff03 on 2010-12-27
Ok, I'll give it a shot. I'm on the road without a live CD, so I'll check this out in the next few days. Thanks for your suggestions.

--Kevin

---

### Post by drs305 on 2010-12-27
Using the "grub-install" command will refresh some files but won't replace deleted, renamed or some other Grub2 files. If you can boot into your system from the Grub prompt, you can purge and reinstall the Grub2 files without using 'chroot'. As *amsterdamharu* pointed out, sometimes even a G2 that looks ok fails.

I'd recommend you boot normally and then:
```
sudo apt-get update  # verify you have a good Internet connection.
sudo apt-get purge grub-common  # This will remove grub-common/grub-pc. Tab to OK when asked.
sudo apt-get install grub-pc # This will reinstall grub-common/grub-pc
# Select only the drive when asked for the installation location

```

This should return the Grub2 files to their original state and point the MBR entry to your Ubuntu partition (if you install to sda, sdb, etc - do not install to a partition).

At last thing the commands should do is run "update-grub". If not, run:
```
sudo update-grub
```

If you need to chroot, here is a guide which also includes background info on the commands:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

