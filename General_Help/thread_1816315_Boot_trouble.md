---
title: "Boot trouble"
date: 2011-08-01
forum: General Help
---

### Post by MysticMetal on 2011-08-01
This isn't really a ubuntu specific question but since I've had soch good help before...

My computer got shut off when the power blinked, and then wouldn't give me anything but a black screen.  So, I moved the jumper on the video card and the jumper for the battery on the motherboard over and waited a while and then moved them back.  Now after I set my boot order in bios the machine will boot from a cd but not from a hard drive.  It doesn't report a failure, just displays the 'boot from cd:' and then a new line.

I can see my drives and their partitions from the ubuntu live cd and knoppix.

thanks in advance

---

### Post by oldfred on 2011-08-01
Depending on what was happening a power failure is often file corruption.

Does gparted show any symbols which indicate issues with a partition. If so I would run file checks on those partitions. If NTFS use a windows CD and run chkdsk. If ext3 or ext4 run e2fsck.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by MysticMetal on 2011-08-02
It seems as though either I was mistaken of my drive letterings got changed.  After loading ubuntu from live CD and noticing the triangle ! symbol next to one of me drives  I then noticed that the assignments in /dev were different than I had thought.  So, I changed my BIOS boot order and it's working now.

Thanks, it seems I'm still a newbie.

---

