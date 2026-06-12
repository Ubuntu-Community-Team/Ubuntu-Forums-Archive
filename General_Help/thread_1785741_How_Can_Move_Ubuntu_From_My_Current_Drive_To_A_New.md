---
title: "How Can Move Ubuntu From My Current Drive To A New Drive"
date: 2011-06-18
forum: General Help
---

### Post by CharleyGnarly on 2011-06-18
I have Ubuntu 11.04 on a hard drive that has Windows 7 as well. I just obtained  another hard drive and want to move Ubuntu and all of the contents therein to the new drive, so I can have one drive dedicated solely for Windows (for the family) and Ubuntu on the other.
The current drive is a SATA drive and the new is an IDE if that makes a difference.

---

### Post by prodigy_ on 2011-06-18
[http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk](http://wiki.linuxquestions.org/wiki/Dd#Clone_a_harddisk)

If you want something more user-friendly, try an app like [Clonezilla](http://www.clonezilla.org/).

---

### Post by CharleyGnarly on 2011-06-18
I changed the title of this thread from "How Can Move Ubuntu From My Current Drive To A New Drive" due to simplification... hopefully.
What I have done is deleted the install of Ubuntu 11.04 from my current hard drive and reclaimed all of the space for Windows 7.
I have another hard drive with Windows on it that I want to reformat and use solely for Ubuntu.
If I install the old drive and reformat it, then install Ubuntu, will it have the necessary settings to give me the option on boot up as to which hard drive/OS I start up?
A bonehead step-by-step would be great.

---

### Post by prodigy_ on 2011-06-19
You want to have both Windows and Ubuntu on the same PC but on different physical disks - am I correct?

If yes, you can easily clone your current Ubuntu installation to the new HDD if:
1) It's an actual (I mean non-Wubi) installation.
and
2) There's enough space on the new disk to make a partition of the same size as your current Ubuntu system partition.

Otherwise I'd suggest a clean install.

The cloning process is simple and [described step-by-step here](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/). Be careful with **dd** though - make sure you've got source and target partitions right.

---

### Post by CharleyGnarly on 2011-06-19
> **prodigy_ said:**
> You want to have both Windows and Ubuntu on the same PC but on different physical disks - am I correct?

If yes, you can easily clone your current Ubuntu installation to the new HDD if:
1) It's an actual (I mean non-Wubi) installation.
and
2) There's enough space on the new disk to make a partition of the same size as your current Ubuntu system partition.

Otherwise I'd suggest a clean install.

The cloning process is simple and [described step-by-step here]("http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/"). Be careful with **dd** though - make sure you've got source and target partitions right.

I have decided to go with a clean install. All I had done on Ubuntu was do updates and add a few programs, all of which took very little time. 
With that in mind, I will have my SATA drive that is currently in the computer with Windows 7 as it is right now. I want to install the new drive and install Ubuntu.
How do I do that? 
Forgive my lack of knowledge, but this is new territory for me.

---

### Post by wildmanne39 on 2011-06-19
> **CharleyGnarly said:**
> I have decided to go with a clean install. All I had done on Ubuntu was do updates and add a few programs, all of which took very little time. 
With that in mind, I will have my SATA drive that is currently in the computer with Windows 7 as it is right now. I want to install the new drive and install Ubuntu.
How do I do that? 
Forgive my lack of knowledge, but this is new territory for me.
Hi, I am going to give you a guide with good instructions for putting ububntu a second drive.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by CharleyGnarly on 2011-06-20
Here is a further update on my dilemma: I have decided to scrap the dual drive option and go with a larger hard drive. I will clone Windows to the new hard drive, then install Ubuntu like I had it before.
The dual drive thing looks entirely too complicated and risky for my current technical prowess (or lack thereof...:confused::()
Thanks for the tips, links and advice.

---

