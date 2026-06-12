---
title: "Hard drive switch"
date: 2010-05-24
forum: General Help
---

### Post by mattsweegold on 2010-05-24
Hey everybody, I am currently using a Compaq SR1750NX [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00572530](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00572530), but recently I have have been given an Intel rig [http://www.amazon.com/Dell-processor-Bluray-ROM-supporting-Graphics/dp/B002GK0AI4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1274743174&sr=8-2](http://www.amazon.com/Dell-processor-Bluray-ROM-supporting-Graphics/dp/B002GK0AI4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1274743174&sr=8-2) that has a damaged hard drive. I was wondering though not only how to perform a hard drive switch but also
[LIST]
[*]Do I need to worry about the sata 1 technolagy being implemented into a device designed to run on a sata 2.
[*]Will there be any significant speed loss in most application if sata 1 is used over sata 2.
[*]Do I need any special cables to complete the transfer.
[*]Do I need to re-download Ubuntu since I am switching from AMD to Intel.
[/LIST]
Thanks in advance

---

### Post by BoneKracker on 2010-05-24
SATA-I drives are compatible with SATA-II controllers and vice-versa.  If one of the two components are SATA-I, then the speed will be limited to half of what it would be if both components were SATA-II.

Here's a good explanation:
[http://forums.overclockers.co.uk/showthread.php?t=17504457](http://forums.overclockers.co.uk/showthread.php?t=17504457)

However, hard drives are increasingly cheap.  If you can afford it, you ought to just buy a new one for the new computer.  Then, your old computer is still functional to be used as something else (give it away, build a router/firewall out of it, build a server out of it, etc.).

Unless the two computers are precisely the same architecture, you really ought to reinstall the OS on the new computer, not simply pop the disk in and try to boot up (although that might very well work).  So, you'd want to back up all your personal files and any system files (e.g. configuration files) which you invested a lot of time in editing.

Then, put the drive in the new computer, boot up, and visit the BIOS setup page to make sure the drive is properly accounted for and that other settings are appropriate.  Save settings and exit.

Then, just boot from the CD appropriate to the architecture, and proceed as you normally would to install the OS.  After installation, replace the files you backed up.

---

### Post by Bobhuber on 2010-05-24
> **mattsweegold said:**
> Hey everybody, I am currently using a Compaq SR1750NX [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00572530](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00572530), but recently I have have been given an Intel rig [http://www.amazon.com/Dell-processor-Bluray-ROM-supporting-Graphics/dp/B002GK0AI4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1274743174&sr=8-2](http://www.amazon.com/Dell-processor-Bluray-ROM-supporting-Graphics/dp/B002GK0AI4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1274743174&sr=8-2) that has a damaged hard drive. I was wondering though not only how to perform a hard drive switch but also
[LIST]
[*]Do I need to worry about the sata 1 technolagy being implemented into a device designed to run on a sata 2.
[*]Will there be any significant speed loss in most application if sata 1 is used over sata 2.
[*]Do I need any special cables to complete the transfer.
[*]Do I need to re-download Ubuntu since I am switching from AMD to Intel.
[/LIST]
Thanks in advance
The drive should work fine in the system. Unless you just like to deal with problems I would highly recommend reinstalling the software.

---

