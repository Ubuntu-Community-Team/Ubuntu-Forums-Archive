---
title: "CDROM and USB Drives not detected after boot repair"
date: 2012-09-10
forum: General Help
---

### Post by landovers on 2012-09-10
Hi everyone, hope someone can help me...

I'm using a dual-boot setup and had to reinstall WinXP. As expected, this messed up GRUB (XP overrides it?), so I booted my Ubuntu Live CD, installed and ran boot-repair with the "recommended repair" option. I think it reinstalled GRUB for me, not sure. This fix worked immediately, but now Ubuntu doesn't detect my USB External HD, my CD-ROM drive or the Windows partition. I'm pretty new to Linux so I don't know how if there's a simple way around this :(

Any ideas? Thanks in advance...

---

### Post by landovers on 2012-09-11
Okay, so I managed to manually mount both my CD drive and USB external HD on /mnt/cdrom/ and /mnt/usbdrive/, respectively. At least I can see the contents now.

But how do I go back to having them show up when I click Places -> Computer? For example, right now I have to be root to do file operations with my HD, and Wine/PlayonLinux is not detecting my DVD for my Dragon Age Origins game installation anymore. I still need help...

I'm using 12.04 by the way.

---

### Post by dozdozez on 2012-09-11
If you can mount it is because linux is detecting it. So the problem must be in the configuration of your desktop environment (gnome, kde, xfce... )

Have you looked in your menus for  settings/preferences/controlcenter/whatever... --> removable drives options...?

There you can configure what has to be done when a removable media such as a cd-rom, pendrive, etc is detected.

---

### Post by landovers on 2012-09-11
Thanks for replying! Sorry for the confusion, I guess it detects the drives but doesn't automatically mount them like before. 

System Settings -> Details lets me choose what to do with removable media, but that doesn't help mounting it. I just found that through System Tools -> Preferences -> Disks I can see my removable medias, and when I click "Mount Media" it mounts on /run/media/my_user. 

When I mount it like that the media shows up on Places -> Computer like I wanted, but when I reboot it's not mounted again, I have to do this every time. So I guess my question now is how to auto-mount media upon booting...

---

### Post by YannBuntu on 2012-09-11
> **landovers said:**
> my question now is how to auto-mount media upon booting...

If your media is connected at Ubuntu startup, you can automount it via Disk-Manager: [https://launchpad.net/disk-manager/+download](https://launchpad.net/disk-manager/+download)

---

### Post by landovers on 2012-09-13
Thanks, I just managed to set both medias (USB HD and DVD) to mount at start-up. 

But now... upon boot after a little while it shows the purple Ubuntu screen with an error message "Error while mounting /run/media/my_user/my_media. Press S to Skip mounting and M for manual recovery [which just yelds a black screen and command line]". It does this twice, once for each drive.

It's weird because once it boots I have no problem to mount. I suppose it has to do with those mount options?

My FAT32 Samsung external HD has these mount options:
defaults,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks2

My TSSTCorp CD/DVDW has these:
nosuid,nodev,nofail,noauto,x-gvfs-show

I'll try and look at what these options mean, I guess. Any help would be appreciated, though :)

---

### Post by YannBuntu on 2012-09-13
Sorry I don't know which mount option you need.
You should ask this in a new thread.

---

