---
title: "Windows 7, Wubi and a seperate Ubuntu partition?"
date: 2012-04-20
forum: General Help
---

### Post by jessabella on 2012-04-20
I was wondering if it is possible to have Windows 7 and Wubi installed and still be able to create a separate partition to test out other versions of Ubuntu. 

The reason for this is my HP Pavilion was very difficult to get Ubuntu installed correctly on and all drivers are not available. I would like to test out 10.04 again and also try 12.04 (with MATE).  I also am pretty sure a live CD  will not let you test graphics drivers since I am pretty sure you need to reboot after installing. Also ATM  I have the 32 bit version installed on a 64 bit laptop and would like to correct this if possible, by hopefully moving everything to the new partition later.

I did try out other versions of Linux and I was not happy with any but the familiar Ubuntu with Gnome 2.

Also  this laptop is mainly used by me but does not belong to me.  I do have permission to install what ever I want on it but because it is not fully mine I need to be very careful not to mess anything up when creating a partition. This laptop also did not come with a reinstall CD for Windows.

Given that, if there is a chance to create more problems I would rather leave things as they are and continue to use an unsupported version of Ubuntu.

There is always the option of doing a clean install of Wubi again but I would like to avoid that if I can since it was a real pain the first time around and I finally had to leave it as it was without updating drivers or Ubuntu would stop working completely.

---

### Post by jerome1232 on 2012-04-20
> **jessabella said:**
> I was wondering if it is possible to have Windows 7 and Wubi installed and still be able to create a separate partition to test out other versions of Ubuntu. 

The reason for this is my HP Pavilion was very difficult to get Ubuntu installed correctly on and all drivers are not available. I would like to test out 10.04 again and also try 12.04 (with MATE).  I also am pretty sure a live CD  will not let you test graphics drivers since I am pretty sure you need to reboot after installing. Also ATM  I have the 32 bit version installed on a 64 bit laptop and would like to correct this if possible, by hopefully moving everything to the new partition later.

I did try out other versions of Linux and I was not happy with any but the familiar Ubuntu with Gnome 2.

Also  this laptop is mainly used by me but does not belong to me.  I do have permission to install what ever I want on it but because it is not fully mine I need to be very careful not to mess anything up when creating a partition. This laptop also did not come with a reinstall CD for Windows.

Given that, if there is a chance to create more problems I would rather leave things as they are and continue to use an unsupported version of Ubuntu.

There is always the option of doing a clean install of Wubi again but I would like to avoid that if I can since it was a real pain the first time around and I finally had to leave it as it was without updating drivers or Ubuntu would stop working completely.

fyi 10.04 is supported to April of 2013, so it's still got a year of life left in it. What you want is possible, messing with partitions does always carry some inherit risk of failing and hosing your data in the process. I'm fairly certain Windows allows you to create a restore cd, you might want on in case you, for some reason, find your self in need to restore your mbr since if you install Ubuntu to a real partition it will put grub in.

Wubi isn't really that great for long term use anyways, I would try and migrate out to a real partition as soon as you feel comfortable doing so.

---

### Post by Mark Phelps on 2012-04-21
> **jessabella said:**
> Also  this laptop is mainly used by me but does not belong to me.  I do have permission to install what ever I want on it but because it is not fully mine I need to be very careful not to mess anything up when creating a partition. This laptop also did not come with a reinstall CD for Windows.

Given that, if there is a chance to create more problems I would rather leave things as they are and continue to use an unsupported version of Ubuntu.

Then basically, my advice would be to leave it alone.

Yeah, I know that's not the popular advice -- because folks here LOVE to experiment -- but if your experimenting breaks something, that becomes YOUR problem to fix.

Before you do ANYTHING else, use the Win7 Backup Feature to create and burn a Win7 Repair CD.  As least this way, if the Win7 boot loader does get corrupted, or the Win7 OS filesystem gets corrupted, you have something you can boot into to fix it.

And, if you do decide to go ahead with installing other Ubuntu versions, do NOT, repeat NOT, use the Ubuntu installer to shrink the Win7 OS partition.  Doing that runs the risk of corrupting the Win7 OS filesystem and rendering it unbootable.

Personally, my own feeling is that folks should experiment on their OWN machines -- and NOT on the machines of others.

But ... that's just my view.  You are entitled to your own.

---

### Post by oldfred on 2012-04-21
Another choice.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I have a full install of Ubuntu 12.04 in a 8GB partition on a 16GB flash drive, just to test on my laptop as it does not have a lot of room. My desktop has lots of room on several drives so there I have other installs also.

---

