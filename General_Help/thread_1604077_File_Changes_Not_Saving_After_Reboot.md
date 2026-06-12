---
title: "File Changes Not Saving After Reboot"
date: 2010-10-23
forum: General Help
---

### Post by Waggoneer on 2010-10-23
I have a problem that began just in the last 3 days. I am not sure if the issue is with Ubuntu or the SSD drive I am using. The issue originally was noticed when a document I had saved to my desktop disappeared. 
I did a search of everywhere on my computer and couldn't find it. So I downloaded it again and this morning it was gone again.

Once I noticed the issue I realized, also, that the system update I had run the night before was lost too. In update manager the program reported that I had not checked for updates in 3 days, though I had just updated the previous night. 

What could this issue be? I am running 64 bit Maverick.

---

### Post by sikander3786 on 2010-10-23
How did you install Ubuntu? Is this an external SSD?

---

### Post by Waggoneer on 2010-10-23
> **sikander3786 said:**
> How did you install Ubuntu? Is this an external SSD?

A normal install from CD. And the SSD was a replacement/upgraded drive for a Dell XPS 1210 laptop.

---

### Post by Waggoneer on 2010-10-25
Anyone have any ideas? I haven't turned my computer off in a few days, to avoid losing things again.

I found this in the dmesg log, is it applicable?

> 
[    2.321401] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.321407] EXT4-fs (sda1): write access will be enabled during recovery
[    2.387662] EXT4-fs (sda1): recovery complete

---

### Post by Waggoneer on 2010-10-31
One more thing in the logs...

> EXT4-fs (sda1): INFO: recovery required on readonly filesystem
EXT4-fs (sda1): write access will be enabled during recovery
EXT4-fs (sda1): orphan cleanup on readonly fs
Oct 31 08:36:49 LinTop kernel: [    2.399889] EXT4-fs (sda1): 85 orphan inodes deleted
Oct 31 08:36:49 LinTop kernel: [    2.399896] EXT4-fs (sda1): recovery complete
Oct 31 08:36:49 LinTop kernel: [    2.419685] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro> Oct 31 08:36:49 LinTop kernel: [    2.367836] EXT4-fs (sda1): orphan cleanup on readonly fs
Oct 31 08:36:49 LinTop kernel: [    2.368055] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3156075
Oct 31 08:36:49 LinTop kernel: [    2.369070] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3156039
Oct 31 08:36:49 LinTop kernel: [    2.371108] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3158980
(...)
Oct 31 08:36:49 LinTop kernel: [    2.399049] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3278618
Oct 31 08:36:49 LinTop kernel: [    2.399083] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3278599
Oct 31 08:36:49 LinTop kernel: [    2.399465] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3276886
Oct 31 08:36:49 LinTop kernel: [    2.399510] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3158863
Oct 31 08:36:49 LinTop kernel: [    2.399854] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3158546
Oct 31 08:36:49 LinTop kernel: [    2.399889] EXT4-fs (sda1): 85 orphan inodes deleted
Oct 31 08:36:49 LinTop kernel: [    2.399896] EXT4-fs (sda1): recovery complete
Oct 31 08:36:49 LinTop kernel: [    2.419685] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)Are the orphans that are being deleted my recent file system changes?

---

### Post by ksolowoniuk on 2011-01-08
I'm just wondering if you found a fix for this? I've been having the same problem, at first noticing missing files or settings changing back and then realising that nothing was being written to the drive. I upgraded the firmware on the drive as well as my BIOS and ended up switching back to Windows 7. The drive eventually failed completely. I received the replacement and, thinking that the BIOS and firmware upgrades had solved the problem, tried running Ubuntu again only to find that the issue still exists.

---

### Post by deltacomp on 2011-01-30
I have the same problem, I have tried reformatting the SSD and restarted the comp and to my surprise, the old OS install was still there! Pretty interesting stuff. Since I had wiped the SSD completely and found the old OS was no longer there, then reinstalled a fresh copy of Ubuntu and just a couple days ago the same thing. When I add a file or make a change to a file I find the change has not been saved. 

If anyone has any ideas please let us know. 

Thanks.

---

### Post by Zasha on 2011-02-08
> **deltacomp said:**
> I have the same problem, I have tried reformatting the SSD and restarted the comp and to my surprise, the old OS install was still there! Pretty interesting stuff. Since I had wiped the SSD completely and found the old OS was no longer there, then reinstalled a fresh copy of Ubuntu and just a couple days ago the same thing. When I add a file or make a change to a file I find the change has not been saved. 


I did exactly the same as deltacomp.. Completely wiped the drive (SSD), reinstalled Ubuntu and still booted the old OS from before the reinstall.

---

### Post by visual1ce on 2011-04-14
This issue is known as time warp or groundhog day and you can read more about this problem on the OCZ and Corsair forums.

In the past month my Ubuntu system has eaten through 3 SSDs! The first one died unexpectedly but the last two developed this time-warp/groundhog day issue. In particular the symptoms were the same: from a certain point onwards no changes were persisted after a cold start; reboot was fine - the changes would still be there but if I did a cold start, changes that I made to files had somehow disappeared as well as files that I had added. Also, files that I deleted magically returned.

I found that doing a quick format had no effect but doing a full format did work, however; after the second cold start after the full format, groundhog day was back with a vengeance.

I was using FDE - full disk encryption with LUKS/dm-crypt. After reading about the way SSDs work and in particular the TRIM function I now realise that encryption and SSDs do not mix (at least not for now). I was wondering how many of you posters were/are also using FDE?

Have any of you enabled TRIM? I've read that others have run SSDs under Ubuntu without enabling TRIM which should also be fine but apparently enabling TRIM increases the life of the drive.

Here is a link to a resource for tuning your SSD:
[cptl.org » Blog Archive » Tuning Solid State Drives in Linux]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/")

---

