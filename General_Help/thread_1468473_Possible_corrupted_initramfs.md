---
title: "Possible corrupted initramfs"
date: 2010-05-01
forum: General Help
---

### Post by Powderhound01 on 2010-05-01
OK, I was an idiot. I was trying to follow this guide: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/) and having had a few issues, I started to play around with the settings. Having seen elsewhere that someone used just
> FRAMEBUFFER=y

instead of 
> echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash to get working, I attempted to use that method. However, now when I try to boot, I'm left stuck on a completely black screen. This occurs even if I use recovery mode or try an older kernel. I tried to fix it with a live CD, and while I could edit the text file, I was of course unable to run the actual update command. Does this mean my installation is now irretrievable and I need to do a reinstall? Thankfully I've got a separate home partition, but this is still obviously an inconvenience. Serves me right I guess. ;)

---

### Post by dino99 on 2010-05-01
sudo update-initramfs -u -k all

---

### Post by Powderhound01 on 2010-05-01
> **dino99 said:**
> sudo update-initramfs -u -k all

Where am I meant to type that into? I can only reach a terminal in the live CD, and when I tried that, albeit only with the -u appended, it said that it was impossible due to running on read only media (ie the CD).

---

### Post by dino99 on 2010-05-01
oh my bad, dont seen you cant boot, so you need to boot with live-cd and chroot into lucid partition, following this thread:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, you can type commands as you need

---

### Post by Powderhound01 on 2010-05-01
> **dino99 said:**
> oh my bad, dont seen you cant boot, so you need to boot with live-cd and chroot into lucid partition, following this thread:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, you can type commands as you need

I've tried following that, but I've never done anything remotely like a chroot before and am pretty confused. I'm in the live CD now, and if I go to disk utility, my linux install can be seen as:

213GB extended /dev/sda2
-->8.2GB swap /dev/sda5
-->16GB filesystem /dev/sda6
-->188GB filesystem /dev/sda7 (This is the home partition)

As such, what do I do from here?

---

### Post by Powderhound01 on 2010-05-01
I've tried this:
> ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /mnt/sda6
root@ubuntu:/home/ubuntu# mount /dev/sda6 /mnt/sda6
root@ubuntu:/home/ubuntu# chroot /mnt/sda6
root@ubuntu:/# sudo update-initramfs -u -k all
sudo: unable to resolve host ubuntu
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
grep: /proc/modules: No such file or directory


---

