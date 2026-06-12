---
title: "Ubuntu stopped !!"
date: 2010-04-24
forum: General Help
---

### Post by ankit.vader on 2010-04-24
IAM IN BIG PROBLEM, i had ubuntu 9.10 which was running fine. I tried to install fedora but apprently fedora CD was corrupt and the installation stopped halfway. As a result ( or may be for other reason) ubuntu stopped working. I do not have windows. 
        Now the problem is when i try to install ubuntu from LIVE CD its not working. May be there is a problem in my CD-drive and i have no clue how to install from USB. Can anyone guide me...
       I have to come to cafe to access internet and send this post. Please Please Please **HELP:confused:**

---

### Post by akand074 on 2010-04-24
Its hard to help with such little information, what is not working? What is the error message? Is it loading into the Live cd? What is happening.

---

### Post by 2hot6ft2 on 2010-04-24
If you use ext4 for the file system in ubuntu then install another distro. they may not be able to see ubuntu because they can't read the ext4 file system so they wont add ubuntu to the boot loader they install (if you let them install one).

*********
[B]If you already tried to install ubuntu over your ubuntu
[/B]
Boot the livecd and open
System > Administration > GParted
Right click on the swap partition and select swapoff
And right click on anything else with locks on it and select unmount.
Then you can try running the installer again.

***********
**If you didn't already try installing ubuntu again over the one that was already there you could fix grub like this.**

Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if you don't have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

---

### Post by ankit.vader on 2010-04-24
Thanks [2hot6ft2]("http://ubuntuforums.org/member.php?u=568708") .......grub installed successfully ...thank you very much:)

---

