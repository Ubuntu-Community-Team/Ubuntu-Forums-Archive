---
title: "Raid 5 rebuilt at install. Did I lose my data?"
date: 2011-04-17
forum: General Help
---

### Post by PlugInPrius on 2011-04-17
I have 6 drives in raid 5 for data. 2 drives in raid 1 for boot. During install I set my 2 drives as raid 1 and had them formatted. I also told it the 6 drives were raid 5 but did not tell it anything else besides not to format them. 

When I booted for the first time I found that it was rebuilding the raid 5 and the file system type is unknown.

Did I just lose all my data on my raid 5?

---

### Post by kseise on 2011-04-17
Did you specify a filesystem type or set a mount point that will get over written during install?

trying running testdisk on the raid and see if you can detect the partition table.  You might just have the wrong file system type (ext3 instead of ext4 or something like that).  Testdisk will allow you to fix the partition table.

---

### Post by PlugInPrius on 2011-04-17
running testdisk right now. Its currently analyzing.

I think I just left it at "do not use", no mount point and set it not to format the drive.

---

### Post by PlugInPrius on 2011-04-17
No partition found. Doing a deeper scan now.

---

### Post by kseise on 2011-04-17
OK, if you said "Do Not Use", then Ubuntu doesn't know how the disk is formatted.  Don't forget the "disk" is actually the raid array.  Is the array assembled correctly?  If so, you will have to manually mount the array.  The good thing is that since you said not to use the disks, nothing should be lost.  You just have to put the raid together and mount it.

---

### Post by PlugInPrius on 2011-04-17
How would I go about mounting it manually? The partition should be ext4. The Disk utility shows the raid 5 but its not showing a partition.

Testdisk is still running. Its found a bunch of stuff but I dont know what it all means. Might take all night to let it finish its deep scan.

---

### Post by kseise on 2011-04-17
sudo mount -t ext4 /dev/md0 /mnt/raid

You will have to change the /dev/mdxxxx number accordingly.  I think it should be md1 on your setup.  That should at least make it accessible.  I am trying to figure out how to fix the partition table to make that ext4 permanent.

I am going off of this link right now:  [http://ubuntuforums.org/showthread.php?t=1468064]("http://ubuntuforums.org/showthread.php?t=1468064")

---

### Post by PlugInPrius on 2011-04-17
I get this when I try that.
"wrong fs type bad option bad superblock"

---

### Post by kseise on 2011-04-17
Ok, try doing 
sudo mdadm --detail --scan

let's see the output from that.

---

### Post by kseise on 2011-04-17
It seems like the superblocks that tie your array together are screwed up.  You can try 
sudo mdadm --assemble --force --scan /dev/md1
or
sudo mdadm --assemble --force /dev/md1 /dev/sd[bcd]

To automatically detect and reassemble the array.  If the superblocks are screwed up, the array isn't assembling.  If the array isn't assembled, the file system sort of doesn't exist, although it is there once you get the raid reassembled.

---

### Post by PlugInPrius on 2011-04-17
First command assembles the array fine but its a still unknown file system. the second command gives "no recognisable superblock on /dev/sda" "/dev/sda has no superblock"

---

### Post by kseise on 2011-04-17
This might be a stupid question, but is /dev/sda part of the array that you are trying to reassemble?

---

### Post by PlugInPrius on 2011-04-17
sda-sdf is part of the raid 5.

---

### Post by PlugInPrius on 2011-04-17
Well I think I'm going to call this a complete loss.

---

### Post by kseise on 2011-04-19
If you are going to reinstall, go through the process and see if you can set the installer to leave the array alone, but mount it as the ext4.  The data should still be there.  Just don't format the array.

---

### Post by PlugInPrius on 2011-04-19
Thats what I did and there was nothing there. I think it destroyed everything when it rebuilt the array. Oh well. Just lost all my stuff over the past ~15 years. I may start looking into building a backup server since hard drives are pretty cheap now.
 
Thanks for your help.

---

### Post by kseise on 2011-04-19
I am really sorry to hear that.  It doesn't make any sense though..

---

### Post by PlugInPrius on 2011-04-19
Yeah I know.

I thought I did this a while back where during the installation I told it was a raid 5 but dont do anything to it. Then I manually mounted it after installation. Dont know what happened this time.

Next time I'm not even going to tell it about the raid 5 and leave the drive completely alone. Then mess with it after installation.

---

