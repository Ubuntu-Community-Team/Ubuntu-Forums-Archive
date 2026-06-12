---
title: "booting dell recovery partition from grub"
date: 2009-08-17
forum: General Help
---

### Post by juicymixx on 2009-08-17
So, I recently purchased a new Dell inspiron laptop which came with Vista.   One of the first things I did after receiving the computer was to shrink the vista partition down using gparted, and install Ubuntu.   The HD in this laptop is 500MB, which I shrunk (and moved left) leaving about 75 GB of space for Ubuntu (the gpartd procedure took an absurd 10 hours to complete, then Vista took another hour 'repairing' itself).   I partitioned the Linux so that I have a separate /home, /, and swap.   The Ubuntu install went flawlessly, as I've come to expect.

I then set about modifying Vista to suit my needs. While customizing dll files I managed to b0rk the system.   Well, fine.   It was a new setup, and I hadn't done much, so I figured in the worst case scenario I would just reformat the Vista partition and reinstall it.   However, I did want to try to recover if I could... I tried various recovery and fixing methods, but none of them worked.   Then I remembered that while I was partitioning using gparted that there was a Dell RECOVERY partition, as well as another 'hidden' partition, at the front of the disk.

The normal Dell method to boot from the recovery partition is to hold down CTRL+F11 on bootup.   My guess is that some part of the Vista loader notices this and kicks you over to the RECOVERY partition to bootup.   Well, since I had installed Ubuntu and was using grub to dual boot this option didn't appear available.   I ended up booting off the Dell recovery CD and getting to the command prompt using the included recovery tools, then running the PCRestore program on the RECOVERY partition (after setting the path correctly).

Now that everything is back to 'normal', I was wondering what entry I need to make to the GRUB's menu.lst to have an option to boot to the RECOVERY partition?   According to [http://www.goodells.net/dellrestore/vista.htm](http://www.goodells.net/dellrestore/vista.htm) the RECOVERY partition is the Vista Recovery Environment.   Should I make an entry (in menu.lst) similiar to the Vista chainloader entry?

A little bit of searching brought me to this:
[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)
which I haven't tried yet.   Does anyone have experience with the GRUB and booting the RECOVERY partition/tools?  :confused:

Thanks.

---

### Post by juicymixx on 2009-08-23
Well I still haven't tried this yet since I'm busy working on other systems, but I'm surprised that I haven't gotten a response.   
I figure there must be a bunch of Dell and HP laptops out there dual booting Vista and Ubuntu (college students and professionals), and both companies use RECOVERY partitions, so...   
Am I posting this question in the wrong section?:confused::P

---

### Post by lanebrain65 on 2009-11-15
bump

---

### Post by Mark Phelps on 2009-11-15
The reason that there have been no responses to the original question is because --- it can't be done!

All that the GRUB variants do for MS Windows OS's is select a partition and then hand off control to an MS Windows boot loader in that partition.

If, in the case of a Dell recovery partition, there is no MS Windows boot loader present, the machine will not then boot.

The Dell recovery CD (I'm guessing) contains Windows RE -- which can boot on its own.  So, it needs no additional MS Windows boot loader in order to utilize the Dell recovery partition.

---

### Post by Lateralis on 2009-11-15
My Fujitsu Siemens laptop comes with a recovery partition at the front of the disc.  When I installed Ubuntu a few months back onto this hard drive, it recognised this partiton and *did* add an entry into menu.lst for this recovery partition.  I know this because after my first reboot post installing Ubuntu, I had two Windows entries and the first one took me into the recovery partition.  If I hadn't have been careful, I would have hosed the whole hard drive!  

My menu.lst file looks like this:

```

title Windows Vista (loader)
rootnoverify (hd0,0)             <--- Vista recovery partition
savedefault
makeactive
chainloader +1

title Windows Vista (loader)   
rootnoverify (hd0,1)             <---- Vista system partition
savedefault
makeactive
chainloader +1

```

Looks pretty innocuous, but the first partition is a preinstalled recovery partition.  

I guess what I'm trying to say is that on some systems and with some setups, you can boot to a recovery partition with grub.

---

