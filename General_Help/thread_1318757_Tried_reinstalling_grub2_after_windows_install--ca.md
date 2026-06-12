---
title: "Tried reinstalling grub2 after windows install--cannot boot anymore"
date: 2009-11-07
forum: General Help
---

### Post by Seishuku on 2009-11-07
I spent all of yesterday installing Karmic and customizing it.  I spent all of today installing Windows 7 and customizing it.  I know I installed them the wrong way around, but I thought it would just be a matter of reinstalling grub afterwards.

I tried to use one of the guides here on the forums, but ran into some problems:

-The first time around, I mounted the NTFS partition (sda2), but ignored the devices part or any other sections, since my file system is all lumped up together.  I tried to do the chroot part, but it wouldn't let me.  I figured I'd go ahead with the install.  I forgot to read the entire thing through, and attempted to install directly into sda2 when I was only supposed to use sda--the command prompt told me it was a bad idea, etc. but still went through with the install.  So I reread and I do it again with sda.  It tells me it has no errors.  I check again.  no errors.

-I boot up, but I get this weird command prompt that says sh:grub>, and I can't boot into anywhere, or figure out how to do anything.

-I try reinstalling grub2 again, following closer attention to the instructions.  It doesn't let me mount devices or do chroot.  I try to reinstall grub2 the same way I did before, but this time it won't let me.

-I restart my computer.  I get the same screen.  I type boot and it says there's no bootable partition.  I hit escape, and I get the same horrible process screen I got when my hard drive died--no bootable media.  I checked through a live usb and my partitions are all right, though.

Right now I'm posting this from a live usb--I'd really like to get grub2 or at least legacy grub working again.

---

### Post by confused57 on 2009-11-07
Here's a method to install grub2 without having to chroot:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by Seishuku on 2009-11-07
These are the errors I get in the terminal:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev/ /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
```

---

### Post by Seishuku on 2009-11-07
> **confused57 said:**
> Here's a method to install grub2 without having to chroot:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")

That didn't work...this is what happened:

```
ubuntu@ubuntu:~$ ls /media
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub /dev/sda
grub-setup: error: Cannot open `/boot/grub/device.map'
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda
grub-setup: error: Cannot open `/media/disk/boot/grub/device.map'
ubuntu@ubuntu:~$ sudo grub-setup -b /media/disc/boot/grub/boot.img -c /media/disc/boot/grub/core.img -m /media/disk/device.map /dev/sda 
grub-setup: error: Cannot open `/media/disk/device.map'
ubuntu@ubuntu:~$ 
```

---

### Post by Seishuku on 2009-11-07
Ahahaha! :lol: 

After reading another guide, I realized that my mistake was mounting the Windows partition and not the Linux partition.  I mounted the Linux partition and everything worked like a charm.

However, in my desperation, I had attempted to reinstall Windows 7, which I couldn't because the installer hung on 0%.  Because of this, my existing installation became corrupted.

I'm back to square one, with an Ububtu I can boot into but no Windows.

Well...at least I know how to get grub2 back once I finish reinstalling Windows 7.

---

### Post by earfer on 2009-12-04
sorry but may i know which guide you read?

---

### Post by kocoman on 2010-03-11
bump, what other guide??

---

### Post by Method X on 2010-03-11
> **kocoman said:**
> bump, what other guide??

Try my guide

[http://ubuntuforums.org/showpost.php?p=8931531&postcount=4]("http://ubuntuforums.org/showpost.php?p=8931531&postcount=4")

---

