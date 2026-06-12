---
title: "Boot Stucks at &quot;stopping system v run level compatibility&quot;"
date: 2011-08-12
forum: General Help
---

### Post by jamesisin on 2011-08-12
My roomie's been using one of my Ubu machines (11.04) while his machine is away at rehab.  That machine has been running fine, but today he was removing his Android phone and his USB connected NTFS external (both using Safely Remove) and...

Phone safely removed
Drive gave an error (couldn't remove probably the device busy error)
Reboot

Now it won't boot past that point ("stopping system v run level compatibility").

Anybody want to have a go at this one?

---

### Post by hyfanious on 2011-08-13
did u checked ur partition table and boot flag?

---

### Post by jamesisin on 2011-08-13
I can log in at a command prompt so if you can tell me which commands to run and what I should see/fix I'll do it right now.

---

### Post by hyfanious on 2011-08-13
```
sudo fdisk -l /dev/sda

```

or use ur path of ur hard drive instead of sda

---

### Post by jamesisin on 2011-09-10
Sorry, this laptop problem slipped to the bottom of the priority pile...

I have run fdisk:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e61c9

   Device Boot   Start     End         Block    Id   System
/dev/sda1    *       1     9601     77111296    83   Linux
/dev/sda2         9601     9730      1037313     5   Extended
/dev/sda5         9601     9730      1037312    82   Linux swap / Solaris
```

I'm not clear how that will help but I'm looking forward to learning what you have to teach.

---

### Post by mraswan on 2011-12-19
This thread helped me move forward with this issue:
[http://ubuntuforums.org/showthread.php?t=1850641](http://ubuntuforums.org/showthread.php?t=1850641)

BTW I upgraded to 11.10 from 11.04 when I faced the same thing. 

I am cut pasting here suggestion in that thread that helped me:
" 				 				**Re: Gnome3 installed + reboot = Stopping System V runlevel Compatibility. Help Please** 			
 			 			 		   		 		 		Sorry to be so late to the rescue, but I came up with a solution that worked for me. 
1. Ctrl+alt+f1 and login.
2. After logging in I ran sudo dkpg --configure -a
3. This will probably run for a while, and spit out some errors, but it  will work for the most part. Once it's done, run sudo apt-get  dist-upgrade
4. Once it's done, sudo apt-get update, and then reboot. 
5. Still having a little trouble with booting, because everytime I start up I have to ctrl+alt+f1 and startx
" by [bholzer]("http://ubuntuforums.org/member.php?u=1387235")

---

### Post by fire-fly on 2013-03-30
> **mraswan said:**
> This thread helped me move forward with this issue:
[http://ubuntuforums.org/showthread.php?t=1850641](http://ubuntuforums.org/showthread.php?t=1850641)

BTW I upgraded to 11.10 from 11.04 when I faced the same thing. 

I am cut pasting here suggestion in that thread that helped me:
" 				 				**Re: Gnome3 installed + reboot = Stopping System V runlevel Compatibility. Help Please** 			
 			 			 		   		 		 		Sorry to be so late to the rescue, but I came up with a solution that worked for me. 
1. Ctrl+alt+f1 and login.
2. After logging in I ran sudo dkpg --configure -a
3. This will probably run for a while, and spit out some errors, but it  will work for the most part. Once it's done, run sudo apt-get  dist-upgrade
4. Once it's done, sudo apt-get update, and then reboot. 
5. Still having a little trouble with booting, because everytime I start up I have to ctrl+alt+f1 and startx
" by [bholzer]("http://ubuntuforums.org/member.php?u=1387235")

Thanks! dbkpg--configure -a, reported the gdm need to be reinstalled and problem resolved.

---

### Post by oldos2er on 2013-03-30
Old thread closed.

---

