---
title: "Increasing home partition and shrinking &quot;/&quot;"
date: 2010-05-09
forum: General Help
---

### Post by Igorpan on 2010-05-09
Hi,i want to decrease my "/" partition size and increase home partitions size.

What i did is, booted up on LiveCD and shrinked "/" partition,but it doesn't let me to increase home partition size.

[http://img535.imageshack.us/img535/7825/screenshotsq.png](http://img535.imageshack.us/img535/7825/screenshotsq.png)

Second one to the left is "Home"

Any ideas ? :S

---

### Post by jerome1232 on 2010-05-09
That screenshot doesn't tell me which partition is /dev/sda3 and which one is /dev/sda4, from what you've said I'm assuming /dev/sda3 is the root partition your shrank (the one directly left of the unallocated space) and /dev/sda4 is your home partition, directly right of /dev/sda1 and directly left of /dev/sda3.

In which case you have a small problem, your root partition (sda3) is in between sda4 and that unallocated space, so in order to expand your home partition you need to delete your root partition, it's in the way. I can think of a very convoluted approach that would avoid a reinstall but it's kind of a crappy way to do it.

1) backup the /home files, make a tar and stick it on that ntfs partition, do this from the live cd. I wouldn't even bother compressing it.

2) Delete the sda4 partition.

3) Move your /root all the way up against sda1, your ntfs partition. (gparted can move partitions like that if I remember right)

4) create a new partition in the unbroken large area that is now unallocated, this will be your new /home.

5) copy your backup into the new partition.

6) mount the root partition from live cd and edit fstab, you'll have to update the /home mount options, prbly the /dev/sdx path and the uuid's. Double check all uuid's and such make sure they are correct. I'm pretty sure you won't need to adjust grub settings. Then save and reboot. Maybe cross your fingers. :)

7) I told you my solution was convoluted, I'm not sure if there's an easier way to do it, maybe just backup your personal files and reinstall with a better partition scheme and restore your files from backup. If you mess up anything attempting what I described you may need to reinstall Ubuntu anyways. So unless your comfy and completely understand what I said don't attempt it.

---

### Post by Igorpan on 2010-05-09
Yeah,I understood it, but I thought there was another(easier) way to do it.

Oh well,thanks for help,and yeah, I will keep my fingers crossed :D :)

---

### Post by dino99 on 2010-05-09
to do that work i use partedmagic

---

