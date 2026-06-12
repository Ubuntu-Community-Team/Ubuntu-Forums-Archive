---
title: "complete removal of vista"
date: 2011-08-14
forum: General Help
---

### Post by fidelandche on 2011-08-14
Hi all,

I have a Toshiba Satellite L300 with 160GB HD dual booting 11.04 and  Vista. I have now got VB working to run the two programmes I only need windows for. So my HD has 90GB for Vista and the rest is for 11.04, what is the best way to remove Vista and leave the HD free for Ubuntu only? Do I just back everything up to an external HD and reinstall?? (But I have a few problems get some things to work) So not sure if this is the right option for me or is there another way? 

Cheers

Andy

---

### Post by Elfy on 2011-08-14
I'd boot the livecd/usb or whatever you have. 

Fire up gparted from the sys admin menu - remove the vista partition. 

I would then create a partition and use it for data, mounted through fstab. 

You could if you wanted to resize your existing / or /home partition if you had one of those seperately.

Certainly no need to reinstall. 

IF you do go for resizing then make sure you have backups just in case.

EDIT - if you do decide to resize you will need to turn off swap I suspect to allow it - just guessing that swap and the / are in an extended partition.

Also - once you have deleted the vista partition and have rebooted, run ```
sudo update-grub
``` to remove it from the boot list.

---

### Post by Mark Phelps on 2011-08-14
If you want to have Win7 backed up in case you DO need it again in the future, then do the following:
1) Download and install the free version of Macrium Reflect
2) Use the option in MR to create the Linux Boot CD
3) Image off the Win7 partitions (there are likely to be two of then, a small one and a large one).

Then, if you need it back later, you have a means of restoring it.

Also, if you DO image off using MR, you have no more need for a Recovery partition, so you can remove that and reclaim the space.

---

### Post by Elfy on 2011-08-14
I assume that works for the vista the OP has :)

Long time since I've looked at windows software so most of it is new to me now - hence the question.

---

### Post by fidelandche on 2011-08-14
Well, I have no idea on what I did but I completely messed my system up!! everything just stopped and I could not get the terminal to open or try to start from safe mode, but thank the stars I had backed everything up before hand. So not matter what I did, I just could not get my system to restart, so in the end I had to reinstall 11.04 and all is well.

Cheers for the replys.

---

