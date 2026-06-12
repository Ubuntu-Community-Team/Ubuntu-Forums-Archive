---
title: "Moving to 64 bit"
date: 2011-01-06
forum: General Help
---

### Post by CJ_Hudson on 2011-01-06
Hi,
I just tried the pae kernal fix to try and recognise all my loverly RAM but it didn't work. Still only 3.1 GB RAm out of the 4 physically installed.

I tried uninstallling the pae kernal but it's still there.
I now want to try 64 bit Ubuntu and have a couple of questions:

1) I am running Natty Narwhal. Please, will I have to do a clean install to get 64 bit Ubuntu up and running?
2) Will the modified pae kernal cause any complications if I am 'upgrading' to 9.10 64 bit?

Yours in ignorance.:confused:

---

### Post by oldfred on 2011-01-06
To change from 32bit to 64bit you have to do a full reinstall. Do you have a separate /home? If not now would be a good time to create one. You can also export a list of installed apps to make it easy to reinstall.

Why would you install Natty. It is Alpha and has regular breakages. if you have a spare 20GB you can install it into that, but I would not install it as your working system.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
 dpkg --get-selections > ubuntu-files

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by SquishyOctopus on 2011-01-06
> **oldfred said:**
> To change from 32bit to 64bit you have to do a full reinstall. Do you have a separate /home? If not now would be a good time to create one. You can also export a list of installed apps to make it easy to reinstall.

Why would you install Natty. It is Alpha and has regular breakages. if you have a spare 20GB you can install it into that, but I would not install it as your working system.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
 dpkg --get-selections > ubuntu-files

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

I couldn't have said it better myself.  :)

---

### Post by CJ_Hudson on 2011-01-07
Thankyou very much for the advice and tips.
I don't know how I ended up with Natty Narwal, I thought I had Mavaerick Meerkat installed.  (?!)

I haven't installed many apps but I built my wireless adapter for my wireless card myself, it took a book from the library on Linux Ubuntu, much online help and 6 months of my spare time.

Please, final question, will the 64 bit version set up my wireless automatically or will I have to go through all that again?
Final final question, can I roll back the Narwal installlation back to Meerkat if I decide not to go through with the 64 bit install?
Your assistance is greatly appreciated.

---

### Post by mikewhatever on 2011-01-07
> **MogBug said:**
> ...

Please, final question, will the 64 bit version set up my wireless automatically or will I have to go through all that again?
Final final question, can I roll back the Narwal installlation back to Meerkat if I decide not to go through with the 64 bit install?
Your assistance is greatly appreciated.

If wireless didn't work out of the box with 32bit, it's unlikely to do so with 64. Hopefully it won't take six months this time.

There are no roll back or downgrade features of any kind in Ubuntu.

---

### Post by wojox on 2011-01-07
> **MogBug said:**
> 
I don't know how I ended up with Natty Narwal, I thought I had Mavaerick Meerkat installed.

You may have a bug. Run this in the terminal:

```
cat /etc/lsb-release
```

---

### Post by oldfred on 2011-01-07
You may not then have Natty as there seems to be a bug in the display of version.

These commands tell more about system.

32 or 64 bit
uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit
Version or DISTRIB:
cat /etc/*release
fred@fred-LucidDT:~$ cat /etc/X11/default-display-manager

There is no way to go back. I always install in a new 20GB root partition and keep my old one for a while.

---

### Post by dcstar on 2011-01-07
> **wojox said:**
> You may have a bug. Run this in the terminal:

```
cat /etc/lsb-release
```

The bug that mistakenly reports 11.04 for 10.10 systems?, isn't that fixed **yet**?

---

### Post by wojox on 2011-01-07
> **dcstar said:**
> The bug that mistakenly reports 11.04 for 10.10 systems?, isn't that fixed **yet**?

Someone wrote a patch [In Maverick 'About Ubuntu' displays Natty info]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248"), but I guess it hasn't been released?

---

### Post by CJ_Hudson on 2011-01-07
No, you are correct, it incorrectly reports 11.04 in ->System --> About Ubuntu, but in -> System --> Administration ---> System Monitor (System tab) it correctly reports Maverick.

However I am bemused because at the top of the boot menu is still: 10.10-2.6.35-24-generic-pae .
Why does it still boot to this kernal when I have uninstalled it according to the exact instructions in the [Wiki]("https://help.ubuntu.com/community/EnablingPAE"), where it claimed it would revert back to the pre-pae kernal?

---

### Post by wojox on 2011-01-07
What do you have installed?

```
dpkg --list | grep linux-image
```

---

### Post by wojox on 2011-01-07
Also did you run

```
sudo update-grub
```

---

### Post by CJ_Hudson on 2011-01-09
Thankyou very much for your response. Below is the code:

chris@chris-desktop:~$ dpkg --list | grep linux-image
rc  linux-image-2.6.24-16-generic              2.6.24-16.30                                      Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-21-generic              2.6.24-21.43                                      Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.27-11-generic              2.6.27-11.31                                      Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.27-14-generic              2.6.27-14.33                                      Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.27-7-generic               2.6.27-7.16                                       Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.27-9-generic               2.6.27-9.19                                       Linux kernel image for version 2.6.27 on x86/x86_64
rc  linux-image-2.6.28-11-generic              2.6.28-11.42                                      Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-13-generic              2.6.28-13.45                                      Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-14-generic              2.6.28-14.47                                      Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.28-15-generic              2.6.28-15.52                                      Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-2.6.28-16-generic              2.6.28-16.57                                      Linux kernel image for version 2.6.28 on x86/x86_64
rc  linux-image-2.6.31-15-generic              2.6.31-15.50                                      Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-16-generic              2.6.31-16.53                                      Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-17-generic              2.6.31-17.54                                      Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-19-generic              2.6.31-19.56                                      Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.31-20-generic              2.6.31-20.58                                      Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-21-generic              2.6.31-21.59                                      Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-21-generic              2.6.32-21.32                                      Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-22-generic              2.6.32-22.36                                      Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-23-generic              2.6.32-23.37                                      Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-24-generic              2.6.32-24.43                                      Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-25-generic              2.6.32-25.45                                      Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-26-generic              2.6.32-26.48                                      Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.35-23-generic              2.6.35-23.41                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-24-generic              2.6.35-24.42                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-24-generic-pae          2.6.35-24.42                                      Linux kernel image for version 2.6.35 on x86
ii  linux-image-generic                        2.6.35.24.28                                      Generic Linux kernel image

I hope that means something to you, it means s.f.a. to me!

---

### Post by CJ_Hudson on 2011-01-09
> **wojox said:**
> Also did you run

```
sudo update-grub
```

Result below:

chris@chris-desktop:~$ sudo update-grub
[sudo] password for chris: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-24-generic-pae
Found kernel: /boot/vmlinuz-2.6.35-24-generic
Found kernel: /boot/vmlinuz-2.6.35-23-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
 
Thanks.

---

### Post by wojox on 2011-01-10
Okay to remove the PAE run:

```
sudo aptitude remove linux-image-generic-pae  linux-image-2.6.35-24-generic-pae linux-headers-generic-pae linux-headers-2.6.35-24-generic-pae
```

Then to be safe 

```
sudo update-grub
```

---

### Post by CJ_Hudson on 2011-01-10
Thankyou very much wojox.

---

### Post by wojox on 2011-01-10
Your welcome. :D

---

### Post by CJ_Hudson on 2011-01-19
> **mikewhatever said:**
> If wireless didn't work out of the box with 32bit, it's unlikely to do so with 64. Hopefully it won't take six months this time.

There are no roll back or downgrade features of any kind in Ubuntu.

Please, would it involve a roughly similar process to 32 bit to install the driver package for my wireless card in 64 bit Ubuntu? i.e. would I still have to chose between proprietary and open source drivers, blacklist the old drivers and download ndiswrapper via a cable before getting it to work?
Thanks :-)

Of course, it may work 'out-the-box' since my original installation was Gutsy Gibbon 8.10.

---

### Post by CJ_Hudson on 2011-01-19
> **mikewhatever said:**
> If wireless didn't work out of the box with 32bit, it's unlikely to do so with 64. Hopefully it won't take six months this time.

There are no roll back or downgrade features of any kind in Ubuntu.

Please, would it involve a roughly similar process to 32 bit to install the driver package for my wireless card in 64 bit Ubuntu? i.e. would I still have to chose between proprietary and open source drivers, blacklist the old drivers and download ndiswrapper via a cable before getting it to work?
Thanks :-)

Of course, it may work 'out-the-box' since my original installation was Gutsy Gibbon 8.10.

EDIT: Sorry  I don't know why this appeared twice, I only posted it once!

---

