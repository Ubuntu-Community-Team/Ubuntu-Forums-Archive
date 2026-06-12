---
title: "Frozen during upgrade from 10.10 to 11.04"
date: 2011-05-29
forum: General Help
---

### Post by Lash009 on 2011-05-29
Hello, I run Ubuntu (10.10) from a flash drive on my Dell computer. Yesterday when I tried to upgrade it to 11.04 After downloading a lot of files, and then installing most of them, my computer froze.
When I restarted my computer, It went straight to booting Windows XP. I didn't get a GRUB screen at all.
So somehow GRUB and Ubuntu got screwed up, and I'm wondering if there's anyway I could salvage what I have (I know I can use a Live CD to get my files off of there). So is there any way I could avoid having to do a clean install? Could I possibly salvage the files which upgrade to 11.04?
Any advise/ideas are appreciated (I'm kinda a Linux noob). I'll try to check this thread as often as I can today and tomorrow.
Thanks   -Matt

---

### Post by ajgreeny on 2011-05-29
Try the boot-info-script link in my signature; follow the instructions, and then copy the RESULTS.txt file back here in code tags, the # icon in the toolbar above.  That will give us a lot of info about the OSs on disk and grub's setup.

---

### Post by Lash009 on 2011-05-29
Ok, I ran that. I'm going to cut the results file into 3 parts so I can upload it onto here.
There is a sector (on sdb5 and 7) that still has the 9.04 Kernel on there, but that is not the problem. They are lingering there from a failed install (faulty hardware).
My Ubuntu Boot thing is on sdc:
```
sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

--------------------------------------------------------------------------------------------------------------------------------
Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    29,861,887    29,859,840  83 Linux
/dev/sdc2          29,863,934    31,264,767     1,400,834   5 Extended
/dev/sdc5          29,863,936    31,264,767     1,400,832  82 Linux swap / Solaris  
```

I'm not really sure what else to put up, so I'll attach 3 files with the results on here.
I also noticed that when I had both the liveCD and my normal booting flash drive in at the same time it will go to GRUB. So I'm going to try to see if I can do anything with that.

---

### Post by Lash009 on 2011-05-29
So, I kinda fixed my problem, but not really. I booted with both the Live disk and flash drive in there. I tried to start Ubuntu how I normally would, failed, tried the repair thingy for that kernel version. It quickly gave me a bunch of words, among which I caught "kernel panic". Then I tried to boot from "Previous Linux versions" went to the first one, and it booted up Ubuntu 11.04 in all it's.... weirdness.
Hopefully that information can help you to help me. and by the way, thanks for taking the time to help a noob like me \\:D/ You're awesome (somthing that sets Linux users apart from the people I see on Windows help forums).

---

