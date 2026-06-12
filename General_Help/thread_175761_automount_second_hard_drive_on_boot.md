---
title: "automount second hard drive on boot"
date: 2006-05-13
forum: General Help
---

### Post by aaarg on 2006-05-13
(stupid newb question disclaimer)
i put another hard drive in my ubuntu box for more storage on my samba server. i am having to go into the disk manager and i guess reactivate it after every reboot. it is ext3...what do i need to put into fstab to have it automount to the place i want? i have tried to "wing" it and it has failed miserably :)

thanks

---

### Post by Omnios on 2006-05-13
wiki on mounting.
[https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29")

 This is on fstab.
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by Omnios on 2006-05-13
Here found a post about it.

 [http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3]("http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3")

---

### Post by aaarg on 2006-05-13
first off thanks for the help Omnios, it is greatly appreciated!

i did exactly what they said to do in the last link you sent....i had my nomenclature correct in fstab (i think) but it still doesnt work...here is the line of my fstab i am working on.....

/dev/hdb1      /home/mike/public/shared ext3 defaults 0 0

---

### Post by aaarg on 2006-05-13
ok, it shows up in the disks app...but i still have to "activate" it...and it still fails to load the local file system module when i boot.

i know i am getting close, but something is still messed up

---

### Post by Omnios on 2006-05-13
Make shure " /home/mike/public/shared " exists. Also you are mounting to the home direcotry and there might be a problem with root trying to mount there but not shure. I have mounted window partitions there before but not ext3. ANother thing you might want to try is mounting the partition in media and create a link in /home/mike/public/shared to the media mount directory.

---

### Post by aaarg on 2006-05-13
ok, i changed fstab to /media/shared/ and when i pull up the disks manager it shows it active and mounted in the correct place but i still cant access it....

i made the directory, i changed ownership (followed what the link you sent said) and nothing.....

i can access my samba share on the root partition, but still not the new one...any more advice?

---

### Post by Omnios on 2006-05-13
Taken from the fstab in my signature.

 > [user and nouser These are very useful options. The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab./QUOTE]

[QUOTE][rw Mount the filesystem read-write. Again, using this option might cure the headache of many new Linux users who are tearing their hair off because they can't write to their floppies, Windows partitions, or something else./QUOTE]

[QUOTE]defaults Uses the default options that are rw, suid, dev, exec, auto, nouser, and async. I think this may be causing your problem not shure though.

 You might want to try this instead of defaults:: auto rw,auto,user,exec "0 0" not shure on the 0, 0 part though.

 ALso with the user part you should be able to mount it into a home direcotry but not 100% shure like I said I have only tryed this withvfat and ntfs

---

### Post by aaarg on 2006-05-13
alright, i am stupid...i forgot to change my samba conf to reflect the new /media/shared/....now i can access it *finally*, but i still have to manually mount it...

i am gonna change my fstab back to default and see what happens....

---

### Post by aaarg on 2006-05-13
well, i dont know what the deal is....it still fails to mount it automatically, but if i manually mount it it works...

thanks a ton for your help Omnios....it aint perfect but it works...if you were here i would buy you a beer...cheers for the help :)

i will keep trying to figure out how to mount it automagically

---

### Post by nanotube on 2006-05-13
hi aaarg,
can you please post here the contents of your fstab, and the output of the command
```
sudo fdisk -l
```
once we have that, we can make an exact fstab line for you to try, so that it automounts on boot.

---

### Post by aaarg on 2006-05-13
fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2385    19157481   83  Linux
/dev/hda2            2386        2491      851445    5  Extended
/dev/hda5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
254 heads, 63 sectors/track, 9767 cylinders
Units = cylinders of 16002 * 512 = 8193024 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9767    78145735+  a5  FreeBSD


fstab:
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/media/windows/ ntfs	nls=utf8,umask-0222 0	0
/dev/hda1	/media/windows/ vfat	iocharset=utf8,umask=000 0	0
/dev/hdb1       /media/shared/ ext3 auto defaults, 0 0

thx for the help!

---

### Post by nanotube on 2006-05-14
aha
well
according to that output of fdisk -l, your hdb1 is not formatted as ext3, but as a freebsd partition (ufs)
so, you would have to change your fstab line so that instead of ext3 it says something else. here is what it should look like:
```
/dev/hdb1 /media/shared/ ufs defaults,ufstype=44bsd 0 0
```

now, another point - your fstab appears to be mounting partition hda1 several times, as several different partition types. why is that? you should remove these lines from your fstab:
```
/dev/hda1 /media/windows/ ntfs nls=utf8,umask-0222 0 0
/dev/hda1 /media/windows/ vfat iocharset=utf8,umask=000 0 0
```

so, in total, your fstab should look like this:

```
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/shared/ ufs defaults,ufstype=44bsd 0 0
```

try that, and see if it works.
of course, just in case, back up your fstab before modifying it, so that you can easily restore it in case something goes wrong.

---

### Post by aaarg on 2006-05-14
nano...i dont know why it appears to be ufs...i formatted it yesterday with the disks as ext3 and it shows up as ext 3 in the disks manager....what could have caused that?

about the ntfs and fat mounts..i use a lot of external drives and i used a guide to make them automount when i plug them in

i will try to change to ufs and see what happens

---

### Post by aaarg on 2006-05-14
ok, i changed the fstab to ufs like you suggested....and nothing changed. i still have to manually mount it and then it works fine. any other suggestions?

---

### Post by nanotube on 2006-05-15
hmm, well, i notice that your hdb1 partition is set as "bootable", maybe that's what's causing it. try changing the line to :
```
/dev/hdb1 /media/shared/ ufs auto,defaults,ufstype=44bsd 0 0
```
(add explicitly the "auto" option), and see if that helps. if not, then also try
```
/dev/hdb1 /media/shared/ ext3 auto,defaults 0 0
```

hmm, also, check to see if directory /media/shared actually exists...

well, try those, and we will go from there.

---

### Post by jtech on 2006-05-15
**UPDATE:**
Secondary drive now mounts at boot. It just still isn't listed as a drive in computer:/// for some reason. 

I am having a very similar problem with my secondary drive. I can mount it and browse it using disk manager, but I can't for the life of me get it to show up in 'computer:///' and mount automatically. Here is my out put for fdisk -l

> Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4314    34652173+  83  Linux
/dev/sda2            4315        4500     1494045    5  Extended
/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
 
Here is my fstab file:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb1       /storage        ext3    defaults,errors=remount-ro 0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

I don't mean to interupt aaarg's post but perhaps this will help someone help us solve this together. Thank you very much in advance for any assistance!

-jtech

---

### Post by aaarg on 2006-05-15
[QUOTE=jtech]
I don't mean to interupt aaarg's post but perhaps this will help someone help us solve this together. Thank you very much in advance for any assistance!

-jtech[/QUOTE]

feel free to jump in......

nano: i will try those and see what we get

---

### Post by jtech on 2006-05-15
Thanks aaarg...I used this [http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+drive]("http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+drive") to get my drive mounting on boot. Maybe it will help you as well. However, I'm still not sure how to get the drive to show up in computer:///.

---

### Post by aaarg on 2006-05-15
well, it finally works...even computer:/// :) thanks a ton for the help yall!
jtech, i initially had my second drive set up with the errors=remount and such, but it wouldnt work for me....i dont know what to tell you...maybe nano can help?


here is my fstab:
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/windows/ ntfs nls=utf8,umask-0222 0 0
/dev/hda1 /media/windows/ vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/shared/ ext3 auto,defaults, 0 0

---

### Post by nanotube on 2006-05-15
[QUOTE=jtech]Thanks aaarg...I used this [http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+drive]("http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+drive") to get my drive mounting on boot. Maybe it will help you as well. However, I'm still not sure how to get the drive to show up in computer:///.[/QUOTE]
hey jtech,
it will only show up separately under "computer:///" if it is mounted under /media. so for example, in your case, you can mount it in /media/storage, rather than /storage.
otherwise, all the drives are simply incorporated into the overall "filesystem" at their appropriate mount points, and do not show up separately. 

as for automounting it, try adding the "auto" keyword to the options list, just like i suggested for aaarg.

and btw, aaarg, i'm glad it finally worked out for you. :)

---

### Post by gmcle454 on 2006-05-16
Thanks, that was just what i was looking for.

---

### Post by jtech on 2006-05-16
That did it for me. Thanks Nano!

-jtech

---

### Post by nanotube on 2006-05-16
[QUOTE=jtech]That did it for me. Thanks Nano!
[/QUOTE]
great, enjoy! :)

---

### Post by light50 on 2008-02-08
Thanks for this - it works a treat!

---

