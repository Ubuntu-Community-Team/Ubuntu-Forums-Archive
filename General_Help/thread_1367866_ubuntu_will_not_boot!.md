---
title: "ubuntu will not boot!"
date: 2009-12-30
forum: General Help
---

### Post by madjackrogers on 2009-12-30
So, I was trying to get that annoying beep to go away in firefox/pidgin when I backspaced things, and I think I missed something up.  I added a line of code into /etc/gtk-2.0/im-multipress.conf, and now my system won't boot.

This could also be that I deleted some extra entries from GRUB via menu.lst so I only had the ones I needed.

My symptoms include:
when I try to boot in regular or recovery mode, the ubuntu 8.04 load screen shows up (I relatively recently upgraded from 8.04 to 8.10, then to 9.04, then to 9.10) the orange bar goes back and forth for a while, then it gives me a bunch of errors and dumps me out
as root.  specifically, it says that it couldn't mount the devices, apparently.  general error mounting filesystems.

I tried changing the file multipress.conf back to its original form using the nano command, but it said I couldn't because it was read only, even when I tried using sudo.

I honestly have no idea what I've done or what's going on here.  Can anyone help?

---

### Post by madjackrogers on 2009-12-30
Bump.  I've tinkered around and I still can't find anything to do to fix this.

---

### Post by Leppie on 2009-12-30
have you tried running fsck? if the filesystems cannot be mounted, errors may have corrupted some things.

---

### Post by madjackrogers on 2009-12-30
I just did.  I'm not exactly sure how fsck works, but it came back "clean"?  I have to admit, I don't know as much about linux as I probably should.

---

### Post by Leppie on 2009-12-30
can you manually mount the partitions?
try mounting the root partition and access the boot log file.
you may want to do something like this to check the errors:
```
$grep -i fail /mount/point/var/log/boot  ##change /mount/point to the actual mount point
```

---

### Post by madjackrogers on 2009-12-30
I apologize for being a linux newbie here, but I have no idea what I should do with your post.  How do I know what the mount point is?  Do I put in the command with the ampersand?

---

### Post by shaaaadoooow on 2009-12-30
The multipress.conf has nothing (I think) to do with the your booting problems. If you really didn't change anything aside from that and the grub-menu.lst (Which--I think-- also has nothing to do with your booting problems), 1) Maybe your hard drive just had a problem. Just my thoughts. :)

P.S. Filesystems should NOT be mounted when doing an fsck, so maybe, fsck won't detect any internal problems about the mountability (is there such a term? Hehe.) of that filesystem. So maybe, the filesystem cannot be mounted because of *physical* terms. I'm just trying to help. Hehehe. :)

---

### Post by phillw on 2009-12-30
Hi, despite your tortuous upgrade path, you'll still be on grub legacy.

I'd suggest popping over to Grub2 -- as your grub legacy seems unhappy. You'll need a 9.10 LiveCD for this - But, it is quite painless (I know, I messed up & to use it)


[LIST=1]
[*]**[COLOR=Navy][SIZE=3]Reinstalling GRUB 2 from LiveCD[/SIZE][/COLOR] **
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the 9.10 Karmic LiveCD to the Desktop.
[*]Open a terminal - Applications, Accessories, Terminal.
[*]Determine your normal system partition - `sudo fdisk -l`  (That is a lowercase L)
[*]If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system partition:      ```

     sudo mount /dev/sdXY /mnt 
```
[LIST]
[*]Example: sudo mount /dev/sd*a1* /mnt
[*]Note: substitue the correct partition: sda1, sdb5, etc.
[*]Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
 
[*]Only if you have a separate boot partition:
[LIST]
[*]     ```

     sudo mount /dev/sdXY /mnt/boot 
```
 with sdXY being your /boot partition designation.
[/LIST]
 
[*]Reinstall GRUB 2:      ```

     sudo grub-install --root-directory=/mnt /dev/sdX 
```
[*]
[LIST]
[*]Example: sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the correct device - sda, sdb, etc. Do ''not'' specify a partition number.
[/LIST]
 
[*]Unmount the partition:       ```

     sudo umount /mnt 
```
[*]Reboot.
[/LIST]
That's from [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[/LIST]
You'll find a load of stuff on Grub2 - and how to customise it, etc. over there & in drs's signature.

Regards,

Phill.

---

### Post by fdmille on 2009-12-30
Seems that you messed up your menu.lst file.  Recommend you make a SuperGrub boot disk and reinstall grub.  The Web site for Supergrub is: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by madjackrogers on 2009-12-30
Phillw:  I took your advice, and now when I boot, I get some business about GNU 1.97~beta4 and it gives me a command line starting with

sh:grub>

what do I do now?

---

### Post by madjackrogers on 2009-12-30
fdmille I tried your advice as well; booting from the CD lets me get into ubuntu, but without the CD I'm still at the same point with the sh:grub>  I tried ls, and it listed what I assume are my partitions (hd0) (hd0,6) (hd0,5) (hd0,3) (hd0,2) (hd0,1)

---

### Post by madjackrogers on 2009-12-30
alright, I installed grub 2.0 and got it working.  However, I still have 4 entries of ubuntu on my screen.  How can I clean that out properly?

---

### Post by ticthak@AOL.com on 2010-01-06
Your GRUB@ list is probably "properly clean"- I imagine it lists your current working boot default(2.x.yy-something generic) first, then a recovery version that uses the same kernel that gives you a very useful menu of things to help (one of which is "boot normally", but will dump you to a cli terminal from which you can use startx to get your GUI) plus 2 alternate boot choices based on the previous kernel- a good idea to save these, or even more choices as you upgrade the kernel. Since the first thing in the list is default after the timeout, who cares what else is in the list if the default works? And if it doesn't, something there can rescue you...

---

