---
title: "My Entire Os Disappeared"
date: 2012-05-28
forum: General Help
---

### Post by stewi1014 on 2012-05-28
Hello,
After having been running for 3 days, my Ubuntu was getting a bit sluggish, so i restarted it. when my computer booted up, grub said could not find file. being a bit knowledgeable about Ubuntu i knew what it meant. so after another try i booted the install disk, and opened disk manager thinking that my hdd was dying, i checked its smart status and it said the disk was healthy, and the windows partition mounted and read fine. i then tried to mount the ext4 file system, it then gave me an error (cant remember exactly) saying that i couldn't mount it because of a block error or because another program was using it. i closed disk manager and the same error happened. i then proceeed to open gparted and did a check/repair of the file system, it completed successfully. i then mounted the file system with no problems. i then opened it, and nothing was there except for the lost+found folder. however, gparted said that 20gigs was still used (same as before my files/Ubuntu disappeared). i then opened nautilus as root (through terminal) and checked the size of the lost+found folder, and it was 20gigs...

so, can anyone tell me what is going on, and maybe how to fix it.
i am currently running my 2nd self test on the hdd.
i also made this computer out of old parts from the dump if that helps any.

---

### Post by stewi1014 on 2012-05-28
I have found that searching for my files in the lost+found folder works, i have managed to recover 2 of my movies (no big deal). i would just really like to reconstruct Ubuntu to a working condition.

EDIT: Just found my whole home folder. it is inside a folder called #6291457

---

### Post by xyzzyman on 2012-05-28
You should remove 'dafaq' before a mod does it for you.

To the point, you clearly have data corruption. Where is this "self-test" that you are running? If a full surface scan passes, you should run a memtest. If both pass, it's still possible one or the other is bad, but you could also have a bad mobo, bad power supply, etc... Or it could have been a fluke caused by an improper shutdown or even a fluctuation from your power at the wall. 

I don't know where you live, but if it's in a hot area then people turning on their air conditioners in some places causes voltage to fluctuate and drop which can cause problems.

---

### Post by stewi1014 on 2012-05-29
the self test is in disk utility (i forgot its name and said disk manager in original post). I am pretty sure that the HDD is in working condition. i will run another test on it. if ram could cause a problem like this, then i think that there is a big chance that it is the problem. i have four 2gig sticks of ram (none of them are broken) and all operating systems i have used on this computer say i have exactly 6 gigs of ram, and the way it behaves when i move/remove sticks of ram from the mobo makes me think that its not the mobo limiting the ram to 6 gigs. another thing is that i used to have problems with the ram, where  the whole computer would just crash (no VGA, DVI, or HDMI output, power light still on). i fixed this my changing a whole bunch of variables in the BIOS (some sequence of numbers like 6-6-32-6-132-6-6-6) and that seemed to stop the crashing. so i think there is a fair chance it is the ram, however it has passed all memtests before (most recent one one month ago), but ill do another memtest. another thing to mention is that one of the reasons I restarted the computer was because i couldn't put files on my external HDD because it was mounted as read only.
  Ilive in Perth, but it is winter here so I not many people would have the air-con on, but it might be something generic like the power, because a week ago a different desktop's graphics card started playing up and one of my server's HDDs died as well, but it was part of a raid5 system, so no data lost :D
but i still cant find out witch harddrive actually died on the server, I just know it was part of the raid system. but back to the broken desktop, is there any way to restore the folder tree and files, or is a reinstall the only way (and some backups taken with clonezilla semi regularly). thank you for the help

EDIT: I cant find a way to remove the dafaq from the title

---

### Post by cariboo on 2012-05-29
Have you run fsck on your partition? Boot using the live CD, once at desktop open a terminal, and enter the following command

```
sudo fsck /dev/sdxX
```

Where /dev/sdX = your root partition.

---

### Post by stewi1014 on 2012-05-29
I tried fsck and got this:
```
stewi@stewi-HDD:~$ sudo fsck -f /dev/sda3
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?
```
as you can see i installed Ubuntu on my external HDD, so i guess ill use my external HDD until i am sure i can't get the data back or if i do get the data back.

---

### Post by gnusci on 2012-05-29
Give a good low level check to your HD with a tool like SpinRite, then use a Live CD of BackTrack to recover you data.

---

### Post by stewi1014 on 2012-05-31
well i reinstalled Ubuntu. i managed to get back most of the files that i wanted to keep. this is definitely the weirdest problem i have ever had with Ubuntu. I also found out that some windows programs like to store data in the boot track (sector 2 to 63) ,so that may have something to do with it.
```

/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
/usr/sbin/grub-setup: warn: Sector 34 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
/usr/sbin/grub-setup: warn: Other software is using the embedding area, and there is not enough room for core.img.  Such software is often trying to store data in a way that avoids detection.  We recommend you investigate..
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.

```

---

### Post by wilee-nilee on 2012-05-31
The boot-repair tool has a flexnet fixer.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[ATTACH]219037[/ATTACH]

---

