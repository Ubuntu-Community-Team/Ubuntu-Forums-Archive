---
title: "Boot hangs at logon sound - no video signal - appears drive is still working"
date: 2011-02-12
forum: General Help
---

### Post by Danial on 2011-02-12
Hi,

Thanks in advance for your time.
I am using Ubuntu for a bit of time and still learning (credit goes to this community). As of now Ubuntu/Edbuntu is the OS of my choice (though still have to go to Windows for few application - to name: Silverlight). Anyway that is not my gripe or recent problem
My problem started last night when Ubuntu refused to start. I get to the OS selection menu, I choose the current built. I am on autologon (I know some of seasoned guru will not like this - but pardon me, please).  I hear the logon sound and that is the end of the story. My monitor goes blank after the 'no video signal' prompt.  HD is still on and once a while I hear it is running.  My rig has a temp. display and that shows a slow rise of core temp. (just above the normal and stays there). My only exit at this point is to hit the reset button.  To my little understanding, grub menu is working (I may be wrong) because I am able to choose another OS (Win7) and log on to that properly.  I tried to go into the recovery mode of Ubuntu and also older versions to same results. I tried to use  Maverick's live CD (same one I used to install the Maverick) and that stops with a garbled video on top of the screen.  However, I was able to get into live session with Lucid. Okay, I can take that my cd got damaged but now where I go. I tried Super Grub CD and that reports (thru support menu) that error 15 file not found: /etc/fstab and promptly hangs up on checking menu items.  In live session, I was able to see the fstab, I am not sure about the menu.

**So is there any hope for me or I have to go re-installing the OS?**

Any advise, help, most importantly your time is very appreciated in advance.

Danial

---

### Post by Danial on 2011-02-12
**Hmmm no response !!!  That is strange. **

Do I need to rephrase this problem or just bump it down to the south street?

Thanks,

Danial

---

### Post by davidmohammed on 2011-02-12
What is your graphics card?

Are you using any proprietary graphics drivers?  If you are - what is it and how have you installed it?

Have you tried booting with

nomodeset

or maybe

nomodeset xforcevesa

?

---

### Post by quadproc on 2011-02-12
> **Danial said:**
> 
My problem started last night when Ubuntu refused to start. I get to the OS selection menu, I choose the current built. I am on autologon (I know some of seasoned guru will not like this - but pardon me, please).  I hear the logon sound and that is the end of the story. My monitor goes blank after the 'no video signal' prompt.
Which version of Ubuntu are you trying to run?  Did that version work OK previously? Have you changed any hardware just recently?  Did you do a software update just before the problem?  Do you have an xorg.conf file?

If you can give us more information then we can try to figure out what is happening.

quadproc

---

### Post by Danial on 2011-02-12
> **davidmohammed said:**
> What is your graphics card?

Are you using any proprietary graphics drivers?  If you are - what is it and how have you installed it?

Have you tried booting with

nomodeset

or maybe

nomodeset xforcevesa

?
> 
Which version of Ubuntu are you trying to run? Did that version work OK previously? Have you changed any hardware just recently? Did you do a software update just before the problem? Do you have an xorg.conf file?

If you can give us more information then we can try to figure out what is happening.

quadproc



HI,

Sorry, I did not get back with you guys earlier. 

**NO**, I did not try to boot with those options.  I will do it soon after this post. 

**Yes**, I am using proprietary driver nvidia graphics g6150 (I believe). It was installed right after OS (Maverick) installation back in October when system  prompts me for available 3rd party drivers.  Later sometime in December, I started using xbuntu desktop.  Until last night, I did not have any problem except that once in a while firefox/chrome crashes probably due to flash contents. 

**NO** there is no recent changes of any kind in hardware arena as well no new software or application installation except for the software update which was couple of days ago and system was working fine after that.  I generally use default options and update everything offered in software update message.  I am not sure if there is xorg.conf file but I will check and report back.  

I will try to boot with above mentioned options and if that is not successful, I will boot with live cd and look for the xorg.conf as well.  I will be posting back in few.
  
Thanks a bunch for your help.

Danial

---

### Post by Danial on 2011-02-12
Here is my little finding:

I was unable to boot with option nomodeset >> no kernel found.  I guess, I have to enter whole string linux /boot/vmlinuz-2.6... and then add the option of nomodeset.

Following are the contents from (copy/paste from files) of xorg.conf, fstab and grub.cfg.


/etc/x11/xorg.conf


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

====================
/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=84781de9-0f61-474c-a56e-d6f455826462 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=d898c458-3a28-4abf-9a28-c34d356c0046 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

==============

/boot/grub/grub.cfg

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=84781de9-0f61-474c-a56e-d6f455826462 ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84781de9-0f61-474c-a56e-d6f455826462
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 66b8b439b8b40a17
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

I am not sure what else I need to put in here at this time.  I depend on words from you guys.

Thanks,

Danial

---

### Post by quadproc on 2011-02-12
> **Danial said:**
> Here is my little finding:

I was unable to boot with option nomodeset >> no kernel found.  I guess, I have to enter whole string linux /boot/vmlinuz-2.6... and then add the option of nomodeset.

More or less, yes - I think that you eliminated the name of the kernel while putting in the nomodeset.  The usual suggestion is to get to the point where grub offers the OS choices, then choose the one you want, edit that one by removing the "quiet splash" text, and replacing that text with nomodeset.
> 
/etc/x11/xorg.conf
 That looks like a good and minimal xorg.conf file.
> 
/etc/fstab
Hmm.  You have two swap partitions showing.  I don't know what the system will make of that.  Also, your floppy should probably be set up for a passno of 2 (that is the last numeric value in the entry).

I am perplexed because some of the reported symptoms suggest hardware problems while other symptoms suggest software but I did not see anything in the files that should affect the graphics.  Perhaps other readers can spot something.  The first thing that I would do is to fix up the swap entry.

One other note - when you have something lengthy in a post, please mark it as code by using the # just above the edit window when you have highlighted the lengthy portion.  That will put the selected material into a scrolling window and that makes it easier to read.  Thanks.

quadproc

---

### Post by Danial on 2011-02-13
> **quadproc said:**
> More or less, yes - I think that you eliminated the name of the kernel while putting in the nomodeset.  The usual suggestion is to get to the point where grub offers the OS choices, then choose the one you want, edit that one by removing the "quiet splash" text, and replacing that text with nomodeset.

Yes, I did miss that on my initial try.  Thanks for pointing it out. But when I did it right, I still got the same result of being hang, no inout signal to the monitor and that is it.
 
> You have two swap partitions showing.  I don't know what the system will make of that.  Also, your floppy should probably be set up for a passno of 2 (that is the last numeric value in the entry).

Idea about two swap was from an earlier discussion regarding partitions and setting up /home on a separate partition; according to that if there are two physical drives, it is okay to have swap on both drives. For simplicity sake, I will take it off from sdb (that is the drive with win7). About floppy drive, I had no idea and I will correct it as you advised.

> I am perplexed because some of the reported symptoms suggest hardware problems while other symptoms suggest software but I did not see anything in the files that should affect the graphics.  Perhaps other readers can spot something.  The first thing that I would do is to fix up the swap entry. 

At this point, I am more inclined to say that at some point in time, hardware caused file corruption.  Because it all started when Win7 crashed on me (more than couple of times in a short period). I never thought that may be affecting this side of the OS world.  Last night I ran memtest and let it run over 8 hours and no errors reported in 10 passes. Interestingly, for first 30 minutes temp. went up quite a bit up to 40C and then dropped to 37C which is still high.  In past I never saw it that high even when pc is in full load. Another thing to that account (with my little knowledge), when I am running memtest, it should not be putting extensive load on cpu and should not cause temp to go up. 

So, apparently mem. sticks are good as well cpu (hopefully).  I will open the box and do some cleaning, reseat the memory and see if that resolve the heating problem.  Once that is settle, I will dig back into software side. I may have to resort to re-install because above files do not show any corruption and I sure don't know what other files may affect (unless some reader point it to me).


> One other note - when you have something lengthy in a post, please mark it as code by using the # just above the edit window when you have highlighted the lengthy portion.  That will put the selected material into a scrolling window and that makes it easier to read.  Thanks.

quadproc

I do apologize and also thank you for pointing it out. I did not know this tip, but now I will be more careful in future.

[B]Once again thanks a lot for your guidance and time.
[/B]
Danial

---

### Post by quadproc on 2011-02-13
> **Danial said:**
> 
Idea about two swap was from an earlier discussion regarding partitions and setting up /home on a separate partition; according to that if there are two physical drives, it is okay to have swap on both drives. For simplicity sake, I will take it off from sdb (that is the drive with win7). 

OK, but let me be a little more verbose: having more than one swap partition is OK, perhaps a bit wasteful of disk space but should not cause any operational difficulty.  The thing that concerns me is that both swap partitions were listed in fstab.  I suspect that the system will use the last one mentioned but I am guessing.  It is probably better to remove one of the swap entries from fstab.

> 
At this point, I am more inclined to say that at some point in time, hardware caused file corruption.  Because it all started when Win7 crashed on me (more than couple of times in a short period). I never thought that may be affecting this side of the OS world.
You certainly should not need to worry about some other OS straying out of its own territory and damaging something else, but I have seen Windows "fix" a perfectly good Ubuntu install which i then had to repair.  A crashing program might do several unexpected things in one crash.
> 
Another thing to that account (with my little knowledge), when I am running memtest, it should not be putting extensive load on cpu and should not cause temp to go up. 
 I have not looked at the memtest code but I would expect it to make the CPU fully busy and therefore the temperature rise should be greatest.  The reason for the busyness is that you want the memtest to be as stressful as possible, and you want it to finish as soon as possible.

> . I may have to resort to re-install because above files do not show any corruption and I sure don't know what other files may affect (unless some reader point it to me).
Since you mentioned a crash, it might be wise to do as much file checking as possible.  If your system hasn't recently done a fsck then it might be useful to do that.

quadpproc

---

### Post by Danial on 2011-02-14
About the swap entry, I understand your explanation and I will follow up on that. 

> I have seen Windows "fix" a perfectly good Ubuntu install which i then had to repair. A crashing program might do several unexpected things in one crash.
Well, given the fact that no other abnormal event happened, this may be our best guess.  

> Since you mentioned a crash, it might be wise to do as much file checking as possible. If your system hasn't recently done a fsck then it might be useful to do that.
I did run a fsck from live cd, at first it reported that system time is set in future (something in that regard) and it fixed  that.  Following fsck did not return any problem on either sda2, sda3 or sdb2. 

> I have not looked at the memtest code but I would expect it to make the CPU fully busy and therefore the temperature rise should be greatest. The reason for the busyness is that you want the memtest to be as stressful as possible, and you want it to finish as soon as possible. 
That is perfect explanation which I did not think earlier.  Thanks for explaining it.

I am downloading Maverick again and will burn it to a new CD and see if symptoms persist (as I mentioned earlier that even live CD of Maverick is acting up - which I had given doubtful benefit of bad CD). I will post again with results.

**I really appreciate your time and help in this regard.** 

Danial

p.s.: I have another question which in fact is not related to this thread but I am throwing it in.  If at some point you can spare sometime can you look back at my current fstab.  Back in December, I tried to move /home to its own partition.  But now when I checked all the partitions, I do see home partition but nothing in it.  To my little knowledge, fstab is showing only one partition mounting at startup.  Is this correct?  Do I need to mount /home within fstab and what would be the options? **Once again, please only respond to this when you have extra time.** If you  prefer, I can start another thread once system is back up and running.  But you need the output of fdisk.
```

ubuntu@ubuntu:~$ sudo fdisk -l && df -h

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd3c5204

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         630     5060443+  82  Linux swap / Solaris
/dev/sda2   *         631        6391    46275232+  83  Linux
/dev/sda3            6392       11220    38788942+  83  Linux
/dev/sda4           11221       60801   398259352    5  Extended
/dev/sda5           11221       17785    52733331   83  Linux
/dev/sda6           17786       27656    79288776   83  Linux
/dev/sda7           27657       37527    79288776   83  Linux
/dev/sda8           37528       40799    26282308+  83  Linux
/dev/sda9           40800       44071    26282308+  83  Linux
/dev/sda10          50637       55718    40821133+  83  Linux
/dev/sda11          55719       56977    10112886   83  Linux
/dev/sda12          44072       50636    52733331    7  HPFS/NTFS
/dev/sda13          56978       60801    30716248+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         637     5116671   82  Linux swap / Solaris
/dev/sdb2   *         638        4865    33961410    7  HPFS/NTFS

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1126     3915752    c  W95 FAT32 (LBA)
Filesystem            Size  Used Avail Use% Mounted on
aufs                  881M  776M  105M  89% /
udev                  881M  296K  881M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  881M  216K  881M   1% /dev/shm
tmpfs                 881M   20K  881M   1% /tmp
none                  881M   88K  881M   1% /var/run
none                  881M     0  881M   0% /var/lock
none                  881M     0  881M   0% /lib/init/rw
/dev/sdc1             3.8G  492M  3.3G  13% /media/Crucial
ubuntu@ubuntu:~$

```

---

### Post by quadproc on 2011-02-15
> **Danial said:**
> 
I did run a fsck from live cd, at first it reported that system time is set in future (something in that regard) and it fixed  that. 
If that message means that your system's time setting was farther forward in time than a correctly set clock, that is both interesting and potentially troublesome.  Normally, the system time is set by reading the clock which is part of the mother board.  Sounds like something either changed it, or the data transfer was corrupted.  Either way, it sounds like a problem.
> 
 Following fsck did not return any problem on either sda2, sda3 or sdb2. 
This is good.

> 
I am downloading Maverick again and will burn it to a new CD and see if symptoms persist (as I mentioned earlier that even live CD of Maverick is acting up - which I had given doubtful benefit of bad CD). I will post again with results.
You might be able to save a CD - do you know about md5sum?  That is a mathematical operation which is applied to a file such as the .iso file containing the download.  The result is a fairly short binary number which is effectively unique to that file.  If there is any corruption of the file then the md5sum will not match the published value.  You can find that value at
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
An easy way to check the value is to run md5sum in a terminal, highlight the resulting value, and use your browser's *find* function to look for that string in the Ubuntu page.  If it isn't found then it doesn't match.  If it does match then your CD is good.


New subject:
> 
p.s.: I have another question which in fact is not related to this thread but I am throwing it in.  If at some point you can spare sometime can you look back at my current fstab.  Back in December, I tried to move /home to its own partition.  But now when I checked all the partitions, I do see home partition but nothing in it.  To my little knowledge, fstab is showing only one partition mounting at startup.  Is this correct?  Do I need to mount /home within fstab and what would be the options?This subject is a little bit involved so I will try explain it without too much detail.

There will be a /home created by the Ubuntu installer and it will have a few common and popular directories in it, e.g., Music and Pictures.  This /home will be a part of the root file system / it is just another directory much like /etc or /var.

Usually, the reason for moving /home to another place is to put your files someplace that won't be lost if the OS is reinstalled.  If you relocate it this way then it becomes fairly easy to install new releases.  You might even want or need to share the /home file system with one or more other OSes so putting /home in its own partition has a number of advantages.

When you create a partition for /home usage, it does not have to he on a different disk drive - this is usually a personal choice which depends on factors such as how many disk drives the system can hold and how much you can afford.  There is probably a little more safety in using a separate disk drive.

Now that I have mentioned the background, here is where we get to your question.  When you first create the new /home directory in its own partition, you will have two home directories on your system.  One will be located under / and the other will be located in whatever the new partition has been mounted as, for example /datadrive/home where datadrive is the name used to temporarily mount the new partition.

The purpose of an fstab entry is to get the OS to automatically mount a partition at startup time.  So, if fstab has an entry for / but not one for /home, you will be accessing the original installation's home directory and that probably doesn't have any of your files in it.  But if your fstab has an entry for /home on a different partition then you will be accessing that partition.  And this is what you want.

Here are few lines from my fstab which uses a separate drive for /home
> # / was on /dev/sda9 during installation
UUID=71059336-6d53-4273-ad4e-49dd1a223ed4 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1652a31f-4ee8-493d-a8c4-2bec45b3fc2b none            swap    sw              0       0
# the /home line was added 1/22/2011
UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home           ext3    nodev,nosuid    0       2A couple of things are worth mentioning: I use UUIDs because these are **much** safer than device ids such as /dev/sda9, and the /home entry uses a passno (the last digit in that entry) of 2.  This causes /home to be mounted after / and prevents a possible race condition.

You might also want to post the output of sudo blkid - I find this to be very handy when looking at partitioning issues mainly because it shows me the labels and UUIDs.  And the mount command will show you what is mounted at the time.

I hope that helps to explain a little about partitions and home directories.  Of course, there is much more that can be done with the system's file and partition structure but I will stop here to avoid an information overload.

quadproc

---

### Post by Danial on 2011-02-15
**Thanks a lot for your time and patience, (can not appreciate it enough to justify your trouble.**
 
I will split this response because I started two things at one time (my bad).

> **quadproc said:**
> 
An easy way to check the value is to run md5sum in a terminal, highlight ... 

Yes, I am familiar with that and I used it with both CDs (newly dowloaded Maveric). 

Here is interesting finding when using the new CD.

This CD acted same way as old one - just hanging up with some garble video on top part of the screen.  I restarted and tried again; by pressing <esc> key at startup, I was able to get to the main menu of the CD and was able to choose the 'nomodeset' option; which brought me to command line mode and I was stuck at that point (don't know what to do at that point :(). I tried to not to use the 'nomodeset' and I got the same garbled screen. I put back the Lucid CD and I am booted into Live Session without any problem.  So I am confused and lost that why my system just refused to co-operate with Maverick.

By the way, I have not changed the fstab yet (removing 2nd. swap entry). I guess, I should do it and give another try. I will do this tomorrow due to time constraint.  

Danial

p.s.: I will post another response in regards to /home

---

### Post by Danial on 2011-02-15
> **quadproc said:**
> 
New subject:
This subject is a little bit involved so I will try explain it without too much detail.
quadproc

You put it very clearly and I can say that I understand it much better than before. Unfortunately, I am rushing this response at this time - don't mean to disrespect your effort. I will get back into it later tomorrow in the evening. However, briefly, I do see that I did not configure the new partition properly.  I will be looking into it tomorrow in further detail.  Here is the result of blkid:  This is run in while I am using the live CD.
```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="swap" UUID="3a7ce152-9022-42d2-8069-088a8ce8d58d" TYPE="swap" 
/dev/sda2: UUID="84781de9-0f61-474c-a56e-d6f455826462" TYPE="ext4" 
/dev/sda3: UUID="61e2bc23-bf09-45de-aff1-fb53119daa7a" TYPE="ext4" 
/dev/sda5: LABEL="Download" UUID="6e000c7f-2221-490e-818d-62a8d5d61578" TYPE="ext4" 
/dev/sda6: LABEL="Ganey" UUID="2c97211d-9eb8-4520-9ea7-c091e58b3a3b" TYPE="ext4" 
/dev/sda7: LABEL="Tasaveer" UUID="846a0dc9-58ba-468d-9e19-1fc5b59715c4" TYPE="ext4" 
/dev/sda8: LABEL="Kaghzat" UUID="b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3" TYPE="ext4" 
/dev/sda9: LABEL="Linux-doc" UUID="1d3711f4-d1cf-472d-b09b-f90667a033fa" TYPE="ext4" 
/dev/sda10: LABEL="Temp" UUID="ce1aca59-ceda-4aef-8230-eb2996535daf" TYPE="ext4" 
/dev/sda11: LABEL="Kachra" UUID="3f608fc3-eef3-4dfe-a755-5e83486bb0e5" TYPE="ext4" 
/dev/sda12: UUID="73E1719801BBE72A" LABEL="Win-apps" TYPE="ntfs" 
/dev/sda13: UUID="edbae11b-d8b2-4015-a4ac-db1b42a09578" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="swap" UUID="d898c458-3a28-4abf-9a28-c34d356c0046" TYPE="swap" 
/dev/sdb2: UUID="66B8B439B8B40A17" TYPE="ntfs" 
ubuntu@ubuntu:~$ 

```

I am very sorry but I have to get up because my 5 year old is getting impatient. My work schedule is weird and 4 days which I work, I am out before 6 in the morning and get home after 6 in the evening and as of now he is running around to get my attention to play with me.  I really apologize for this.  Thanks for your understanding.

Danial

---

### Post by quadproc on 2011-02-15
> **Danial said:**
> 
Here is interesting finding when using the new CD.

This CD acted same way as old one - just hanging up with some garble video on top part of the screen.  I restarted and tried again; by pressing <esc> key at startup, I was able to get to the main menu of the CD and was able to choose the 'nomodeset' option; which brought me to command line mode and I was stuck at that point (don't know what to do at that point :(). I tried to not to use the 'nomodeset' and I got the same garbled screen. I put back the Lucid CD and I am booted into Live Session without any problem.  So I am confused and lost that why my system just refused to co-operate with Maverick.

I decided to try to reproduce the same steps that you have tried so I booted from a Live CD and discovered thta I actually have two Live CDs, made a few days apart.  I don't remember why I have two of them so maybe there is some revision to the code stored on them.  I may be able to do a diff on them with some amount of work - I have only one CDROM drive so I will have to copy to disk and then compare CDROM to disk.

Anyway, back to my results.  When I booted from the CDROM I let it get to the point where the screen is a gentle purple with small symbols at the bottom for a keyboard and a human, then I pressed escape and got the selection menu.  Using F6 I picked the nomodeset option and then allowed it to continue booting.  It booted similarly to what it usually does, except that the resolution for the display was not right so text was not displayed in a nice format and the splash was only 4 dots wide instead of 5 but it did boot and eventually displayed the "try it out" screen.  I brought up Google and it worked normally.
 
So I shut things down using restart and I observed that the shutdown seemed to go normally except that the resolution was wrong, just as it was in the startup splash.  As the restart proceeded, I noticed that it seemed to be taking longer than usual for the reboot so I glanced at the keyboard and observed that two of the keyboard lights were blinking.  This is an indication of a kernel panic.  I pressed reset and the next boot proceeded normally and things are back to normal.  But this is disturbing - it means that something was remembered in the system through the restart, and that something really fouled up the kernel.  I will have to check the system log to see if I can figure what happened.

But, putting aside my problems, I did not find the trouble that you are having.  I am suspecting that it has to do with different graphics hardware.  Here is a list of what I am running; it might be useful to eliminate matching hardware from consideration:

Intel i7 950 CPU
6 GB DDR3 RAM
ASUS P6T SE motherboard
Two HD4870 ATI graphics cards set up for crossfire
--- the remainder are not likely to make a difference but I list them for completeness ---
Various disk drives but those are not involved when running from CDROM
HAF case
Power supply not likely to be a problem
Two keyboards - one is a Kinesis Dvorak by USB and the other is a Logitech Sholes by adaptor to PS2 jack
One Logitech trackball by adaptor to PS2 jack
APC UPS connected by USB to motherboard
Floppy connected by USB to motherboard
Eleven-in-one memory reader which eventually connects to motherboard
Parallel interface connected to printer
Ethernet cable to switch/firewall and thence to Internet

I may have missed some other small stuff but the majority is listed above.  I mentioned the USB stuff mostly because it interacts with X windows; I do not think that it is a factor in your problem.

quadproc

---

### Post by Danial on 2011-02-16
**Please look into it only when you have some time to spare.**

> **quadproc said:**
> I decided to try to reproduce the same steps that you have tried so I booted from a Live CD and discovered thta I actually have two Live CDs, made a few days apart.  I don't remember why I have two of them so maybe there is some revision to the code stored on them.  I may be able to do a diff on them with some amount of work - I have only one CDROM drive so I will have to copy to disk and then compare CDROM to disk.

Following your steps,  I used Live CD on my  laptop and without any problem I was up and running. I was able to connect to my network and Googled around. 

Back to desktop, from live session (lucid), I omitted the second swap line, tried to boot again with Maverick to no avail.

I tried to see if I am getting any kernel panic (like you mentioned about keyboard lights flashing) but no sign of that - now this may be because I am using a wireless keyboard (thru usb port).  By the way, when I was able to get to the live cd install menu screen, it was on low resolution same as you mentioned.  However, this was not the scenario with laptop. That has all 5 dots and hi res. display.

My hardware details follows.  I build this machine about 3 years ago (antique: should I say).  It is about time to build another one;)

AMD athlon X2 64 3800
2GB Ram - DDR2 800
ABit n-view series motherboard (not available anymore) - on board graphics nvidia G6150 and on board audio - using dvi port for my lcd display - external sub and speakers 
430W ps (I guess it is Rosewill)
logitech wireless keyboard and mouse thru usb port
internal 500GB Seagate drive (I recently found out that drive does not have S.M.A.R.T. features - oh well. 
internal 40GB Western drive 
(both drives are sata)
Sony dvd rom 
a floppy drive (never used and should come out anyway).
wireless printer Brother
 connected (wired) thru a Linksys wrt54GL router with dd-wrt firmware.
Generic case with front and rear fans and side exhaust.

and basically that is it - plain vanilla nothing fancy.


> I mentioned the USB stuff mostly because it interacts with X windows; I do not think that it is a factor in your problem. 

You are right, just one external hd which is mostly for data and rarely in use - plugged in but not powered on. Connects my cell phone sometime just charging and/or moving pictures to HD. Once in a while uses a usb flash drive - nothing more.

So what do you think now?

BTW, I was reading your earlier post regarding /home.  Once I am able to bring this system up, I hope I will be able to set ip properly this time. Did I ever mention that I am using xfce desktop - would that make any difference?

Thanks,
Danial

---

### Post by Danial on 2011-04-02
I was able to resolve the issue by updating the BIOS and using the nvidia driver from their site.
Thanks to everyone for help and time.

Danial

---

