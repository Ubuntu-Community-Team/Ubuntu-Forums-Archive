---
title: "How to copy boot hard disk to usb stick"
date: 2011-05-29
forum: General Help
---

### Post by ktubu on 2011-05-29
Hi

I'd like to move my existing Ubuntu installation from my hard disk (/dev/sda1) to a USB stick. How do I copy the data from HD to USB? 

dd is obviously not the right option since the HD is 320GB and the USB stick only 16GB. However, only 3.5GB are used so this makes perfect sense... And it would make my HTPC even more silent |-)

Thanks!
K

---

### Post by oldfred on 2011-05-29
I am a believer in clean installs. It avoids a lot of time looking for thing that changed. Grub settings, fstab etc.

You then copy /home and export a list of installed applications.  If you made any manual system setting changes in /etc you may want to copy those. 

With a USB Flash drive you do want to make setting changes to reduce writes (like on SSDs) as that is the slowest thing with a Flash drive.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

My backup procedure is so I can reinstall if necessary and not a full image.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

But I keep several working installs on different drives and flash drives.

---

