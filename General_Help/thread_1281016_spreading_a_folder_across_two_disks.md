---
title: "spreading a folder across two disks?"
date: 2009-10-02
forum: General Help
---

### Post by tetsuoharry on 2009-10-02
as per title, is this possible?

I ask as I have added a smaller disk to my existing system and I don't really want to format and raid them.

Harry

---

### Post by BraedenNaylor on 2009-10-02
i know of no way to do this unless done manually or with raid. could you explain what kind of folder it is / what is in it / its primary purpose

---

### Post by tetsuoharry on 2009-10-02
its my home folder that I wanted to spread over the disks, I guess I want a jbod type scenario.

---

### Post by jward3010 on 2009-10-02
Does LVM do this kind of thing, or am I talking crap.

If the answer is yes, you might need the alternate CD to get this result. But the answer is yet to be answered as yes and indeed until that juncture, please ignore my words of ignorance, or wisdom. One does not know yet.

---

### Post by Chronon on 2009-10-02
> **jward3010 said:**
> Does LVM do this kind of thing, or am I talking crap.

If the answer is yes, you might need the alternate CD to get this result. But the answer is yet to be answered as yes and indeed until that juncture, please ignore my words of ignorance, or wisdom. One does not know yet.

Yes, logical volumes can be expanded across multiple physical disks.  It needs to already be a logical partition to do this, though.

---

### Post by sailthesea on 2009-10-02
IF you mounted the new drive in /home it could be viewed as a seperate folder (I think) and simply used as as such How to do it the way you want is a little beyond me though!

---

### Post by jward3010 on 2009-10-03
> **Chronon said:**
> Yes, logical volumes can be expanded across multiple physical disks.  It needs to already be a logical partition to do this, though.
If the new drive is made a logical partition (One large extended partition) can they be joined up without a reinstall, using some special magic within GParted?

---

### Post by badger_fruit on 2009-10-03
To the person who mentioned LVM - yes, this is how the OP would perform the task.
For example I have two 1TB hard-drives for my media collection and the two disks are in a single LVM group ("media").

"df Media" says 2TB

I can now add additional disks to this group and increase the size on the fly.
I am sorry but this is not something I have ever done in Ubuntu, but in Suse you will need to have some head-ache tablets on stand by!!

The process is something like this:-
1. Create an LVM group and give it a name and mount-point
2. Add disks to the group
3. Increase size of LVM to max (to use all the space - you don't HAVE to use all the space, but for simplicity, I do)

Beware that your disk will be formatted when you add it to the group.

For me, to migrate from a single 1TB to a 2TB LVM, all I did was leave my 1TB ("Disk 1") alone, created the LVM group but added "Disk 2" into it first.

I then formatted it to LVM and then when done, moved all the data from "Disk 1" to "Disk 2".  From there, I simply added "Disk 1" into the LVM group - formatted it and no data was lost, yay.

I will also say [B][SIZE=5][COLOR=Red]BE CAREFUL WHEN YOU ARE USING PARTITION EDITORS, ALWAYS, ALWAYS ALWAYS DOUBLE, NO, TRIPLE CHECK WHAT ACTIONS WILL BE DONE BEFORE CONFIRMING THEM![/COLOR][/SIZE]

[/B]One day, I forgot to re-read the actions to perform and accidentally formatted my 2TB LVM, oops.

---

### Post by jward3010 on 2009-10-03
Cheers for the feedback on LVM, I thought it was the right thing but wasn't 100%. I also know little about setting up LVM although always interested in experimenting. What did you use to perform LVM tasks, alternate disk or was it another Linux distro altogether, I notice some are more featured than others at install time.

---

### Post by badger_fruit on 2009-10-04
> **jward3010 said:**
> Cheers for the feedback on LVM, I thought it was the right thing but wasn't 100%. I also know little about setting up LVM although always interested in experimenting. What did you use to perform LVM tasks, alternate disk or was it another Linux distro altogether, I notice some are more featured than others at install time.

My LVMs (I have two now) were both done under Open Suse 11.0 & yast; they both at the moment comprise of two (physical) disks each:-

LVM 1 - 750GB & 1TB 
LVM 2 - 1TB & 1TB

Opensuse has LVM built in so no need for additional packages.
At the moment, I don't have any Ubuntu LVM experience although my MythTV disk (a mere 160gb) is running very low on space so I might need to LVM that and a spare 80gb I have lying around ... with the new 2TB disks coming into play and the 1TBs being so cheap right now I may even invest in another 1TB ... although with christmas just around the corner I don't think the wife wants more disk spare so it may have to wait lol!

---

### Post by jward3010 on 2009-10-05
If we we're to do LVM within Ubuntu what would we need? GParted doesn't seem to handle LVM. I'd love to mess around, I have a few 250GB S-ATA drives sitting in my machine doing nothing.

---

