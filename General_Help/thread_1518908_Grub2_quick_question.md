---
title: "Grub2 quick question"
date: 2010-06-27
forum: General Help
---

### Post by randiroo76073 on 2010-06-27
Just migrated to grub2 w/10.04. Have read alot about it, but haven't gleaned this: If you multi-boot do you install grub2 to each distro partition, or just the main one and use update-grub from there ?

---

### Post by oldfred on 2010-06-27
Grub2 does not like to be installed to a partition. It will complain about blocklists being unreliable. If any files it uses for booting get moved on the harddrive your boot will break. If it is old grub with another distro you can install it and still chainboot but then you have to do customization of your menu.

With grub2 the osprober is very good at finding other systems and letting you directly boot them. If you have a lot of systems the menu can get large and need customization. With each install you have to decide which system is incharge and is the primary one you want to boot and keep that one in the MBR to boot first. All the others if possible choose not to install grub and then update-grub from the primary to find the new install.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by randiroo76073 on 2010-06-27
Thanks oldfred, kinda what I thought, but wasn't sure,

---

### Post by randiroo76073 on 2010-08-19
Update: You can install grub2 to partitions, so they must have fixed it. My present setup is:
sda1 = Zorin 10.04 (default) kernel 2.6.35.15
sda2 = Lubuntu 10.04            "       "
sda3 = Pinguy 10.04             "       "
sda4 = Ubuntu netbook 10.04     "       "
sda5 = Maverick 10.10 b3     kernel 2.6.35.16
sda6 = Fedora 13
sda7 = Suse 11.3

All have bootloaders installed to respective partitions, all stable & running great. All are using shared /home partition(250gb) with *distro name as /user folder. Makes it easy to keep synced, all share common folders: Documents, Music, Videos, Pictures, Public, Downloads, Wallpapers.

All boot times are less than 45 seconds to desktop from boot menu, default(Zorin) is 37 seconds from cold boot

---

