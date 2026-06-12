---
title: "Need serious help resizing."
date: 2012-09-04
forum: General Help
---

### Post by lemonoid on 2012-09-04
Okay so I need help using GParted to make WAY more space for my current 12.04 32-bit install. I just recently installed the other day because I just got this computer back up and running. I had Windows and two Mint installations, and my end game was my dad's Windows with maybe an extra 15GB of space for him, and the rest of it for my 12.04 and a little Swap. What I have here is the screenshot of my current situation. So I would like to allocate around 18GB of space from Windows to Ubuntu, and take all of the rest of the free space to the right and add it to my Ubuntu except my Swap. I'm thinking I may need more swap too because this is an older PC with low RAM, and I need as much RAM as possible because this will be my main machine for compiling Android. I was hoping by including this screenshot someone could help me figure out how to reallocate this space, because as I'm syncing my Android source, I realized that my free space is terribly low. I did not realize how bad my space situation was until now. I probably won't be able to stay up much longer and take care of it, but I wanted to go ahead and post my situation so I could get as much feedback as possible before tomorrow morning. I thought I would be able to do this by myself, but I am not being given the option to edit any of these partitions, only the option to make a new partition. Thank you for your feedback and sorry for any ignorance. I have never had an issue with space and partitioning until I've gotten this PC back up and running because I've had to do a lot of installing/removing of OS's. By the way, in case you just don't notice, everything after dev/sda2 is Ubuntu/free space. And I need 18gb from sda2.

---

### Post by lemonoid on 2012-09-04
bump

---

### Post by Mark Phelps on 2012-09-04
To get the space from sda2, do NOT, repeat, NOT use GParted.  That runs the risk of corrupting Win7 and rendering it unbootable.  Instead, boot into Win7 and use the Disk Management utility to shrink it -- but don't be surprised if it won't let you shrink it by 20GB.  If you use something else (like GParted) to shrink it more, as said earlier, you run the risk of corrupting Win7.

Also, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy, should you need to repair the Win7 boot loader or the Win7 filesystem.

---

### Post by lemonoid on 2012-09-04
> **Mark Phelps said:**
> To get the space from sda2, do NOT, repeat, NOT use GParted.  That runs the risk of corrupting Win7 and rendering it unbootable.  Instead, boot into Win7 and use the Disk Management utility to shrink it -- but don't be surprised if it won't let you shrink it by 20GB.  If you use something else (like GParted) to shrink it more, as said earlier, you run the risk of corrupting Win7.

Also, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in handy, should you need to repair the Win7 boot loader or the Win7 filesystem.


Well I can wait to pull the 20GB from Win7 if I can get that other space to the right of my linux system (in the picture) to allocate to my Ubuntu. because that adds up to around I think like 37GB. But I don't know how. Can I just delete those partitions and then resize my Ubuntu? (except for swap)

---

### Post by plucky on 2012-09-04
Why do you need to pull 20Gb from Win 7?

You already have two large un-allocated spaces.

I would delete the install on the sda5 partition, then resize the Ubuntu partition until you reach the swap partition,and then use the unallocated space that is left for the second mint install.

Make sure you are booting from your Ubuntu partition before deleting the install on sda5,or you could end up being unable to boot any system.

You need to use the Live CD/USB to resize the Ubuntu partition,and make sure you turn off swap.

Once the resize is complete,you could put the second install of mint on the second un-allocated space which is sitting behind the swap partition.

Good Luck

---

### Post by lemonoid on 2012-09-04
> **plucky said:**
> Why do you need to pull 20Gb from Win 7?

You already have two large un-allocated spaces.

I would delete the install on the sda5 partition, then resize the Ubuntu partition until you reach the swap partition,and then use the unallocated space that is left for the second mint install.

Make sure you are booting from your Ubuntu partition before deleting the install on sda5,or you could end up being unable to boot any system.

You need to use the Live CD/USB to resize the Ubuntu partition,and make sure you turn off swap.

Once the resize is complete,you could put the second install of mint on the second un-allocated space which is sitting behind the swap partition.

Good Luck

I don't actually need the Mint install. And if I can grab all that unallocated space plus that which is on sda5, I won't need the 20GB from Win. It just happened that when I started fixing this PC, there was Win7 and Mint, I couldn't remember my Mint passwd so I installed a second Mint OS, and I asked someone on those forums if I could just delete the first one once I was on the second installation, they said yes, I did, and it did break my boot. But luckily I have Boot Repair on DVD I was able to fix my MBR. As far as what you said about deleting sda5, I can just open up GParted and delete that right now right? It won't have any effect on my MBR or anything? And you said I need to be booted from Live CD/USB to resize my Ubuntu with that unallocated space? I just pop in my USB, boot into live, open GParted and stretch it up to the edge of swap? And how do I make sure swap is turned off while in Live mode? Sorry for so many questions. As I stated before I've never had to do anything special regarding partitioning. I used to have the option of just replacing any Linux distribution with my current install, and for some reason lately I've not had that option, only the one to add on.

---

### Post by plucky on 2012-09-05
> As far as what you said about deleting sda5, I can just open up GParted and delete that right now right? 

Yes as long as it doesn't Have the **key** symbol next to it,as that means it is mounted and locked.

> It won't have any effect on my MBR or anything?

Not as long as your default boot is from the last install.

 > I just pop in my USB, boot into live, open GParted and stretch it up to the edge of swap? 

Yes,after you turn off swap,as gparted won't let you manipulate the extended partition if any of the other partitions are mounted within it.

To turn off swap,select the partition in Gparted and right click on it and there should be an option to turn swap off.


> I used to have the option of just replacing any Linux distribution with my current install, and for some reason lately I've not had that option, only the one to add on. 


I think that was changed in later distributions as some people were wiping out there current installations when trying to triple boot.It seem to default to using un-allocated space now.

Good Luck

---

### Post by lemonoid on 2012-09-05
> **plucky said:**
> Yes as long as it doesn't Have the **key** symbol next to it,as that means it is mounted and locked.

I think I'm going to have to boot into live Ubuntu to do all of this, including deleting /dev/sda5. When I tried to delete it now, it told me to Please unmount any logical partitions having a higher number than 5. This is impossible because the installation in which I am currently using, my Ubuntu, is /dev/sda7, and my swap is dev/sda6 which is ok but like I said, I'm using sda7 right now. So am I correct that I need to boot into live to do all of this, since while I'm booted live, sda7 won't be mounted?

---

### Post by plucky on 2012-09-06
> So am I correct that I need to boot into live to do all of this, since while I'm booted live, sda7 won't be mounted? 

You are correct.

Because your / partition is within the extended partition,you will not be allowed to manipulate any partition when booted to /sda7.Boot the Live USB and **turn swap off** and you should be able to manipulate all the partitions.

Good Luck

---

