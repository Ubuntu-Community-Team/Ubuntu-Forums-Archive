---
title: "Dual booting"
date: 2009-09-03
forum: General Help
---

### Post by Capt. Blackwood on 2009-09-03
Ok, part of me wants to dual-boot windows xp and Ubuntu. I'm a gamer, web designer, and every now and then i mix audio.
 
 
I've got a 500GB hard disk and i'd like to know what is an ideal partition size...besides splitting the drive in two. I'm also fairly certain windows will not be able to see the Ubuntu drive and vice versa (correct me if i'm wrong)
 
 
I would like to use Ubuntu as the whole thing with Virtual box utilizing my primary hardware, or some other method of switching operating systems without rebooting.

---

### Post by MoonRocketZero on 2009-09-03
I haven't done so for a long time but you can access your Linux drive from Windows and Windows drive from Linux (I'll leave detailed instructions to others, who have can explain the steps to you better, as I said it's been a while since I played around with doing that - I am not expert at Ubuntu)

As for partition size I guess that really depends on what your going to be doing in each OS - largest partition for the most used OS and a smaller one for the less used OS (you can always resize them later if necessary) 

I personally only have a 30gb partition for Windows (use it only for gaming, don't need to acces file from that partition when in Linux) 

I run the work Windows programs I need in either wine (if they will run - which most don't a few do) or in vituralbox which works just great! - just not for games - but I can run all the Adobe CS3 programs, and other progs I must use and they all work well enough :) )

But if you want to game with newer games you will NEED to keep a separate Windows partition, and boot to it for that.

If it wasn't for games I would be totally switched I think.

---

### Post by Katalog on 2009-09-03
> **Capt. Blackwood said:**
> I'm also fairly certain windows will not be able to see the Ubuntu drive and vice versa (correct me if i'm wrong).

If you decide to dual boot, Ubuntu will certainly be able to see your Windows partition, but  Windows doesn't natively have the ability to read ext3/ext4 file systems. It may show you a partition with an "unknown" file system, but you won't be able to read or write to it. I believe there are some utilities or other tricks out there to get this functionality, but it won't do so out of the box.

If you really don't want to reboot to use one or the other, then I would say that the aforementioned VirtualBox would probably be the way to go. Just create an expandable virtual hard drive (vdi) for the OS so that it will only take up as much space as it needs and then grow if necessary later on if and when you add more applications and files.

---

### Post by habskilla on 2009-09-03
Here's something else to think of instead of dual bootings but still having windows and Ubuntu available at all times.  If installing non open source programs is issue for you then ignore this post.  Also, being a gamer, I don't think this will work out for you 100%, but it's a free idea  :)

Use VMware vCenter Converter Standalone and convert your existing windows into a vitual machine.

Install Ubuntu.
Install VMware server
Run your windows vm inside Ubuntu.

If you're box has enough horse power, you'll won't even notice you're running windows in a VM session.

---

### Post by MoonRocketZero on 2009-09-03
> **Katalog said:**
> If you decide to dual boot, Ubuntu will certainly be able to see your Windows partition, but  Windows doesn't natively have the ability to read ext3/ext4 file systems. It may show you a partition with an "unknown" file system, but you won't be able to read or write to it. I believe there are some utilities or other tricks out there to get this functionality, but it won't do so out of the box....
Yes I know for a fact I had to get a app for windows to allow me to see ext3 partitions (and I have no idea if you can access ext4 or not never tried that, as I said it's been a while)

Think I paid for the program I played around with to access ext3, but I just googled this [http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/) which looks promising (I'm going to down load it and give it try - not that I need it but stil want to see what it does)

---

### Post by Capt. Blackwood on 2009-09-03
> **Katalog said:**
> If you decide to dual boot, Ubuntu will certainly be able to see your Windows partition, but Windows doesn't natively have the ability to read ext3/ext4 file systems. It may show you a partition with an "unknown" file system, but you won't be able to read or write to it. I believe there are some utilities or other tricks out there to get this functionality, but it won't do so out of the box.
 
If you really don't want to reboot to use one or the other, then I would say that the aforementioned VirtualBox would probably be the way to go. Just create an expandable virtual hard drive (vdi) for the OS so that it will only take up as much space as it needs and then grow if necessary later on if and when you add more applications and files.
 
I'm thinking about doing that.
 
 
I know i do need to set aside 120GB for media (My zune's that big)
 
 
Using ubuntu's gettin my brain clickin, and it can't stop. You know a week ago windows was getting on my damn nervs. I had to wait for it to finish loading just to get the overclocking software to run...here it's BAM! I have to type it manually (if you know a way to do this automatically please tell me, i'm clocking through nvclock) but hell. I can do that FASTER!

---

