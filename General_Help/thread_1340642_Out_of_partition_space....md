---
title: "Out of partition space..."
date: 2009-11-28
forum: General Help
---

### Post by DarkSunrize on 2009-11-28
Ok so I installed Ubuntu 9.04 today. I burned the .iso image to a CD off of my dad's computer and installed on my mom's laptop. I first ran Ubuntu in the "demo" mode and then ran the install from in there. When it got to asking me about the partition i let it do the default and now after using it for like 3 hours i am completely out of partition space. What can i do to increase the partition space or create more room for myself? (please be specific im a noob...)

It is to the point where i cant even put anything on my desktop because i have no space left and i have created no files or anything.

---

### Post by DarkSunrize on 2009-11-28
can someone please help me?

---

### Post by ed-koala on 2009-11-28
Open a terminal and type **df -h** and post the output here please.

---

### Post by DarkSunrize on 2009-11-28
Output of df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 462M     0  462M   0% /lib/init/rw
varrun                462M  108K  462M   1% /var/run
varlock               462M     0  462M   0% /var/lock
udev                  462M  148K  462M   1% /dev
tmpfs                 462M  1.2M  461M   1% /dev/shm
lrm                   462M  2.7M  460M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  368K  656K  36% /tmp


as i said the partition has no space available

---

### Post by ed-koala on 2009-11-28
Your partition is rather small, only 2.3 gig.  How big is your hard drive?

Assuming you have some extra space elsewhere, you can boot a live CD and use gparted to resize the partition.  Be warned this can take hours for a large hard drive!

---

### Post by DarkSunrize on 2009-11-28
Ok i have a hard drive with 201.2 Gigs of free space left. Will u give me a step by step and tell me how to do Gparted please??

---

### Post by fluffman86 on 2009-11-28
This is a known bug with 9.04, with a few workarounds:

1)  Reinstall, this time using 9.10.  The bug should not be present there, but make sure that you give yourself enough free space: The base install requires at least about 4 GB.  I recommend at least 10 if you plan to add any programs and actually do anything, 20 if you want to rip/burn DVDs, make music CDs, or have any files of any decent sizes.

2)  If for some reason 9.10 doesn't work on your machine while 9.04 did (shouldn't happen, but it's possible), then reinstall with 9.04 and follow the same instructions above.

3)  If you don't want to reinstall, you can resize your partitions, but this will take almost as long.  Boot from the live CD, go to System > Administration > Partition Editor (Or Gparted).  Right-click and click resize to shrink your NTFS (windows) partition, and do the same for Ubuntu, this time growing it to fill the freed space.  Then Apply your changes.

To make sure you get the most available space, and to make the process *safer* and quicker, I highly, highly, *HIGHLY* recommend:
a. running CCleaner in Windows
b. running Start > Programs > Accessories > System Tools > Disk Cleanup in Windows
and c. running Start > Programs > Accessories > System Tools > Disk Defragmenter

Finally, if you're going to reinstall, I recommend following the general instructions here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

And more particularly here (ONLY if you have 30 or 40GB MINIMUM to spare):
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

With a few exceptions:
1. Use ext4 instead of ext3 in the above instructions.
2. make "/" at least 10GB, and make the rest (at least another 20 GB minimum) for /home
3. your swap partition should be 1 GB.

Keep us posted as to what you do, and don't hesitate to ask more questions!

---

### Post by DarkSunrize on 2009-11-28
Hey thank u but here are my issues. 9.10 will not work for me bc im running a AMD x64 processor not an intel so i cant re- install that. My second issue is that i can not keep windows open but for like 10 min. That is the reason i installed ubuntu. Im thinking about just using the partition editor because i have been reading and alot of people have problems getting GRUB to work if they re-install. So is there anything i should avoid doing or a new solution now that u have more insight?

---

### Post by ed-koala on 2009-11-28
Sure.  First, you can't do this if you are using the partition, i.e. you can't resize the Ubuntu partition when you are booted into it.  So, it's best to use the Live CD for this.  If you don't have one, step one is download and burn one (burn it at slow speed to make a good copy).

Boot from the CD.  Choose Try Ubuntu without any changes to your system (even though we are gonna make some changes).

Once up and running, go to System - Administration - GParted

Find the partition you want to make larger, right click and choose resize. Make it whatever size you like, say 20 gig? That's up to you.

Wait while gparted works.  This will take awhile.  Go read a book, watch some TV.  Check back from time to time.  When it's done, restart your pc, taking out the CD when told to do so.

Enjoy your new space.

---

### Post by DarkSunrize on 2009-11-28
ok thank u soo much!!! Just one last question about the BIOS on my computer. I have an HP laptop and when i startup it says i can "change the boot order" or "enter SETUP" so which one do i select? Last time i did this i was able to start the boot from windows. Thanks u sooooo much!!!

---

### Post by fluffman86 on 2009-11-28
> **DarkSunrize said:**
> Hey thank u but here are my issues. 9.10 will not work for me bc im running a AMD x64 processor not an intel so i cant re- install that. My second issue is that i can not keep windows open but for like 10 min. That is the reason i installed ubuntu. Im thinking about just using the partition editor because i have been reading and alot of people have problems getting GRUB to work if they re-install. So is there anything i should avoid doing or a new solution now that u have more insight?

Editing with gparted won't be a problem.  But you certainly *CAN* install 9.10 on just about *ANY* processor.  For any x64 (amd64 or intel core2's, etc.), just select the x64 version of 9.10.  Or you can even install the 32bit version on a computer with a 64bit processor, doesn't matter.

---

### Post by DarkSunrize on 2009-11-28
> **fluffman86 said:**
> Editing with gparted won't be a problem.  But you certainly *CAN* install 9.10 on just about *ANY* processor.  For any x64 (amd64 or intel core2's, etc.), just select the x64 version of 9.10.  Or you can even install the 32bit version on a computer with a 64bit processor, doesn't matter.

Oh rly? I did not know that... Ok well i will consider doing that sometime but for now im gonna stick with this... I rly dont feel like waiting another hour and half to burn a Live CD for 9.10 plus i dont feel like pushing my like tonight. I gotta b in a room playing call of duty in an hour. So thank u!!!!

---

