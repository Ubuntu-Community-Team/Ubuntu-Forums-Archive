---
title: "Boot to Windows 95 ?"
date: 2011-10-10
forum: General Help
---

### Post by oygle on 2011-10-10
I currently have a boot to windows XP setup in the grub menu (using 11.04). Now I need to mount a windows 95 disk (2 partitions), or more the point, boot to the windows 95 drive.

Here is what 'mount' shows when the drive is simply mounted via a usb connection.

```
/dev/sdc1 on /media/W95_C type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc5 on /media/W95_F type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

Here is the grub.cfg code for the windows XP setup ..

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 8efc2d0bfc2cef61
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

so do I just add the same sort of lines after the windows xp code, to reflect windows 95 ?

Oygle

---

### Post by oygle on 2011-10-10
I had previously install 'startupmanager' , so I powered on the windows 95 drive, then ran startupmanager , and it seemed to recognise the win95 drive. So I will reboot and see if there is an option on the menu.

---

### Post by oygle on 2011-10-10
Well, it sort of worked, but only to see a menu option and take that option. It did boot, but fell over because of the dos boot files. Those boot files want a drive called "C".

The drive is external, USB, so it is no longer "drive C".

Any way for grub to force the drive number to be "C" ??

Well "C" and "F" , as the drive has 2 partitions  ??

Oygle

---

### Post by Mark Phelps on 2011-10-11
Grub doesn't use drive letters.  That is an MS Windows convention.  So, no, there is no way to force GRUB to assign any letter at all.

Also, Windows 95 won't run from an external drive.  So, if that is why you are trying to boot using that drive, you're wasting your time.

---

### Post by oygle on 2011-10-13
Mark - yes I was trying to run win 95 from an external drive, and had messages about memory limit exceeded. Decided to simply run it from another box, as an internal drive (no usb support, terrible).

From your other notes, it looks like an impossibility, re drive letters, etc. Thanks.  :)

Oygle

---

### Post by mastablasta on 2011-10-13
why you need to boot to Win95 drive? Xp can handle Win95 programmes just fine for a couple of years now. but if there is still an issue there is always VM or Virtualbox.

---

### Post by oygle on 2011-10-13
I don't know VM or virtual box. I need to use win95 to convert many old files, like ms works, ms money, etc,etc.

They can't be installed on XP, as the original CD's or diskettes have read errors. Even if I could copy all the files, there are still DLL's and other files under windows itself, not just the app. Also there are the registry entries. All up, it's not as easy as just copying a few files to XP and then expect it to work.

Easier to just use the win95 drive. I did think of WINE, but that could be time consuming also.

---

### Post by Mark Phelps on 2011-10-13
Can you boot from the Win95 drive OK?

If you can, and want to experiment, then check out LapLink website.  They have an app that allows you to "migrate" apps from one PC to another.

What it does is allow you to select the apps.  Then, it hunts down all the stuff associated with each app, including registry entries, and packages all that stuff into a single file.

You then copy the file to the "target" PC, install the Laplink app on the target PC, run it, open the saved file -- and can now add the apps to the new PC, without actually installing them.

It might NOT work, but if you want to experiment, it may be worth a try.

---

### Post by weezyrider on 2011-10-13
If your computer has newer video card, more ram and other new configurations, XP/95 probably won't run. I ran into that with the Original Russian version of Tetris. (I like the backgrounds and music. Wish it would be re released.)
There's a program called DOSBOX you can look up. That ran another original Tetris.

---

### Post by col48 on 2011-10-13
For what it's worth, I have W95 installed in VirtualBox in my Hardy (8.04) Partition.  It is not officially supported and I had to fiddle to get a reasonable but not optimal (by W95 standards) screen resolution (was it change some options?) and moderately good approximation to colours (update the graphics driver, if I remember rightly).  There is no USB support in W95 which makes communication with the outside world difficult as every peripheral I have is USB.  However, I can read and write files on the W95 virtual disk in Ubuntu (although I am careful not to change the size of any of them).

I haven't used it for over a year now, but it was useful while I was adjusting to Ubuntu and needing to think of new ways to do old things.

---

### Post by oygle on 2011-10-16
Thanks for the replies. I will just keep it simple and use win95 as an internal drive, convert all the files, then toss the drive.

---

