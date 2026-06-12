---
title: "Migrate Ubuntu to another partition."
date: 2010-08-11
forum: General Help
---

### Post by SkulblakaSama on 2010-08-11
Greetings to all, 

It's me again, I wish to be a little more organized. I incidentally installed Ubuntu on the same partition as my main Windows 7. 

Is there a possible way to "migrate" this Ubuntu OS to another partition, keeping all of the settings. Also, would "migrating" the OS interfere with GRUB2? 

Thanks. :popcorn:

---

### Post by SkulblakaSama on 2010-08-11
Also, I could just reinstall Ubuntu, although it'd save the trouble by simply migrating, hopefully. If migrating isn't an option then I would need some advice on removing Ubuntu, ***with*** GRUB2

---

### Post by bodhi.zazen on 2010-08-11
You can move or copy the partition with several graphical tools including gparted , clonezilla, or similar live CD.

You can copy your partition with dd.

After moving or copying your partition you will need to update grub and /etc/fstab to boot the correct partition and set the proper partition to /

---

### Post by SkulblakaSama on 2010-08-11
> **bodhi.zazen said:**
> You can move or copy the partition with several graphical tools including gparted , clonezilla, or similar live CD.

You can copy your partition with dd.

After moving or copying your partition you will need to update grub and /etc/fstab to boot the correct partition and set the proper partition to /

Thank you, there are other posts related to my question. Although they didn't answer how to "update grub and /etc/fstab to boot the correct partition and set the proper partition". Can you tell me how to do that?

---

### Post by bodhi.zazen on 2010-08-12
How much do you know about grub and fstab ? How long do you want to spend learning ?

See this thread :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

It is quite old, but it should point you in the general direction.

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by SkulblakaSama on 2010-08-12
> **bodhi.zazen said:**
> How much do you know about grub and fstab ? How long do you want to spend learning ?

See this thread :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

It is quite old, but it should point you in the general direction.

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Those links show me what "fstab" and "GRUB2" are, not what I actually want to do. I'm new to Linux.

---

### Post by bodhi.zazen on 2010-08-12
> **SkulblakaSama said:**
> Those links show me what "fstab" and "GRUB2" are, not what I actually want to do. I'm new to Linux.

The first link shows you how to move a partition and update fstab and grub.

The second link is informational about fstab.

The third link is about grub2 as grub 2 is a little different from grub 1 which was used in the first post, which is old.

If you have a specific question, we can help. But honestly if you do not understand the documentation, I suggest you back up your data and re-install.

when you re-install I highly suggest you make a separate /home or a data partition so you may preserve your /home and your data if you re-install.

---

### Post by dino99 on 2010-08-12
if you want a clean install, which is easier than a migration, follow this little help:

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by SkulblakaSama on 2010-08-12
> **dino99 said:**
> if you want a clean install, which is easier than a migration, follow this little help:

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

I have a 10GB partition ready on ext4 format. So all I have to do is simply install Ubuntu into that partition. Then boot into Ubuntu, then run the terminal and run "sudo grub-mkconfig && update-grub" which will show me option to boot into Windows 7. Then I will be able to delete the old Ubuntu partition. Is that correct?

---

### Post by bodhi.zazen on 2010-08-12
> **SkulblakaSama said:**
> I have a 10GB partition ready on ext4 format. So all I have to do is simply install Ubuntu into that partition. Then boot into Ubuntu, then run the terminal and run "sudo grub-mkconfig && update-grub" which will show me option to boot into Windows 7. Then I will be able to delete the old Ubuntu partition. Is that correct?

You probably do not even need to do that.

boot the live CD, format the old Ubuntu partition and / or make any changes to your partitioning you want, and install into the new partition.

I doubt you will need to run any of those grub commands, just stay with the defaults when you install.

---

### Post by SkulblakaSama on 2010-08-12
> **bodhi.zazen said:**
> You probably do not even need to do that.

boot the live CD, format the old Ubuntu partition and / or make any changes to your partitioning you want, and install into the new partition.

I doubt you will need to run any of those grub commands, just stay with the defaults when you install.

Thanks, I also forgot to mention this. Like I said, I wanted to be organized, meaning my Ubuntu partition is installed into the same one as my main Windows 7 partition. Do I merely delete it?

---

### Post by bodhi.zazen on 2010-08-12
> **SkulblakaSama said:**
> Thanks, I also forgot to mention this. Like I said, I wanted to be organized, meaning my Ubuntu partition is installed into the same one as my main Windows 7 partition. Do I merely delete it?

Probably. Hard to know without more detailed information on your partitioning scheme and what you want to accomplish.

---

### Post by SkulblakaSama on 2010-08-12
> **bodhi.zazen said:**
> Probably. Hard to know without more detailed information on your partitioning scheme and what you want to accomplish.

My current Ubuntu OS is on the same partition as my Windows 7 OS. I want to delete that Ubuntu OS so that I can install the new Ubuntu OS onto the new partition. But what's stopping is GRUB2, I'm afraid that if I delete the original Ubuntu then I won't be able to boot since the bootloader is gone.

---

### Post by bodhi.zazen on 2010-08-12
> **SkulblakaSama said:**
> My current Ubuntu OS is on the same partition as my Windows 7 OS. I want to delete that Ubuntu OS so that I can install the new Ubuntu OS onto the new partition. But what's stopping is GRUB2, I'm afraid that if I delete the original Ubuntu then I won't be able to boot since the bootloader is gone.

Oh, I see now.

You did a wubi install and now wish to partition your hard drive and install Ubuntu.

By far and away the easiest it to :

1. Delete Ubuntu.

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

2. Install Ubuntu via a standard install. Grub will automatically be configured as part of the install.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Converting or migrating a wubi install is possible, but it is complex, even for experienced users.

If you are interested, see :

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by SkulblakaSama on 2010-08-12
> **bodhi.zazen said:**
> Oh, I see now.

You did a wubi install and now wish to partition your hard drive and install Ubuntu.

By far and away the easiest it to :

1. Delete Ubuntu.

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

2. Install Ubuntu via a standard install. Grub will automatically be configured as part of the install.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Converting or migrating a wubi install is possible, but it is complex, even for experienced users.

If you are interested, see :

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

I greatly appreciate your assistance.

---

### Post by bodhi.zazen on 2010-08-12
> **SkulblakaSama said:**
> I greatly appreciate your assistance.

You are most welcome. Don't worry, it gets much easier as you become familiar with how the OS works.

---

### Post by bcbc on 2010-08-13
It's possible to migrate a wubi install to partition and keep your settings and data: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

