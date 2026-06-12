---
title: "My windows partition crashed. How do I reformatt it without wiping my Ubuntu?"
date: 2011-12-05
forum: General Help
---

### Post by gjacobs7191 on 2011-12-05
Hello everyone,

I have a Toshiba Satellite P755-s5269. It came with Windows 7. I partitioned the hard drive and installed Ubuntu 10.04 LTS on the new partition. Recently my Windows partition crashed. It says it is unable to read the C drive, displays nothing except for the trash and the favorites folder, and comes up with endless error boxes regarding system files. 

I have the recovery disks and want to fix my windows 7, but I don't want to damage the computer in the process. 

I am worried that when I reinstall windows, it will erase everything on my Ubuntu partition somehow, because I think that my Ubuntu is installed on an extended partition that is somehow connected to the Windows partition that I will be reformatting. Im not even 100% sure which partition is running Ubuntu and which was running windows.

 My Disk Utility app says that I have a 1.6 GB NTFS System partition. I also have a 433 GB NTFS partition labeled Tl106151W0F (which I think is the windows one). Then I have a 301 GB Extended partition which says its usage is "Container for Logical Partitions." Within that there is a 291 GB partition (usage: filesystem; partition type: Linux (0x83); Type: Ext4 (version 1.0)) and a 9.8 GB partition (usage: Swap Space; Partition Type: Linux swap (0x82)). Finally I have a 15 GB partition labeled HDD recovery. 

When I boot from the recovery environment disk and click on the toshiba recovery wizard, it asks me to insert the recovery disk 1 and then prompts me with a warning saying something like "You are about to reformatt Tl106151W0F. You will lose all data..." It never gives me an option of which partition to reformatt. The other option besides the Toshiba Recovery Wizard only sees the the 433 GB partition, which it says has Windows 7, and has a bunch of options, none of which are reformatting (one says system repair or something). 

So I guess my question is, can I just follow what the Toshiba Recover Wizard says? Will I lose the data on my Ubuntu partition if I do?

Thanks in advance,

-G

---

### Post by elliotn on 2011-12-05
use gparted

---

### Post by gjacobs7191 on 2011-12-05
Alright, I'll try that. Thanks.

---

### Post by gjacobs7191 on 2011-12-06
So i burned gparted-live-0.10.0-3.iso to a dvd as an image and booted from it. I ended up in some sort of gparted desktop with a partition manager window. Im not sure how to proceed. I can see my partitions, and the one that has the crashed windows on it. What do I do next?

There is an option to format the partition, but there are many different types of formatting that if asks me to choose from. Which one do I choose? When do I get to the point where I use the Windows 7 Recovery DVDs?

Thanks again,

G

---

### Post by N00b-un-2 on 2011-12-06
before you do anything rash, I'm assuming you have a factory recovery disk for Windows.  DO NOT USE IT!!!  If you must use your recovery disk to restore your computer, be aware that it is going to return your computer back to the configuration that it was in before you bought it, and that includes wiping your ubuntu partition.   I have been over this topic in depth before [here]("http://ubuntuforums.org/showpost.php?p=11091991&postcount=16")

back up. then (only if you have a commercial copy of Windows and not a recovery disk) partition, otherwise then run your recovery disk.  then partition with gparted or other software.  then reinstall ubuntu.  then restore your backups.

---

### Post by gjacobs7191 on 2011-12-06
Thanks! I burned the recovery DVD's myself (they don't give you recovery DVDs anymore apparently). But yes, they are just recovery DVDs, not a 'commercial copy' of windows. So in that case I'll just assume that everything will be wiped if I reinstall windows, and backup all my ubuntu data before doing so. 

Thanks again

-G

---

### Post by N00b-un-2 on 2011-12-06
make sure you follow the instructions in my link.  I spelled things out as clearly as possible.  Regardless of whether you have a manufacturer recovery disk or an actual copy of Windows, you need to install windows before Linux, or else you'll run into headaches reconfiguring GRUB.

1. back up your data
2. format and partition your hard drive
3. install Windows.  If you have a recovery disk, you can skip step 2 since the recovery isn't going to give you the option of installing to a partition.
4. install linux.

[http://ubuntuforums.org/showpost.php?p=11091991&postcount=16]("http://ubuntuforums.org/showpost.php?p=11091991&postcount=16")

---

### Post by Mark Phelps on 2011-12-06
BEFORE you take the drastic step of reinstalling everything, why not try the System Repair option that you mentioned in the original post?  You might have to run it three times -- but if it works, that will save you a lot of trouble.

---

### Post by gjacobs7191 on 2011-12-09
Thanks guys. I ended up checking out those other options and just did a system restore. I restored my Windows 7 to how it was a month and a half ago, before I got the AV Security virus that I think was responsible for my system crashing. Thanks again!

-G

---

