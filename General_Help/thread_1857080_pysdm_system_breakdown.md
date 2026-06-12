---
title: "pysdm system breakdown"
date: 2011-10-09
forum: General Help
---

### Post by Grisogonus on 2011-10-09
First of all, you're dealing with a total noob here. This was bound to happen, I pushed where I shouldn't and now I'm stuck.

Here's the story: I finally found a great player in Ubuntu - Guayadeque, but it does have an issue which is also may be an issue of Ubuntu itself, and it has to do with automatic mounting of hard drives.

So I have an ntfs hard drive where I keep my music collection, in order to be able to access it from windows also. Seemingly Ubuntu doesn't mount other hard drives / partitions by default, and his causes Guyadeque library to appear empty every time I turn off or restart my pc. Then I need to mount the hard drive and rescan library for files to show up again.

Thus I wanted to make ubuntu automatically mount that other drive when system boots. I have read that pysdm (device storage manager) was the easiest way to do it (aparently wrong).

When I started it, I coundn't find an option for automatical mounting, but there was a mount button there, grayed out, so I used assistant or something like that, ticked a few options there, allowing any user to mount/unmount and similar. Nothing much I thought. I restrted the system and entered pysdm again, now the mount button was no longer grayed out, so I pressed it and all seemed fine. At first I didn't notice, but then I realized my partitions were all mixed up, sda sdb and sdc were not as before.

I restrted again and that was it, I cannot boot ubuntu any longer, stuck with the black screen.

Now I can try  and boot from cd, but although I realize I need to rectify this manually in fstab, I do not have the slightest clue where to start or what to do.

All help is appreciated. Thank you for your time.

---

### Post by dcstar on 2011-10-10
> **Grisogonus said:**
> 
..........
Now I can try  and boot from cd, but although I realize I need to rectify this manually in fstab, I do not have the slightest clue where to start or what to do.

All help is appreciated. Thank you for your time.

After you boot from the CD select the disk partition where your Ubuntu installation is and post the contents of the /etc/fstab file in that partition.

---

### Post by Grisogonus on 2011-10-10
This shoud be it:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb6 during installation
UUID=ee2e36a8-0132-4b5b-ac4b-e308d78c10f6  /            ext4  errors=remount-ro    0  1  
# /boot was on /dev/sdb1 during installation
UUID=e55ee612-9634-4d91-93c9-a72f639fb091  /boot        ext4  defaults             0  2  
# /home was on /dev/sdb7 during installation
UUID=b44426bb-f094-4108-8881-8bf996ea10e6  /home        ext4  defaults             0  2  
# swap was on /dev/sda5 during installation
UUID=0bcc47b7-6f64-4dde-a8e9-353c5cc5ece4  none         swap  sw                   0  0  
# swap was on /dev/sda7 during installation
UUID=9010d1db-8e97-4020-b1b9-dbfb89b57988  none         swap  users,sw,user        0  0  
# swap was on /dev/sdb5 during installation
UUID=c3f3f237-052e-4161-baab-ced06ab3d69a  none         swap  sw                   0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  


This doesn't make much sense to me, while I get some fragments of it, I definitely do not know the syntax well enough to say what is wrong here.

I think I have messed this swap, users, sw, user, I remember changing this with pysdm. Also the errors=remount-ro stuff? :?:

---

### Post by dcstar on 2011-10-11
> **Grisogonus said:**
> This shoud be it:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb6 during installation
UUID=ee2e36a8-0132-4b5b-ac4b-e308d78c10f6  /            ext4  errors=remount-ro    0  1  
# /boot was on /dev/sdb1 during installation
UUID=e55ee612-9634-4d91-93c9-a72f639fb091  /boot        ext4  defaults             0  2  
# /home was on /dev/sdb7 during installation
UUID=b44426bb-f094-4108-8881-8bf996ea10e6  /home        ext4  defaults             0  2  
# swap was on /dev/sda5 during installation
**UUID=0bcc47b7-6f64-4dde-a8e9-353c5cc5ece4  none         swap  sw                   0  **0  
# swap was on /dev/sda7 during installation
**UUID=9010d1db-8e97-4020-b1b9-dbfb89b57988  none         swap  users,sw,user        0  0**  
# swap was on /dev/sdb5 during installation
**UUID=c3f3f237-052e-4161-baab-ced06ab3d69a  none         swap  sw                   0  0**  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  


This doesn't make much sense to me, while I get some fragments of it, I definitely do not know the syntax well enough to say what is wrong here.

I think I have messed this swap, users, sw, user, I remember changing this with pysdm. Also the errors=remount-ro stuff? :?:

Boot off the Live CD and use **gparted** to examine the hard disk and check that the UUID of the actual partitions match what is in the fstab file.

---

### Post by Grisogonus on 2011-10-11
OK done per proposal, there seems to be some strange mixup here, I do not have a clue how I accomplished any of this.

Gparted says my linux partition (whole drive actually) is sdc and there is no sdc in fstab, actually ther is that ntfs part, but it can not be as that whole disk is linux ext4. Could this somehow get mixed up?

Is there a way to retrieve my old fstab file? In /etc I noticed fstab.bak file, is this some sort of backup?

I guess some of my partitions changed places, basically I have 3 hard drives, 1 for linux (this should be sdc), 1 for windows (sdb) and 1 for music (sda - this was the last drive I added). On my windows drive (sdb) there are 2 older partitions of linux (it was planned as dual boot from the same drive, but this never got in action), could those somehow have emerged instead of sdc? No clue, err can you direct me what would be best course of action next?

---

### Post by Grisogonus on 2011-10-16
This takes awfully long time for me, thnks for helping but I will format my ubuntu drive, the unpopular solution, install ubuntu anew.

For other noobs out there, I suggest you be extremely careful with pysdm, in fact I'd say you can do far less harm editing fstab itself than messing with pysdm. It is not only a graphical ui for fstab, as some claim. Also, backing up fstab when everything works fine seems a great idea.

Cheers.

---

