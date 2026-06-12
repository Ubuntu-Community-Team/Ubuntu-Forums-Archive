---
title: "Removing Windows from GRUB2"
date: 2009-11-26
forum: General Help
---

### Post by nexoncore on 2009-11-26
**Problem**
The partition holding windows was deleted, but grub has not acknowledged this and has the partition listed. How would I go about removing a windows entry?

[B]Tried
[/B]Looked in all files relevant for making changes, could not find the entry listed in any. Attempted manual change of grub.cfg knowing its ill advised, but faced a read-only error anyway.

---

### Post by Mahngiel on 2009-11-26
Would be nice to know, after the new kernel update to -15, i still have the -14 kernel on Grub

---

### Post by sisco311 on 2009-11-26
Open a terminal and run:
```
sudo update-grub
```

[uhelp]community/Grub2[/uhelp]

---

### Post by nexoncore on 2009-11-26
Tried earlier and didnt work, gonna try again and restart. Will let you know.

Old GRUB was easier to work with though, allowed for more freedom with changes.

Is it possible to downgrade to GRUB legacy and still have ubuntu 9.10

---

### Post by nexoncore on 2009-11-26
Fail


Restarted after running the command, windows entry still there.

Clicked the entry to confirm that it did not exist

Got error "No Such Device"

---

### Post by Mahngiel on 2009-11-26
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

```

Ya, so it was found, how do i get rid of it?

---

### Post by nexoncore on 2009-11-26
It doesnt even find it on mine

---

### Post by sisco311 on 2009-11-26
> **nexoncore said:**
> It doesnt even find it on mine

How did you delete the windows partition? Did you reformat it?

---

### Post by sisco311 on 2009-11-26
> **Mahngiel said:**
> ```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

```

Ya, so it was found, how do i get rid of it?

You can remove the kernel via Synaptic. Kernels removed via Synaptic or with "apt-get remove" will automatically update grub.cfg and no user action is required.

[thread=1195275]Grub 2 Basics[/thread] (*7. Removing Entries from Grub 2*)

---

### Post by nexoncore on 2009-11-26
Deleted Partition in Gparted when working on organising the other hard drives. The space is free unallocated space now. Theres only 1 partition on the hard drive, ubuntu partition. Theres no windows installation or windows partition anywhere on this system.

---

### Post by sisco311 on 2009-11-26
> **nexoncore said:**
> Deleted Partition in Gparted when working on organising the other hard drives. The space is free unallocated space now. Theres only 1 partition on the hard drive, ubuntu partition. Theres no windows installation or windows partition anywhere on this system.

Try to (re)format the partition. The file system type doesn't matter. If you wish, delete the partition after formating it.

Deleting the partition does not remove the data,
maybe grub can still read the partition's boot record an detect it as Windows boot partition.

---

### Post by blueridgedog on 2009-11-26
> **nexoncore said:**
> Deleted Partition in Gparted when working on organising the other hard drives. The space is free unallocated space now. Theres only 1 partition on the hard drive, ubuntu partition. Theres no windows installation or windows partition anywhere on this system.

I believe it sees the windows boot loader in the mbr of the partition, regardless of the fact that you have formated the partition.  Delete it or wipe the mbr, then update grub.

---

### Post by Anonymousable on 2009-11-26
**PLEASE** make sure someone else has verified this before doing it:

```
sudo dd if=/dev/zero of=/dev/sda1
```This should completely blank the partition; It may take a while. AND DON'T GET IT WRONG or you'll be very VERY likely to regret it.

Anyway, if it works, then use update-grub again and see if it works :)

---

### Post by sisco311 on 2009-11-26
@Anonymousable, I wouldn't use that command, it overwrites /dev/sda1 with 0s. We don't even know if sda1 is the partition in question.

@OP: Try to reformat the partition first. If it doesn't work, post the output of:
```
sudo fdisk -l
```

And I will post a command which overwrites the Windows partition's boot record.

---

### Post by Anonymousable on 2009-11-26
> **Mahngiel said:**
> ```
Found Microsoft Windows XP Professional on /dev/sda1
done

```Ya, so it was found, how do i get rid of it?

> **sisco311 said:**
> @Anonymousable, I wouldn't use that command, it overwrites /dev/sda1 with 0s. We don't even know if sda1 is the partition in question.

Sorry... Didn't see that that quote earlier wasn't by the OP

And I know it overwrites sda1 with 0s :P

I guess it's the last thing to try, with the right partition of course.

---

### Post by sisco311 on 2009-11-26
> **Anonymousable said:**
> Sorry... Didn't see that that quote earlier wasn't by the OP

And I know it overwrites sda1 with 0s :P

I guess it's the last thing to try, with the right partition of course.

It should be enough to overwrite the PBR, the first 512 bites on the partition(bs=512 count=1)

EDIT:
@nexoncore

Was Windows automatically detected by grub? Did you edit any file in the /etc/grub.d/  directory?

What's the content of the /etc/grub.d/40_custom file?

---

### Post by nexoncore on 2009-11-26
/dev/sda2           12749       19457    53890042+   f  W95 Ext'd (LBA)
/dev/sda5   *       12749       19457    53890011   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a6b1a6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12111    97281576    7  HPFS/NTFS
/dev/sdb2           12749       19457    53890042+   7  HPFS/NTFS
/dev/sdb3           12112       12748     5116702+   7  HPFS/NTFS


sdb is a second HDD where I store my data, 3 partitions

sda is the OS Hard Drive, in sda5. For some reason on Gparted sda5 is shown to be inside the extended sda2. No other partitions exist.

EDIT: Also, I never added anything to grub, this is grub doing things by itself. 40_custom is blank apart from commentation

---

### Post by sisco311 on 2009-11-26
please post the content of the grub.cfg file:
```
sudo cat /boot/grub/grub.cfg
```

---

### Post by nexoncore on 2009-11-26
40_CUSTOM

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```


GRUB.CFG
```
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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
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
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=235dee43-087c-4d1f-8c69-de8bed1b4970 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=235dee43-087c-4d1f-8c69-de8bed1b4970 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 68ea447fea444c0e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

Windows is listed in grub.cfg even though I have tried the update-grub

---

### Post by sisco311 on 2009-11-26
> **nexoncore said:**
> 40_CUSTOM

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```


GRUB.CFG
```
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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
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
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=235dee43-087c-4d1f-8c69-de8bed1b4970 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 235dee43-087c-4d1f-8c69-de8bed1b4970
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=235dee43-087c-4d1f-8c69-de8bed1b4970 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 68ea447fea444c0e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

Windows is listed in grub.cfg even though I have tried the update-grub

Did you try to format /dev/sda1 (to ntfs/ext3/ext4) and run *sudo update-grub* again?

---

### Post by nexoncore on 2009-11-26
yes, the free space is now ext2

---

### Post by sisco311 on 2009-11-26
> **nexoncore said:**
> yes, the free space is now ext2

Try to reboot, then run "sudo update-grub". If Windows is still in the grub.cfg file, then post the output of:
```
sudo fdisk -l
```

---

### Post by Mahngiel on 2009-11-26
thx sisco

---

### Post by nexoncore on 2009-11-27
Same as before basically.

Might be because sda5 is in sda2, either way I have decided to backup using remastersys and do a complete formatting.

---

### Post by andytof47 on 2010-01-12
Hi Guys, I have a small problem with removing a HDD that isn't mine, I was just retrieving the files for a friend froma  live cd. I already had a partition ready to install Karmic on so I installed it, got the files...YAY everyone is happy... except me....

Because when I remove the HDD I get an error that says it can't find device such and such and leaves me at dropbox........ I want to disconnect the HDD and just be able to boot straight into Karmic.....

Any help please? I'd run an update grub but like i said I just get spat out at Dropbox or something like that ------ It's actually just a blank screen but if you tap a key then it comes up with the  dropbox gear

The system needs to go back tommorrow and I'm not re-installing my Karmic install just because of Micro$oft   pleeeeeeeeeeeeaaaassseeee help

cheers
```

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-17-generic root=/dev/sdb5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-17-generic root=/dev/sdb5 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro single 
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

[B]### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6aecec54ecec1bd7
	drivemap -s (hd0) ${root}
	chainloader +1[/B]
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by andytof47 on 2010-01-13
bump please, it's really urgent and I think putting something as half baked as grub2 into the official release and then not having support for it, really does nothing for Ubuntu or linux's rep in general.



Please can someone give me a workaround as I need to get rid of this crappy winBlow$ drive and keep my beloved Karmic, and i've spent way to long to just format it (although if there was a way to backup each and every setting kind of like ghost, I would be open to suggestions, just not an image, cause me grubby loader would likely look for the other drive)


Many thanks:popcorn:

---

### Post by andytof47 on 2010-01-15
cmon guys. Please.

I must ditch this HDD and frankly unless someone can spoonfeed me I don't know what to do about this dilema.

Should I post in a different section? i'm pretty sure someone out there can help.

cheers

---

### Post by blueridgedog on 2010-01-16
I suggest you disconnect the disk, then boot off of a live CD and recover Grub, per these instructions:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by andytof47 on 2010-02-03
cheers i'll give it a shot and let you know.....


my internet has been down only just checked it....


turns out I can keep the drive but I still want it off :)

---

### Post by andytof47 on 2010-02-04
didn't work.........

just says it can't find info for the device.........




might just have to find out how to make an image of my disk with rsync from a clean install and then just rsync it back to what it was.......



oh yeah & thanks for the reply, pitty it didn't work..... same story with my atheros cards......... I thought ubuntu was going to get better over time, not follow the Window$ release paths........ think about it....

---

