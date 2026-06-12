---
title: "A small but annoying problem and ideas?"
date: 2010-06-24
forum: General Help
---

### Post by ironhoof on 2010-06-24
We have Ubuntu/Kubuntu installed on all our home computers.

The one with Kubuntu (There are two computers with it)

I installed a second hard drive for another family member on it just for internal storage NO other OS on this machine just Linux no FAT file systems because I formatted it ext4 so you can rule that out right away. I read something about that while looking for a solution.

It works fine but now when she starts up Kubuntu says "Kdesudo - Please enter your password to use this device."

She doesn't mind entering a password when she needs to do something but she really doesn't like entering any passwords at startup and I am probably going to hear about it until I get it fixed... She's new to Linux so I want to make sure it keeps a good impression on her.

-Cheers

---

### Post by Chame_Wizard on 2010-06-24
Strange,the last time I had the same problem was 2 years ago.

kdesudo is needed when you want to be the root,to do  something important on the system(graphical,you are the root for 15 minutes).

When you are in Dolphin just click on the device,it will access to the device immediately without problem.

Do you use 10.04 or 9.10?

---

### Post by ironhoof on 2010-06-26
10.04 I download all the Ubuntu varients at the same time they are all 10.04

It works the device fine actually even if you cancel the password window. Just need the password window to go away.

---

### Post by ironhoof on 2010-06-26
Oh yea and it only appears at initial boot. I already used chkrootkit and there is no problems. I did add a user to the VirtualBox group would that do it?

---

### Post by Don Barzini on 2010-06-26
> **ironhoof said:**
> It works fine but now when she starts up Kubuntu says "Kdesudo - Please enter your password to use this device."

She doesn't mind entering a password when she needs to do something but she really doesn't like entering any passwords at startup and I am probably going to hear about it until I get it fixed... She's new to Linux so I want to make sure it keeps a good impression on her.

-Cheers

Post a copy of your **/etc/fstab** file.

---

### Post by ironhoof on 2010-06-26
Here you are as requested:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

Thats all that was in it.

---

### Post by Digger78 on 2010-07-13
How did you determine  which device was asking for the password? or are you just assuming its its the new drive?

I upgraded from 9.10 to 10.04 at the weekend and now I have the same "problem" as you at each boot.

I have not added any new hardware.

Just started looking into it, will post back when i find a solution .

My password prompt is for a small ext3 partition that i forgot about, didn't have an entry in fstab.

I created a mount point and added an entry to fstab, the partition is now automounted  at boot and is usable  BUT I still get that annoying prompt for an unneeded password.

I have read a few posts here and there but they were all about ntfs partitions and adding an entry to fstab sorted the problem.

Edit: I got rid of that annoying password prompt.
------------------------------------
system setting >advanced>removable devices  

CHECK - enable automatic mounting of removable media
CHECK - automatically mount removable media when attached

NO checks in the device overrides 

apply and reboot
-----------------------------------

If your drives don't mount at boot, create mount points and add fstab entries

sudo mount -a      (will  mount all entries from fstab)

---

### Post by ironhoof on 2010-07-15
You might be on to something. I already had the options just as you mention in Removable media so I couldn't do that. I didn't see anything in the list that wasn't mounted. I seen a lot of devices like our pen drives not mounted (but not inserted too).

I am still trying to figure out what changed..

---

### Post by ironhoof on 2010-07-27
Ok, I fixed it. Here is what ahppened so if someone else has the problem. In the settings -> advanced -> removable devices

There is was checkmark on automount on login. Click this OFF. Then tell it to forget the device.

I did not see the password window AGAIN. Plus you can still access the drive via Dolphin.

All is good now.

---

### Post by ironhoof on 2010-07-27
Oooo forgot to mention the automount on login was on the second hard-drive. =P sorry. Yea anyway click the automount on login off your second hard-drive and tell it to forget it.

---

### Post by Digger78 on 2010-07-27
Do your CD/DVDs automount?

I have found it to be a bit of hit and miss, sometimes it mounts, sometimes it doesn't.

I installed halevt which has resulted in more automounts but still fails at times. (dirve is ok, works in XP)

I really do wish optical devices were still handled by fstab :(

---

### Post by ironhoof on 2010-07-29
Yes, everything on her computer auto mounts. Its the second hard drive. I made it forget it. It still shows up in dolphin and if she clicks on it. The password box shows back up after reboot/shutdown. You have to tell it to forget it again.

I consider this solved as I know how to take care of it. It would be nice though if she could use it without kdesudo showing up. Its not a big deal though.

Cheers

---

### Post by mayeulk on 2010-11-07
> **ironhoof said:**
>  In the settings -> advanced -> removable devices

There is was checkmark on automount on login. Click this OFF. Then tell it to forget the device.


Thanks, it solved the problem for me too!

---

### Post by pjoshyjosh on 2011-08-24
After putting up with this issue for far too long, I found this thread.  You guys found where to fix the problem - but so that others can see I will add more info.

The top boxes were checked as mentioned (Enable - and Automatically Mount).

Problem was that the devices had check boxes in the "Automount at Login" - which was overriding the settings on top of the page.  I unchecked the boxes for the devices - hit apply and no more password requirement.

Yes - optical drive seems to work

---

