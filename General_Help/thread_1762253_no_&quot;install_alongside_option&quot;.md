---
title: "no &quot;install alongside option&quot;?"
date: 2011-05-19
forum: General Help
---

### Post by soylentcola on 2011-05-19
So, I'm having a bit of trouble reinstalling Ubuntu 11.04 alongside my Windows 7. I had it installed previously and because I had troubles accessing my Windows 7 drive from Ubuntu.  I think I uninstalled properly as I uninstalled Ubuntu through Windows (in my Add/Remove Programs) and then formatted the old partitions and extended them back into the original OS drive using EASEUS Partition Manager.

I can boot fine into Windows now without problems, but now that I'm trying to reinstall Ubuntu 11.04 as a dual boot, there is no longer an option to "install Ubuntu alongside Windows 7", just two options (Install Ubuntu over Windows 7) and "Something Else..." I've read around and found that you can use "Something Else..." to install it as well, but it looks way too advanced and I'm rather green in terms of Ubuntu.   I even reformatted my USB stick and redid the whole process of creating the Ubuntu install again, but nothing happened.  My main question is, where did the option go, and what can I do to get it back?

---

### Post by soylentcola on 2011-05-19
Also, in case this is needed (ran "sudo parted -l")

I also read that Ubuntu cannot install on an NTFS drive? So perhaps that is the problem?

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs         boot


Model: Kingston DataTraveler2.0 (scsi)
Disk /dev/sdb: 1999MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1991MB  1990MB  primary  fat32        boot, lba


Model: Apple iPod (scsi)
Disk /dev/sdc: 7971MB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      258kB  7971MB  7971MB  primary

---

### Post by Quackers on 2011-05-19
You are not getting the "alongside" option because your hard drive is completely filled with the Windows partition and therefore there is no space for Ubuntu to install in to.

A good first move is to create a Windows 7 repair disc if you don't already have one (or a installation disc - a recovery dvd is not the same!)
To make one go to Control Panel > Backup & Restore Center then in the left pane clcik on "make a recovery cd" and put a cd in the drive. It takes about a minute or so to make the disc.
This disc can be used to repair Windows if something goes wrong. You may need that!

In Windows 7 you should then defragment the C: drive. Twice would be better.
Then go to Disk Management console and right-click on your C: drive and select "shrink". 
A new box will open up telling you how much (in MB) you can shrink the C: drive by. You can select less than the figure shown if you want, but not more.
When you have made that decision click on OK and the shrinkage will take place.
It should not take very long. When it is complete you will see the area of the C: drive reduce in size.

Important!!!   You should now reboot Windows 7 twice!! to make sure it's happy with the resize. It can be funny like that :-)

This change has now given you some unallocated space to install Ubuntu into.
When you now boot from the Ubuntu Live cd/usb you should see the "install alongside" option.

---

### Post by soylentcola on 2011-05-19
Ah, I see. Going to try this now and see how it goes. If anything I'll post back in the thread and let you know what (if any) problems I encounter! :D

---

### Post by soylentcola on 2011-05-19
Oh, before I get into this, does it matter which program I use to defragment the drive? I have CCleaner installed and use that to manage my system and all the defragging and cleaning...would that suffice or should I use the Windows Defragmenter instead? Or does it not really matter?

---

### Post by Sonicrulz12 on 2011-05-19
nope doesnt really matter:D

---

### Post by Quackers on 2011-05-19
I wasn't aware that CCleaner did defragging. The truth is that I'm not sure. I would advise for something as important as this to use the Windows defragmenter, but that will take some time. 
At other times I use Auslogics Disk Defragmenter, but not just before I shrink the C: partition.

---

### Post by soylentcola on 2011-05-19
Oh, my apologies, CCleaner does registry cleaning, Defraggler (obviously that should've given it away) does Defragging, but I'll use the Windoze one just to be safe.

---

### Post by Quackers on 2011-05-19
It's possibly safer, but definitely much slower :-(
Have a sleep then :-)

---

### Post by soylentcola on 2011-05-19
Marking this as closed, as of 6:39PM EST, I've successfully dual-booted Ubuntu 11.04 alongside Windows 7 with no problems, thanks a lot guys! :)

---

### Post by Quackers on 2011-05-19
Nice one :-)

---

