---
title: "Need help adding 2nd hard drive"
date: 2010-01-18
forum: General Help
---

### Post by BlueTeam on 2010-01-18
I've posted this on another site that seems to be much slower than ubuntuforums, so I'll try my luck here with the same post.

I've killed my 9.04 system by attempting to add a 2nd hard drive, 500 gb sata just like the main drive and could sure use some help getting it running again.

System boots through the bios screen, but beyond that I just get a blank screen with blinking cursor.


Here is what I did:
 
1) Followed (apparently not very well) the instructions from here:
   [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

2) used Gnome partition editor to format (as ext4, maybe a mistake not to use ext3?) as a single primary partition of the entire SATA 500 gb drive (same size as my main drive). My main (#1) drive is ext3 I think.
 
3) sudo mkdir /media/hd2
 
4) gksu gedit /etc/fstab 
           to add this to the end of fstab:  
      /dev/sdb1    /media/hd2   ext4    defaults     0        2

5) from terminal executed the following 3 commands so it would mount and be usable automatically:

         sudo chgrp plugdev /media/hd2
         sudo chmod g+w /media/hd2
         sudo chmod +t /media/hd2
 
6) verified new drive was available to me and that I could read and write from new drive (created a new folder and file on it, etc.).  So far, so good.  So I thought.
 
7) rebooted
 
8.  got blank screen with  blinking cursor after bios, and that is as far as it will go
 
9.) booted using ubuntu live cd, mounted main drive and played around with fstab trying a couple things to get it to boot again with no luck. Here are the things I tried:

a) change the new line in my fstab to 
        /dev/s**hd2**    /media/hd2   ext4    defaults     0       ** 0**
   
b) remove the new line in fstab, again no luck with reboot
 
10) So, here I sit with an inoperative Ubuntu system, and I am kindly asking help to get it to boot again. I'm guessing those three lines I executed in Step 5 above modified something that needs to be switched back, but I have no idea what.
 
11) Here is the current fstab contents. I've removed the line at the end that I added in step 4 (it's not in there now but won't boot either way), and blanked out the actual UUIDs.  Do I need to add a line with the UUID of the second drive to be like the other lines I see in there with UUIDs?  If so, where do I get the UUID, and what should that line look like?
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=00XX0000-0X00-000X-00XX-0XX000X00XX /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ZZZZZZZZ-0X00-000X-00XX-0XX000X00XX none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Thanks.

---

### Post by synapsys on 2010-01-18
It could be that your new hard drive is physically plugged into sata0 on the motherboard, therefore your bios is trying to boot from it instead of your primary. Have you checked out the bios boot order yet?

---

### Post by BlueTeam on 2010-01-18
> **synapsys said:**
> It could be that your new hard drive is physically plugged into sata0 on the motherboard, therefore your bios is trying to boot from it instead of your primary. Have you checked out the bios boot order yet?

No, I wasn't that smart.  :)  But when I did check it out, and after I did fix the problem there, it boots normally again, so thank you mightily.  I've got access to the new drive now, and everything seems good after a couple reboots.  Much obliged.

---

### Post by synapsys on 2010-01-18
Glad you got it working.

Be careful, adding hard drives can be addicting....

I started with 500 GB and I'm up to 3.5 TB......:D

---

### Post by pirateghost on 2010-01-18
> **synapsys said:**
> Glad you got it working.

Be careful, adding hard drives can be addicting....

I started with 500 GB and I'm up to 3.5 TB......:D


LOL.. i hear that.  i started many years ago with 10gb, thought i would never need any more than that...   now i have over 8TB usable space spread across 3 servers....if i had more space in my server rack, i would add a few more just for S's and G's

---

### Post by robertcoulson on 2010-01-18
Wow...It must be nice having all that money to spend on big drives (ha,ha)...Makes my dual boot 80gig look wimpish.
Bob

---

### Post by pirateghost on 2010-01-18
> **robertcoulson said:**
> Wow...It must be nice having all that money to spend on big drives (ha,ha)...Makes my dual boot 80gig look wimpish.
Bob
some people have hobbies (cars, fishing, rock-climbing, biking, etc), my computers are my work and my hobby and i like to think that if it werent for computers, i would just be spending all my money on drugs and hookers, the rest would just be wasted.

---

### Post by robertcoulson on 2010-01-18
True...very true....So far Ubuntu and my oldish computer have been good to me...Nice to see people who love computers that much.
Bob

---

