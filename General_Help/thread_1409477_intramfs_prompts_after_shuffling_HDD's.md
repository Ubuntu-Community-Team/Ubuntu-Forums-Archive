---
title: "intramfs prompts after shuffling HDD's"
date: 2010-02-17
forum: General Help
---

### Post by SiHa on 2010-02-17
Wonder if someone out there can help me.

First, a small back-story. I upgraded my Mythbox to 9.10 last year, and as a backup path, I left the original HDD (sda) intact, and chucked a spare drive (sdc) in for the install. I just changed the boot order in the BIOS to boot from the spare drive, and all my data (/var/lib/mythtv/) is on a separate drive (sdb). The original drive is redundant, I just didn't get round to pulling it.

Now, I got a new 1TB drive today, transferred all my data onto it and swapped it for the old data drive, and at the same time pulled the unused old install drive. So I just have the new 9.10 (spare) install drive, and the new drive.

I changed my fstab with the correct UUID's of the drives, but at boot, I get 'gave up waiting for root filesystem on sdc1' and the intramfs prompt. Listing the drives by UUID, I have sda(1&2) and sdb(1&2).

I can get the system bootable again by putting the unused old install drive back, so that I have an sdc, but this is far from ideal, as I have a drive spinning away nearly 24/7 that is not needed.

Now, I thought that using UUID's got away from the whole sda/sdb/hda ... business, but it seems that the kernel is still looking for sdc1 to boot off.

FWIW, my fstab: The old and new data drives, and the boot drive are there, the redundant drive doesn't have an entry. ```
mythbox@mythbox-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# sdc1 / was on /dev/sda1 during installation
UUID=4a5599f5-d409-42b5-a74f-0c689f15d73d /               ext4    errors=remount-ro 0       1
# sdc5 swap was on /dev/sda5 during installation
UUID=46107d9b-d161-4a3f-9890-b9db0bdcc924 none            swap    sw              0       0

#/dev/sdb Samsung500GB - old, removed from system, entry kept in case.
#/dev/sdb1 
#UUID=13dc6de8-4255-432d-80ad-ebcf048aeaac /var/lib/mythtv            ext3     relatime,errors=remount-ro 0       1
#/dev/sdb2
#UUID=f8ec4154-05f2-4183-a9ca-bf71f630360c /backup                    ext3     relatime,errors=remount-ro 0       1

#/dev/sda Samsung 1TB
#/dev/sda2
UUID=f233907c-7bf6-4bd6-b62b-7fc55db1a436 /var/lib/mythtv            ext3     relatime,errors=remount-ro 0       1
#/dev/sda1
UUID=1165dfe5-8191-474a-830e-4035d517a45a /backup                    ext3     relatime,errors=remount-ro 0       1

```

Can anyone tell me how I can stop the system looking for sdc1?

Edit:
Just looked at /boot/grub/grub.cfg:```
.
snip
.
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash hpet=disable
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-
14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
.
snip
.
```

So I guess I need to point grub to the correct location. Now I know I'm not supposed to edit grub.cfg, but I can't see how I can successfully boot the system in a state where running update-grub will pull the correct drive in. My thinking is that what I need to do is edit the```
linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash hpet=disable
```line to read ```
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4a5599f5-d409-42b5-a74f-0c689f15d73d ro   quiet splash hpet=disable
```

Shutdown, pull the redundant drive, boot (hopefully anyway), then run update-grub.

Does that sound OK? Sorry for the war-and-peace!

TIA,

Simon

---

### Post by jamesisin on 2010-02-17
You are on the right path.  Grub *now* uses UUID instead of /dev designations.  But if you are using an old version of grub (pre-upgrade) then your grub is likely using the old method.

I don't know if there is a better solution, but perhaps reinstalling grub is a way to get there (installing the newer version that is).

---

### Post by SiHa on 2010-02-17
Thanks. 

This is where I'm confused. This is GRUB2, on a vanilla Karmic install (**not** an upgrade. The Hardy install disk was physically disconnected when I did the new install. 
The entries further down the list (from the old install that was detected when I ran update-grub for something else, after reconnecting the drive.) use UUID's it's only the sdc ones that don't.

So as I have GRUB2, would my suggestion work?
Sorry, it's just that I'm loathe to do something that might really screw grub, and upset the wife when she can't watch 'Desperate Housewives'!
Cheers,
Simon```
mythbox@mythbox-desktop:/$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash hpet=disable
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 87b46261-ed4e-4121-aaca-8b42fc42a7c7
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=87b46261-ed4e-4121-aaca-8b42fc42a7c7 ro quiet nosplash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 87b46261-ed4e-4121-aaca-8b42fc42a7c7
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=87b46261-ed4e-4121-aaca-8b42fc42a7c7 ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.04.1, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 87b46261-ed4e-4121-aaca-8b42fc42a7c7
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by ajgreeny on 2010-02-17
In your fstab file the sdc1 line is not commented out, or rather the line beneath the sdc1 line which is the line that matters in the file is not commented out.    Therefore fstab is still telling the system to look for that partition.  I accept that fstab also talks about sdc1 being sda1 at install time, but I think it worth trying my suggestion; just make sure you keep a backup first.

Your file is:-
```
# sdc1 / was on /dev/sda1 during installation
UUID=4a5599f5-d409-42b5-a74f-0c689f15d73d /               ext4    errors=remount-ro 0 
```but should be:-
```
# sdc1 / was on /dev/sda1 during installation
#UUID=4a5599f5-d409-42b5-a74f-0c689f15d73d /               ext4    errors=remount-ro 0 

```

It is always confusing when you remove a disk that was present before installing an OS like ubuntu that normally finds all other OSs in the machine.  When you put the old disk back in the disk nomenclature may be completely messed up, I think.  UUIDs should overcome this, but perhaps not always successfully.

---

### Post by dcstar on 2010-02-17
```
sudo update-initramfs -u -k all
```

---

### Post by SiHa on 2010-02-18
@ajgreeny. Thanks, but the UUID's in my fstab are correct, it's just that that partition is no longer sdc1. The problem is getting GRUB to look in the right place.

@dcstar. Thanks, but without any explanation, I'm unclear how this will update GRUB to point to the correct partition. I checked the manpages for update-initramfs, and am no wiser. I like to know why I'm running commands, and how the end-result is achieved.

Anyway, the short version is that I tried my solution:
Edit first entry in grub.cfg (after first backing-up) to point to the correct UUID (that was sdc1).
Shutdown, remove redundant drive.
Restart.
```
sudo update-grub
```
All is now good, grub is updated, the redundant entries have been removed, and the machine boots normally.

Thanks all for your advice.

---

### Post by jamesisin on 2010-02-18
I'm not yet a grub expert, but I tend to read a lot of these threads because I'm trying to get better with it.

It seems I have read on other threads something like "don't edit grub.cfg directly but edit this other file instead (which then causes a change in grub.cfg)".  Do I have this right?

---

### Post by SiHa on 2010-02-18
> **jamesisin said:**
> I'm not yet a grub expert, but I tend to read a lot of these threads because I'm trying to get better with it.

It seems I have read on other threads something like "don't edit grub.cfg directly but edit this other file instead (which then causes a change in grub.cfg)".  Do I have this right?

Absolutely. And the Wiki also says this. I believe the main reason for this is that whenever grub is updated, grub.cfg will be overwritten. The file you are supposed to edit is /etc/default/grub. 

But this file doesn't contain the information that is required to change where grub looks for the root partition at boot. Running update-grub will run some scripts, which look for OS'es to add to the grub menu, and incorporate any changes you've added to the above.

I was in a kind of catch-22 situation, where in order to boot, I had to have an sdc1 partition (which changed to sdb1, when I removed the spare drive), and if I did, then update-grub wouldn't change anything, because the root partition was still where it thought. I needed to be able to boot, just once, with grub looking at the correct partition (sdb1). Then I could run update-grub, and let it sort itself out.

As far as I can see, the way I did it was the only way.

Cheers,

Simon

---

### Post by jamesisin on 2010-02-18
Thanks for that thorough explanation.  I wonder why updating grub from the Live CD didn't produce the desired fix.

---

### Post by dcstar on 2010-02-18
> **SiHa said:**
> @ajgreeny. Thanks, but the UUID's in my fstab are correct, it's just that that partition is no longer sdc1. The problem is getting GRUB to look in the right place.

@dcstar. Thanks, but without any explanation, I'm unclear how this will update GRUB to point to the correct partition. I checked the manpages for update-initramfs, and am no wiser. I like to know why I'm running commands, and how the end-result is achieved.

Anyway, the short version is that I tried my solution:
Edit first entry in grub.cfg (after first backing-up) to point to the correct UUID (that was sdc1).
Shutdown, remove redundant drive.
Restart.
```
sudo update-grub
```
All is now good, grub is updated, the redundant entries have been removed, and the machine boots normally.

Thanks all for your advice.

AFAIK the initramfs update is also part of the update-grub, it is also run whenever a new kernal is installed/uninstalled.

If you stuff around with these things you have to let the system basically realign itself so it will work properly - as you have now found out.

---

### Post by SiHa on 2010-02-19
> **dcstar said:**
> 
If you stuff around with these things you have to let the system basically realign itself so it will work properly - as you have now found out.

Indeed I have. I was just surprised that UUID's weren't being used for the root partition, as this would have ensured that there was no buggering around required, it would have 'Just Worked™'

Anyway, problem sorted, moving on...

---

