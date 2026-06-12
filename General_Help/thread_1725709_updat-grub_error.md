---
title: "updat-grub error"
date: 2011-04-10
forum: General Help
---

### Post by fisch246 on 2011-04-10
when I run "sudo update-grub" i get this:


paul@l4p-tp:~$ sudo update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos1,msdos1).
Found memtest86+ image: /boot/memtest86+.bin
done

I ran fdisk and everything was fine. I realize it did find everything it was suppose to... it's just this is really annoying... this happened as soon as I installed Fedora on another partition. I then moved onto removing it due to many problems. Either way it only started doing this as soon as i installed. I had booted into Ubuntu and ran update-grub in order to get fedora on the list, and has shown this errors since then. Any ideas?

---

### Post by Hedgehog1 on 2011-04-10
If you would do the following, we might get enough info to figure this one out:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by fisch246 on 2011-04-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         620,951,552   625,141,759     4,190,208  82 Linux swap / Solaris
/dev/sda4    *             63   620,951,551   620,951,489  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d7c96749-9aa2-4337-895b-28fde006971f   swap                                     
/dev/sda4        8dddd119-260b-438d-9337-c1bdb5202292   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=8dddd119-260b-438d-9337-c1bdb5202292 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=8dddd119-260b-438d-9337-c1bdb5202292 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 8dddd119-260b-438d-9337-c1bdb5202292
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=8dddd119-260b-438d-9337-c1bdb5202292 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eacbf10c-2e8e-4cac-aa8d-141f7386b80b none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
 147.8GB: boot/grub/grub.cfg
 163.2GB: boot/initrd.img-2.6.35-28-generic-pae
   5.5GB: boot/vmlinuz-2.6.35-28-generic-pae
 163.2GB: initrd.img
   5.5GB: vmlinuz
```

---

### Post by fisch246 on 2011-04-10
anyone have any ideas?

---

### Post by fisch246 on 2011-04-10
I hope I don't have to reformat my drive do get rid of this error >.<

---

### Post by drs305 on 2011-04-10
**ADDED: I just read Quackers simultaneous post. The fstab entry is very likely the problem. Change the fstab entry and reboot, then run update-grub. If that doesn't work, try what follows in this post.  Good eye Quackers.**

I believe this is an issue with the condition of your swap partition. If you delete it and create a new one the problem may go away.

Open Gparted (System, Administration, Gparted).
Highlight the swap partition (sda1).
Right click, swapoff.
Delete the swap partition. If it says you have to unmount sda4, you can't from a running system. Boot a LiveCD and run this entire procedure from the LiveCD.
Create a new swap partition using the same space.
Open a terminal and run this command to give the swap partition the same UUID as the old one:
```

sudo tune2fs -U d7c96749-9aa2-4337-895b-28fde006971f /dev/sda1
sudo swapon -a
sudo blkid -c /dev/null # Check current UUID of swap partition (/dev/sda1)

```
**Added: Make sure the fstab entry for swap matches the UUID from above.**


Try running update-grub again and see if it now works.

---

### Post by Quackers on 2011-04-10
Have you done some partitioning latey?
I don't know why the error is showing, but I can see a problem.
According to the output above your swap partition is on sda1, which has a UUID of d7c96749-9aa2-4337-895b-28fde006971f
However, according to /etc/fstab your swap partition is on sda5 with a UUID eacbf10c-2e8e-4cac-aa8d-141f7386b80b
Does the sytem boot ok?

EDIT
See above post by drs305 :-)

---

### Post by fisch246 on 2011-04-10
This is what I got when I typed that into console after deleting, and formating swap...
```
paul@l4p-tp:~$ sudo tune2fs -U d7c96749-9aa2-4337-895b-28fde006971f /dev/sda1
tune2fs 1.41.12 (17-May-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```

and yes the swap is in sda1 as according to gparted...

---

### Post by fisch246 on 2011-04-10
o sorry just saw the post about editing fstab, hold on...

---

### Post by fisch246 on 2011-04-10
i edited my fstab to say this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=8dddd119-260b-438d-9337-c1bdb5202292 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=d7c96749-9aa2-4337-895b-28fde006971f none            swap    sw              0       0
```

then ran your commands... still got the same error... couldn't find it... was i not suppose to edit fstab?

---

### Post by fisch246 on 2011-04-10
i ran the script again and i noticed i had a new UUID because I formated swap... so I replaced the new UUID for the one in the command... and it still didn't work :/ I used the UUID that was in /dev/null

---

### Post by Quackers on 2011-04-10
I'm not sure if it's required or not, but are you running sudo update-grub in a terminal afterwards?

---

### Post by drs305 on 2011-04-10
I'll assume the error you are still getting is not the Grub error but the swap message.

If you have deleted your swap partition your system will run without it and we can recreate it later. Have you tried running the 'update-grub' command since you removed the swap partition?

First, go into fstab and place a # symbol at the start of the swap line and save the file. This will disable the entry. Then run the update command and see if the Grub update now runs without error.

---

### Post by fisch246 on 2011-04-10
yea i just ran update-grub after removing swap and commenting out the swap line, and it worked fine... >.<

---

### Post by fisch246 on 2011-04-10
mind walking me through getting it working, after formating swap space?

---

### Post by drs305 on 2011-04-10
:-)

Now we need to recreate the new swap partition. 
Make a new partition with gparted. The file type would be 'linux-swap'.

Then in a terminal run:
```
sudo blkid -c /dev/null | grep swap
```
The above command should return the UUID of the new swap partition.


```
gksu gedit /etc/fstab /etc/initramfs-tools/conf.d/resume # Place the new UUID here.
```
Since I don't know where we stand with the UUID in fstab, we'll use the new UUID. Use the UUID for swap from the earlier command, and place it in the fstab swap entry (and remove the # at the start of the line if it's there). You'll also have to put the new UUID in the other file opened by the command.


Then run this command to see if the fstab entry works. If it is correct, you will get no messages:
```
sudo swapon -a  # Tests fstab swap entry and turns on swap
sudo update-initramfs -u  # Updates initrd.img w/ new UUID

```

Your new swap should work. After rebooting, you can run this command to see if it's working. It may show 0 used, but it shouldn't be *all* zeros in the second line:
```
free -m
```

---

### Post by fisch246 on 2011-04-10
everything worked, however when I ran "sudo update-grub" it still produced that same error from the first post. any other ideas?

---

### Post by drs305 on 2011-04-10
So before you recreated the swap the update-grub produced no errors but now that you have recreated it you are back to your first post?

It could be that having swap on sda1 and/or Ubuntu on sda4 is something os-prober can't handle. One of the Grub2 developers said that the message is informative only and doesn't affect the operation of Grub or the OS. (However, he also said he'd remove the message, and this was back in December so you may have an older version of Grub2).

Here are some options:
1. Create a custom menu and disable OS prober. You can create a custom menu that still provides the most recent kernel. If you don't add/remove OS's very often, this is a viable solution.

2. Update Grub2 to Grub 1.99 and see if the problem persists.

3. As the message, according to the Grub2 folks, is an advisory, just learn to live with it.

4. Wait for someone to find this thread and figure out a fix.

5. Go to the #grub IRC channel and ask the devs directly. They may have a quick solution if you can get them to respond to your query.

---

### Post by fisch246 on 2011-04-10
can you tell me how to update grub? cause i believe i'm running 1.97... if that doesn't work I can move swap into a logical partition and make it sda5... which is what it used to be i believe

---

### Post by fisch246 on 2011-04-10
correction i have grub 1.98, and i looked at synaptic and all they had was 1.98, so maybe i'll just move it into an extended partition... feel free to still let me know how to upgrade grub... but if it works i'll mark it as solved :)

---

### Post by drs305 on 2011-04-10
> **fisch246 said:**
> can you tell me how to update grub? cause i believe i'm running 1.97... if that doesn't work I can move swap into a logical partition and make it sda5... which is what it used to be i believe

I'd recommend the second option. Grub 1.99 is at Release Candidate status, and won't be used in releases prior to Natty. So you would be using a version not 'officially' approved for earlier releases.

If you want to upgrade to Grub 1.99 you can alter your /etc/apt/sources.list by changing *maverick* to *natty*. You only need to change the "main" entry. This is what mine looks like:
> 
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) **natty main** restricted
Reload Synaptic or Software Sources or run "sudo apt-get update".

Then upgrade **only** grub-common and grub-pc. Accept the package maintainers version. 
```

sudo apt-get update
sudo apt-get install grub-common grub-pc
```

After you upgrade these two packages, change the name in sources.list back to maverick. You won't get further updates unless you repeat the procedure but you will have the current version of 1.99.

---

