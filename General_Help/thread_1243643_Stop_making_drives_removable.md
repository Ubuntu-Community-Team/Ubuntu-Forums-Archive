---
title: "Stop making drives removable?"
date: 2009-08-18
forum: General Help
---

### Post by aquascrotum on 2009-08-18
I have 2 hard drives and a total of 4 partitions - my home (Ubuntu) partition, an XP partition, and 2 others that I use for media etc.

IS there a way to get rid of the desktop icons for the non-Ubuntu partitions that come up when the drive is mounted (ie all the time?).  I'm assuming this is only supposed to happen with a removable drive?

---

### Post by mcduck on 2009-08-18
Yes, just configure your drives in /etc/fstab, and set them to mount into any other location than /media. (/mnt, for example).

Everything mounted inside /media will show on desktop and the Places-menu.

---

### Post by imbjr on 2009-08-18
You can go into Configuration Editor and change:

 apps . nautilus . desktop . volumes visible

to false and that will also hide them, but it will also hide any USB stick, for example, you might plug in.

---

### Post by aquascrotum on 2009-08-18
> **mcduck said:**
> Yes, just configure your drives in /etc/fstab, and set them to mount into any other location than /media. (/mnt, for example).

Everything mounted inside /media will show on desktop and the Places-menu.

That sounds like what I want to do...how do I go about editing fstab, do I have to do it in terminal or can i edit the text file?

Also a related query, when I do insert a removable drive, I used to get an icon that distinguished the drive as removable as opposed the standard static drive.  That doesn't happen any more, all drives just appear as a standard disk drive icon.

---

### Post by mcduck on 2009-08-18
> **aquascrotum said:**
> That sounds like what I want to do...how do I go about editing fstab, do I have to do it in terminal or can i edit the text file?
This will open the file for editing in Gnome's text editor:
```
gksudo gedit /etc/fstab
```
Just be sure to create the directories where you wish to mount the drives first. If you need help with editing the file, run"sudo blkid" and "sudo fdisk -l" & post the outputs together with the contents of your fstab file here.

Here's a rather complete guide for fstab: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

> **aquascrotum said:**
> Also a related query, when I do insert a removable drive, I used to get an icon that distinguished the drive as removable as opposed the standard static drive.  That doesn't happen any more, all drives just appear as a standard disk drive icon.
Have you changed the icon theme you are using? Some themes have different icons for different types of drives, others don't..

---

### Post by aquascrotum on 2009-08-22
Well I've managed to change my mount points for the three partitions to the /mnt folder using the Storage Device Manager, everything seems to be functioning ok.

Next question though - can I make a link to the partitions appear in my Documents folder, or preferably even in the Places menu? As at the minute to browse to the partitions I have to go Places>Computer>Filesystem>mnt etc etc  (am getting fussy at this stage!)

---

### Post by ks07 on 2009-08-22
> **aquascrotum said:**
> Well I've managed to change my mount points for the three partitions to the /mnt folder using the Storage Device Manager, everything seems to be functioning ok.

Next question though - can I make a link to the partitions appear in my Documents folder, or preferably even in the Places menu? As at the minute to browse to the partitions I have to go Places>Computer>Filesystem>mnt etc etc  (am getting fussy at this stage!)
Yes you can, but more than 5 items turns it into a kind of 'fold out' menu (for lack of a better name) in the places menu on the gnome panel.

Navigate to the folder in nautilus, then at the top of the window choose bookmarks>add bookmark. Voila! :)

---

