---
title: "Can't get win7 to load"
date: 2010-07-02
forum: General Help
---

### Post by shodlc373 on 2010-07-02
I apologize in advance for the long post... I can be somewhat  long-winded at times and I'd rather give a full account of the problem  so that hopefully somebody will be able to help me better. 

I've  always used windows as an OS but have been curious about Linux for a  while now, so after looking around online I decided to try ubuntu. I  have an Asus EEE PC netbook that came with win7 already installed on it.  Last night I downloaded the netbook edition of ubuntu via their  website, burned the .iso to a disc via my external dvd drive and then  ran the demo. I couldn't get it to boot off the disc when I rebooted, so  I had to pick the third option which I think installed some files to  the computer in order for me to be able, to run the demo. When it  finished that and I rebooted, the dual boot menu came up with both win7  and ubuntu on it. I messed around with ubuntu for a few hours before  deciding I wanted to keep it on my computer, so I ran the full  installation and selected the side-by-side installation. I remember when  the installer asked about the partitions. I wasn't sure what to do as I  wanted to keep both windows and ubuntu. There were three options: 1.  Install them side-by-side choosing at startup 2. Erase and use entire  disk 3. Specify partions manually (advanced). I wasn't sure how much  space to allocate ubuntu, so I chose the first option thinking that it  would just give me a default amount and would probably be plenty to  effectively use the OS. After installation, it asked if I wanted to  continue testing ubuntu or reboot and start using the full version. I  rebooted, and it gave me no option for windows 7. In addition to this,  the update manager came up and told me there were some 200 or so updates  available. This is always common with windows when you use it for the  first time, so I tried to update, and an error came up telling me that I  needed at least +500mb free space for the update and only had 400mb or  so. I'm a bit confused, and I've since tried rebooting several times,  but windows is still unavailable.

I guess what I'd like to know  is why win7 isn't listed in the GNU Grub at startup, and how I can fix  that. I would also like to know how I could go about getting more disk  space allocated to ubuntu. I thought about just uninstalling it, and  then reinstalling it and giving myself 10-20gb of space when asked about  the partitions again, but I obviously can't do that right now. The only  other thing that I could think of was doing a factory restore for my  netbook to get windows back, and then reinstalling ubuntu once again. I  wasn't sure that would work though and didn't want to take the chance  without getting the advice of somebody much smarter than me. I greatly  appreciate any help that anybody can give me. Thanks very much.

---

### Post by shodlc373 on 2010-07-03
I've gotten windows to load now, however I'm still stuck with the problem of having a very small partition for ubuntu. I was wondering if there was a way to just uninstall and then reinstall ubuntu. I tried to uninstall via windows and that didn't seem to do anything at all. I also tried to reinstall ubuntu again over the existing copy. I did the demo thing again and once I got into the demo I ran the full installation thinking that when I got to the partition part again, I could either give my existing ubuntu partition less space or give it more, and then do the opposite for the NEW ubuntu partition and use when I would use ubuntu I'd just load the one with the larger partition. This seems like a waste of available diskspace, but as it's only 2.5gb of a 160gb hard drive I'm not too worried about it, and nobody else has offered any advice yet. :(   It didn't work anyway, because when I got to the partition section of the installation, there was no longer an option to install side-by-side. Instead there was the option of using the entire 160gb hard drive, or to manually size the partitions. I started to do the latter, but I then realized I didn't know what I was doing and was afraid that if I continued I'd wreck my computer. Can somebody help me please?

---

### Post by Lucifer The Dark on 2010-07-03
gparted is what you need, you can use that to increase the size of your ubuntu partition, it's installed from synaptic but be warned it's really easy to screw your entire system using it so be careful.

---

### Post by howefield on 2010-07-03
If it were mine, the steps I'd be looking to take would be...

1. Defragment Windows.
2. Using Windows disk management tools, resize Windows to about 50 gigs.
3. Boot with Ubuntu Live CD, and using GParted from the System > Administration menu, create 3 partitions in the space vacated by windows, probably a 20 gig / partition, a couple of gig for /swap and the rest for /home.
4. Install Ubuntu using the manual options at the partitioning stage, to mount the previously created partitions / /home and /swap.

You may wish to view the following 3 short videos, which might clear a few points up for you, (and then ask any questions you might still have).

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)
[http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install](http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install)
[http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen](http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen)

---

### Post by Yarui on 2010-07-03
There is always a risk when using any kind of partitioning tool that something can go wrong, so be sure to back up anything you don't want to lose before trying to resize a partition.

What happened when you installed is that I think you have to drag the little bar that shows orange and blue to represent windows and Ubuntu when you select to install them side by side so that it knows what percentage you want to be allocated to Ubuntu.  You didn't realize that (as many people don't, I was confused by that menu the first time I used it), and left it default, which for some odd reason is generally just barely enough space to install the Ubuntu core files if you already have all of your disk allocated to one OS.

What I would do is just remove the Ubuntu partition using something like fdisk, and then try to install Ubuntu again.  That should give you the option again to install side by side and you can be sure to drag the bar this time.  Using utilities like gparted and fdisk can be a little intimidating if it's your first time, but they are very simple tools, if you read a bit about how they work before you do anything, you should be fine.

---

### Post by Yarui on 2010-07-03
> **howefield said:**
> If it were mine, the steps I'd be looking to take would be...

1. Defragment Windows.
2. Using Windows disk management tools, resize Windows to about 50 gigs.
3. Boot with Ubuntu Live CD, and using GParted from the System > Administration menu, create 3 partitions in the space vacated by windows, probably a 20 gig / partition, a couple of gig for /swap and the rest for /home.
4. Install Ubuntu using the manual options at the partitioning stage, to mount the previously created partitions / /home and /swap.

You may wish to view the following 3 short videos, which might clear a few points up for you, (and then ask any questions you might still have).

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)
[http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install](http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install)
[http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen](http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen)
If you have had your hard drive very full, it's true that defragmenting windows before resizing the partition could be a smart move.

---

### Post by Mark Phelps on 2010-07-03
Make sure, whatever you do, that you pay careful attention to item 2. from Howefield, as below:

> 2. Using Windows disk management tools, resize Windows to about 50 gigs.

If you choose the side-by-side option of the Ubuntu installer and let IT shrink the Win7 partition, you are most likely to end up with a corrupted Win7 boot loader, and it won't start anymore.

So, as Howefield said, youse the Win7 Disk Management utility to do the partition shrinkage.

---

