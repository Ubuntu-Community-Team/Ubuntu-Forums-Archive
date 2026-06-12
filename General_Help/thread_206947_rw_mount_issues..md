---
title: "rw mount issues."
date: 2006-06-30
forum: General Help
---

### Post by matttail on 2006-06-30
Hi all, 
I have hda partitioned into 4 pieces.  hda1 is linux, hda2 is swap, hda3 is windoze, and hda4 is a fat32 drive for sharing between linux and windoze.  I have hda4 in my fstab set to mount rw, users.  I also have it set up to be shared over my windoze network.

I have two problems, I have to umount and mount the drive with my user everytime I reboot so I (not only root) has write access to it.  

The second problem is that it will randomly change to read only, at which point I'm basically forced to reboot my system becuase I can't umount it becuase "the device is busy"  Edit: I have fianlly succecded in getting it to remount, and that has returned my write access without rebooting, but still I can't figure out why it's taking it away in the first place.  No error messages, nothing.  

 

How can I go about fixing these two issue?  Any help is much apprechated.

---

### Post by aysiu on 2006-07-01
These will help with general mounting issues:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

I don't know anything about sharing over a network, though.

---

### Post by matttail on 2006-07-01
Thanks for the links, but I have the drive mounted already, and I can access it just fine.  It mounts rw, but the problem is that sometimes (randomly as far as I can tell) it switches to being read only.  To fix it I have to remount (sudo mount -oremount /dev/hda4).  It's also in my fstab like this:
/dev/hda4       /home/matttail/Desktop/media vfat rw,users

---

### Post by aysiu on 2006-07-01
Try this: ```
/dev/hda4 /home/matttail/Desktop/media vfat iocharset=utf8,umask=000 0 0
``` instead of this ```
/dev/hda4 /home/matttail/Desktop/media vfat rw,users
```

---

### Post by matttail on 2006-07-01
I chnaged out those lines in my fstab last night, went to bed - got up this morning and started moveing a few files around and transfering some files from my main linux ext3 system to the fat32 in question at hda4 and it happened again.  Just all of a sudden I no longer have write access becuase the drive is now mounted ro.  Again a remount fixed it, but I'm not getting any error messages or any idea how to invistigate this problem.  (didn't try rebooting to see if my user had access by default or not, I'm more concerned about it taking away my write access.)

---

### Post by aysiu on 2006-07-01
Hm.

I know this might seem a weird thing to try, but at this point, what would it hurt? Could you try maybe a different mount point? ```
sudo umount /dev/hda4
sudo mkdir /othername
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace it with this line ```
/dev/hda4 /othername vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
ln -s /othername /home/matttail/Desktop/media
```

---

### Post by matttail on 2006-07-01
ok, I've tried this.  However somehting isn't quite right with the symbolic link.  If I go to /music I can read and wirte to the drive, but .../Desktop/media is empty.  (and it crashed nataulius the first time I tried to open it up)

---

### Post by aysiu on 2006-07-01
Hm. Maybe I screwed up the command somehow. Go ahead and delete the symbolic link.

Then just middle-click-drag the /music folder to your desktop and select **link here**.

---

### Post by matttail on 2006-07-01
I got it figured out, just needed trailing forward slash for the Directoires.  I should have thought to try that before posted back.  Anyways, I'll see if this works and let you know.  Thanks for your help thus far!

---

### Post by matttail on 2006-07-01
Nope, same problem.  I just came back after being away for a bit and found that write access had been removed agin.  Any other ideas?

---

### Post by aysiu on 2006-07-01
I have no brilliant ideas about this.

Was the FAT partition created by Ubuntu or by Windows?

---

### Post by matttail on 2006-07-01
I think the partition was created and formatted by Ubuntu.  It's been a bit since I did it, so I'm not perfectly sure.  I ran fsck to see if it came up with any errors, here's the output:
# fsck /dev/hda4
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/Pictures/Slide Edited
  Contains a free cluster (9699334). Assuming EOF.
Reclaimed 1085 unused clusters (17776640 bytes).
Free cluster summary wrong (3657889 vs. really 3658974)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/hda4: 20247 files, 6104279/9763253 clusters
----------

I pressed one for it to correct the error, but it seems to have left everything alone.  Could this be the problem, or should I run some other checks?

---

### Post by aysiu on 2006-07-01
That fsck output is a bit beyond me. I'm sorry.

Can you boot into Windows and see if there's anything out of the ordinary on the FAT32 partition from that side?

---

### Post by matttail on 2006-07-01
I'll see about getting into windws.  I heavn't been *there* in months.  Gotta clear out a virus first.  thanks again.

---

### Post by benplaut on 2006-07-01
I think this may have been a rogue update... i'm experiencing similar trouble.  Right now, it's messed up to a point where anyone can mount, but *nobody* can write... not even root.

It's really annoying...

<edit>

never mind... turned out i had a bit of filesystem corruption.  If you want to test that on your own, just post in this thread the output of dmesg.

---

### Post by matttail on 2006-07-05
Windows didn't find any errors on the music drive.  There were several wonky errors with the windoze partition though.  I had to put it into an other computer running windows, use knoppix and ntfstools to mark the drive for scanning on reboot before I could get at it though.  

Still having the problem.     :(  Any other ideas?

---

