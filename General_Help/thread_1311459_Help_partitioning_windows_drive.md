---
title: "Help partitioning windows drive"
date: 2009-11-02
forum: General Help
---

### Post by dixie460 on 2009-11-02
Howdy all, I have two 160GB hard drives that i would like to use, one to put Ubuntu 9.1 on, the other for storage/file backup. These are in an old Gateway Win XP machine. One appears to have no operating system on it, it's probably full of old Windows XP backup files, if anything. The other one has a corrupted copy of Win XP Home on it, that someone tried to reinstall over...when the installer hung up and quit, they gave the whole computer to me. I can get harware information later on when I get home, but for now let me explain my problem...
 
when I try to run the Ubuntu installer from the Live CD, it works fine until the Partitioner gets to 5%, then it hangs up solid. I tried this on both drives, and I tried to install after booting into Ubuntu from the CD (clicked on Try Ubuntu with no changes to this computer) as well as just running the cd and selecting Install Ubuntu.
 
Do I need to format these to FAT32 first, before running the installer?
 
Regards,
Andy

---

### Post by ajgreeny on 2009-11-02
You don't need to actually format the drives to anything first, but is probably worth running the ubuntu live CD, going to System > Administration > Partition Editor and checking what that can find, and perhaps deleting those partitions it sees by right clicking and choosing "delete".

Then try installing again.

Perhaps the partitions are corrupt and are stopping the installer from doing the partitioning properly.

---

### Post by ezsit on 2009-11-02
Couple of questions.

1. Are the hard drives PATA or SATA? 
2. If PATA, are they jumpered correctly? 
3. If SATA, are they connected to SATA ports controlled by a RAID?
4. How are the SATA ports set in the BIOS, to IDE mode, or other type of config?

Once you have got the drives and ports figured out, we can get to other possible causes for problems.

---

### Post by dixie460 on 2009-11-02
They are IDE drives, I think also known as ATA?

I have the jumper removed per the decal on the top, that shows no jumpers needed for "Single or Master". I only had one drive plugged in at a time.

I don't have a RAID setup and I don't see an option in my BIOS to set any port to be a RAID port. If it matters any, they worked fine when Windows was installed. Apparently Win suddenly quit working one day, and dude tried to run the installer and it also failed to run, it kicked him to the famous blue screen of death about halfway through.

Per the label: Western Digital WD1600 Enhanced IDE hard drive. 

thanks for the help

Regards,
Andy

---

### Post by peculiar penguin on 2009-11-02
Download WD's diagnostic software ("Data Lifeguard Diagnostic for DOS (CD)" is the bootable LiveCD-like version) and run both the quick and extended tests to make sure the drives aren't toast.

---

### Post by dixie460 on 2009-11-02
Ok, I will do that!! Thank you for the help, I'll get back to yall. I'm also fighting to get my 19" LCD to work, so between those two things, I'm pullin my hair out lol.

---

### Post by dixie460 on 2009-11-06
Yep, I think both drives are toast. Oh well

Regards,

Andy

---

