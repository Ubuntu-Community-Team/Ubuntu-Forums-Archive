---
title: "Install Windows 7 but keep Ubuntu"
date: 2011-11-25
forum: General Help
---

### Post by shawnubu on 2011-11-25
Hi all,

Moderator: Feel free to move if warranted
I am running Ubuntu 11.10 on a desktop computer. I need to also run Win 7. However, I *think* I accidentally deleted my Win 7 data when installing Ubuntu. Is there any way to install Win 7 but keep Ubuntu so that I can dual boot the two? I have a 7 installation CD (no Ubuntu Live CD), flash drives, an external HD, and free time. Let me know if you need any additional info - Thank you so much for the help and I hope you had a great Thanksgiving!

Ubuntu Experience: 1 1/2 years, but still on beginner level
Here is a screenshot of Gparted:

[IMG]http://i40.tinypic.com/2ro6r1y.jpg[/IMG]

---

### Post by Miljet on 2011-11-25
Yes, it looks like you wiped your Win install. There are a couple of ways to add Win 7, but you are going to need a Ubuntu Live CD, or Live USB, in either case. Anytime you install Windows after Ubuntu is already installed, Windows will overwrite the MBR (Master Boot Record) and you will lose GRUB. Then you will need a Ubuntu installation media to restore GRUB to the MBR.

If it was me, I would simply back up personal files, use Gparted to set up your partitions, reinstall Windows and then reinstall Ubuntu. If you choose this route, it would be a good idea to expand the extended partition and install Ubuntu on a logical partition inside the extended one.

Here is a link to one of the best guides to dual booting I have found.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by BC59 on 2011-11-25
The easiest way for me:

Make a backup of your personal files and remove them from the computer.

Install the application Remastersys.

Execute Remastersys from the dash and follow the instructions to backup your entire system (it's the first option).

Remastersys makes an installable clone of your system. So burn the .iso file produced (you find it in File System-->Home) and make a live CD (actually you will need a DVD). Boot with this Live CD to see if it's working.

If you are sure that you have your system in the DVD, install Win 7 by formatting the entire disk.

Then from the working Win7 go to partitions and resize the main partition to leave about 40G space for Ubuntu.

After that install Ubuntu from your personal Live CD. You will have the same system intact, like before and a dual boot Win7.

---

### Post by mastablasta on 2011-11-25
have a look here (Install windows after Ubuntu section): [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
and here is how to recover grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

