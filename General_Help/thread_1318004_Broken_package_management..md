---
title: "Broken package management."
date: 2009-11-07
forum: General Help
---

### Post by kimdino on 2009-11-07
Hi folks,

Two days ago I decided to upgrade Jaunty to Karmic. Shortly after starting the upgrade I was informed that there was insufficient room in my root ('/') partition. I like to have separate 'usr' and 'home' 
partitions and so the root partition is only 2Gb. 

So I fired up Midnight Commander and went looking for clutter that could be removed to make that extra bit of space. What I found was what appeared to be the leftovers of past kernel upgrades. I cannot remember the kernel version current at the time but I believe it was 2.6.28-15. So when I found that the headers etc for 2.6.28-11, 2.6.28-13 & 2.6.28.14 were still there I believed that these were just clutter that somehow got forgotten by 'dpkg' when clearing up after previous kernel upgrades. After all, they could be no possible use to the current system so I deleted them, the associated 'lib' directories & boot 'img's.

Hey presto, there was now enough space so I fired up the upgrade to 'Karmic' and went to bed.

The next day, with 'Karmic' running, I fired up the system manager to sort out various applications and got a broken dependencies error. As my investigations went down through the package manager levels I realised that 'dpkg' was attempting to clean up the old kernel stuff, not finding the files & exiting.

To summarise 'dpkg --audit' returns
[I]The following packages are only half installed, due to problems during
installation. The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-restricted-modules-2.6.28-14-generic Non-free Linux kernel modules for v
 linux-restricted-modules-2.6.28-13-generic Non-free Linux kernel modules for v
 linux-restricted-modules-2.6.28-11-generic Non-free Linux kernel modules for v[/I]
and
[I]dino@dino-desktop:~$ sudo dpkg --remove linux-restricted-modules-
linux-restricted-modules-2.6.28-11-generic  linux-restricted-modules-2.6.28-15-generic
linux-restricted-modules-2.6.28-13-generic  linux-restricted-modules-common
linux-restricted-modules-2.6.28-14-generic
dino@dino-desktop:~$ sudo dpkg --remove linux-restricted-modules-2.6.28-11-generic
[sudo] password for dino:
(Reading database ... 137692 files and directories currently installed.)
Removing linux-restricted-modules-2.6.28-11-generic ...
rmdir: failed to remove `/lib/modules/2.6.28-11-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.28-11-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Cannot find /lib/modules/2.6.28-11-generic
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-11-generic[/I]

I tried reinstalling them but 'apt-get' falls into the same trap and doesn't complete.

I have got as far as trying to clean up using '--force-remove-reinstreq' in 'dpkg' with no luck. So I thought it time to seek wisdom elsewhere.

'dpkg' refuses to do anything until this is corrected so I am unable to use anything sat on it, such as 'System Settings', 'aptitude' et. al. 

Has anyone any advice. Advice other than 'use the package manager to remove files in future', I've already learnt that big time.  
[http://ubuntuforums.org/images/smilies/redface.gif](http://ubuntuforums.org/images/smilies/redface.gif)
Cheers, Kimdino

---

