---
title: "Hard disk problems: Previous Windows Vista and Ubuntu 9.10 partitions"
date: 2010-07-19
forum: General Help
---

### Post by z0e7u1s0 on 2010-07-19
Hello,
        I have some trouble with my hard disk and I may have made some simple or possibly large mistakes.  I am currently running the livecd of Ubuntu 9.04 to access the internet, but I had previously installed partitions of Windows Vista and Ubuntu 9.10.  A few days ago, my computer froze in Windows Vista, and I made a stupid mistake of shutting my computer off manually.  When I tried to start it, every time I attempted to access the Windows OS from Grub, it started Startup Repair, and it would not work.  I then used a pair of Recovery Disks to reformat the Windows partition and reinstall factory conditions.  The reformatting always went through, but reinstalling always stopped short and froze.  I booted up the Ubuntu 9.04 livecd, and tried to use Gparted to just format the entire disk and install Ubuntu 9.04.  Now there is an input/output on  error when I try to install.  I should also add that when I tried to use Gparted to format the entire drive, I cancelled the operation while it was in the process and instead decided to do it using the install program.  Now the entire disk shows up empty, and Gparted will not recognize any partition except free space.  I simply wish to clear the entire drive and install Ubuntu 9.04 off the live cd, and then upgrade to Ubuntu 9.10.  I can supply any hardware or software information needed for help, and any help would be greatly appreciated. I'm not in the position to purchase a new computer, so any way I can make this work would be great. Thanks for any help.

---

### Post by MatthewPlanchard on 2010-07-19
Hey z0e7u1s0

First, what happens if you try to install Ubuntu straight from the LiveCD, instructing it to use the entire disk?

---

### Post by z0e7u1s0 on 2010-07-20
It gives a display message of  Input/Output Error during read on /dev/sda and then a message stating the creation of swap space in partition #5 of SCSIl(0,0,0)(sda) failed.  I also did a hard disk test from the HP setup when the computer first booted up and the test status reported to replace the hard disk.  Do I need to replace it, or is there a way to erase the hard drive without making the disk unusable?

---

### Post by LeeDaugherty on 2010-07-20
Is this a laptop by any chance?  The recovery partitions don't like the default partitions resized and gparted usually breaks partition type 72.  And just for the fun of it I got to ask....why install 9.04 and then upgrade?  That's alot of installing and upgrading.

---

### Post by z0e7u1s0 on 2010-07-20
This is a laptop, but the reason is because I only have a 9.04 livecd available, I never made a 9.10 livecd.  Is there a way to wipe the entire hard drive and then install ubuntu on it?

---

### Post by MatthewPlanchard on 2010-07-20
When you're setting up your install, how are you setting it up?  

Try doing a manual partition during setup.

Make sure to select "format" for every partition you create, and I'd recommend the following:

20 GB partition mounted as "/"
3 GB partition as "swap"
The rest of your space mounted as "/home"

Try formatting the / and /home partitions as ext3, and the swap partition as swap, and let us know if you still receive an error message.

---

### Post by z0e7u1s0 on 2010-07-21
Attempted it, and received the same error message.  Thank you for the help though. Any suggestions?

---

### Post by MatthewPlanchard on 2010-07-21
The next step I'd  try is completely and totally wiping the hard drive, using the instructions found here:

[How to Securely Wipe Your PC's Hard Drive]("http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/")

However, if there are any other suggestions, you should probably try those first, as this is completely and totally irreversible.

If you decide to wipe it, do so, and then try a fresh install of Ubuntu or Windows.

---

### Post by z0e7u1s0 on 2010-07-23
Thank you for the suggestion. I'm currently borrowing a 80 GB SATA hard drive from a friend to run, and am in the market for a 1 TB drive since this problem.  I'm going to use that advice to try and fix the hard drive.  Thank you for all your help, and if this fixes it, I'll post again to help others with this problem.  Again, thank you both for your help.

---

