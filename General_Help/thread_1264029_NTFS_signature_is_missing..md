---
title: "NTFS signature is missing."
date: 2009-09-11
forum: General Help
---

### Post by zitstif on 2009-09-11
My motherboard is an Asrock939 dualSATA2:

I'm trying to mount my RAID0 array via mount and ntfs-3g.

```
sudo dmraid -r
```
Yields:

```

/dev/sdc: pdc, "pdc_eagjbjhaja", stripe, ok, 145225472 sectors, data@ 0
/dev/sdb: pdc, "pdc_eagjbjhaja", stripe, ok, 145225472 sectors, data@ 0

```

```
sudo dmraid -ay
``` 

produces:

```
RAID set "pdc_eagjbjhaja" already active
```

```
sudo mount /dev/mapper/pdc_eagjbjhaja /media/WinXP/ -t ntfs -o nls-utf8,umask=0222
``` 

produces: 

```
NTFS signature is missing.
Failed to mount '/dev/mapper/pdc_eagjbjhaja': Invalid argument
The device '/dev/mapper/pdc_eagjbjhaja' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

Also might I note that there is nothing wrong with my RAID0 array, Windows XP SP3 boots up just fine.

I need to get this array mounted and use chntpw to clear my user account password because I can't remember it for the life of me.

I've also tried using kon-boot, but this does not seem to function.

Also, when I set up Windows XP PRO Sp3, I've locked down all the accounts, so there isn't an admin account or system account.

This is why I have resorted to attempting to mount the array in ubuntu.

Any tips or words of wisdom?

I know that I could just rebuild the RAID0 array and setup Windows XP on it again.. but I have XP setup quite nicely with a copious amount of software installed on it and would rather not reinstall XP, but if I have to I will.

---

### Post by zitstif on 2009-09-12
[bump]

Yeah this is quite annoying.. :D

---

### Post by NoaHall on 2009-09-12
I had this problem... I fixed it by using Konqueror instead of Nautilus, mount it, and remove the options/defaults you added.

---

### Post by zitstif on 2009-09-12
NoAHall, would you like to elaborate on your process a bit more? I don't see how using a different file manager/browser would be of any help. (No offense)

---

### Post by NoaHall on 2009-09-12
Well, if you changed your HD's settings via nautilus, Konqueror doesn't follow them, so it mounts it without the options. You can then delete them, so you can mount via nautilus again It works. Trust me.

---

### Post by zitstif on 2009-09-12
I haven't touched the settings of the HD Array via nautilus. I've been trying to do this from the command line in gnome-terminal. 

If you don't mind, would you like to recall what you did specifically?

---

### Post by NoaHall on 2009-09-12
I've told you. Here's the thread - [http://ubuntuforums.org/showthread.php?t=1259283](http://ubuntuforums.org/showthread.php?t=1259283)

Well, anyway, are you sure it's ntfs?
Have you messed around with /etc/fstab?

---

### Post by zitstif on 2009-09-12
Thank you for the words of wisdom.

I ended up getting kon-boot to work under Windows. I'm currently using Windows right now.. I know.. evil.. sry! :D

[http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/)

---

### Post by giyad on 2009-11-13
> **zitstif said:**
> Thank you for the words of wisdom.

I ended up getting kon-boot to work under Windows. I'm currently using Windows right now.. I know.. evil.. sry! :D

[http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/)
Hey ztistif did you ever figure out how to mount the RAID-0??  I'm having this same problem.  I want to mount my RAID in Ubuntu so I can access my shares on the network while using ubuntu, otherwise I cut everyone off in the house :-(

@NoaHall:

I wasn't able to get it to mount with Dolphin either, it doesn't show up there and actually my other NTFS drive (the windows installation) doesn't show up either.  In Nautilus the windows drive shows up fine as "150.0 GB Media" and I can mount it by just double clicking.

More info [here]("https://answers.launchpad.net/ubuntu/+source/dmraid/+question/89536")

---

### Post by zitstif on 2009-11-14
> Hey ztistif did you ever figure out how to mount the RAID-0??

I did not end up getting my raid 0 array to mount under Ubuntu 9.04. I think it's due to a hardware incompatibility issue.

I ended up mending my problem by going via a different route. (i.e. konboot.)

---

### Post by giyad on 2009-11-16
I got it to mount!

Kudos to mostlyharmless from the linuxquestions.org forums

[http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9.04-64-bit-769017/page2.html](http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9.04-64-bit-769017/page2.html)

---

### Post by zitstif on 2009-11-16
> sudo mkdir /dev/mapper/mountpoint

I don't think you'd want to make your mount point here though.. it's not very convenient. :p

---

