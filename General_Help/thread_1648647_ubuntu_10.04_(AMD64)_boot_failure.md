---
title: "ubuntu 10.04 (AMD64) boot failure"
date: 2010-12-19
forum: General Help
---

### Post by sotirisa on 2010-12-19
I have a serious problem with a persistent ubuntu 10.04 boot failure and urgently need help to fix my installation. This is my first post and here is my story.

I have been using ubuntu for about two years now and except of a few occasions of true frustration, it was running quite smoothly. During this time, I added many programs and a few customization features. I think of myself as an experienced computer user, but I am not a Linux expert and know little about Unix commands.

My ubuntu 10.04 installation is on an HP desktop with Intel Core 2 Duo CPU E7300, 3GB of ram and 2 hard drives (160GB (sda), 500GB (sdb)). My first drive (sda) included a partition with the an XP installation, an ext3 empty partition and third partition with a Windows 7 installation. The second drive includes and NTFS partition with data, an ext3 partition with my ubuntu 10.04 installation and a couple of small swap partitions.

Lately, I installed a new Plymouth theme and had a couple of hangs (I just rebooted), but other than that the system was fine, at least on the surface.

About a week ago I decided to clean up my computer. First, I removed some old linux Kernels from my ubuntu installation with Synaptic and left the latest version (2.6.32-26). I think ubuntu continued to behave normally, but I am not 100% sure about this. Then I moved all the useful data from the partition with the XP installation and formatted the partition. When I rebooted disaster struck and could not boot to anything. I tried the recovery mode, but it also failed to boot and gave me no menu to move ahead.

I tried fixing grub 2 with a live DC with Ubuntu 9.10 (and a then a USB startup disk with ubuntu 10.04) following the instructions for grub 2 reintallation at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (first and third method). I managed to boot into Windows 7, but my ubuntu installation would still hang on Plymouth animation. At the time, I thought this was still a grub 2 problem and I tried EasyBCD from Windows 7, but with no success. I also used Rescatux from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and tried to fix grub 2. At this point, I noticed that grub 2 was giving me two options to boot to the same Linux Kernel (+2 for additional options for the corresponding recovery modes). The first was listed as “generic” and the second “generic-single user”. I still see double entries in my grub 2 menu (the "generic-single user" tag was only visible in Rescatux) but no matter which entry I try, I still get the same results: The system hangs and fails to boot.

I saw an old post from 2006 that the live DC included at the time a repair option, but I guess this is no longer available. This is truly disappointing having in mind that even Windows readily offers this capability. Such a feature is far more important for Ubuntu since it is a lot more than an operating system. 

In any case, I decided to install a fresh Ubuntu installation on my first drive (sda, old ext3 partition that I reformatted to ext4) to make progress.  I updated the system and this new installation now runs smoothly with kernel 2.6.32-26 on this drive. This eliminates to a very large extend the possibility of a hardware problem. However, all my programs and customization features are still in my old Ubuntu installation in the second drive (sdb), which still does not boot.

Trying to check if this is a Plymouth problem, I followed the instructions in this post [http://askubuntu.com/questions/8445](http://askubuntu.com/questions/8445) to bypass Plymouth, but this did not fix the problem. The system still hangs, control+D does nothing and if I press Esc I see:

unreadahead-other main process (846) terminated with status 2 
mountall: Event failed 
unreadahead-other main process (847) terminated with status 2 
mountall: Event failed 

I checked the “unreadahead” message on the forums and learned that this is not necessarily an error. I have also seen a couple of bug reports on “mountall: Event failed”, but found no solution to this issue. 

I have also tried to copy my programs and settings from my old Ubuntu installation to the new by copying my old /home folder to the new installation according to this post [http://ubuntuforums.org/showthread.php?t=1585001](http://ubuntuforums.org/showthread.php?t=1585001).  However, I could not generate a package.selections file and this method did not work.

I then found an old post at ubuntu geek [http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html) with instructions to repair a broken system from a line CD using the “chroot” command. I followed the instructions and updated the system with “apt-get update,
apt-get upgrade, apt-get dist-upgrade” but with no success. I also tried a newer post at geekzone at
*[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=65017](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=65017), Reply # 357500, that suggested using the “aptitude” command instead, but still with no success.

It this point, I do not know what else to do. I spend quite some time to set up all my programs and settings in my original Ubuntu installation and it is very important for me to be able to fix it, or at least find some way to import this configuration to my new and clean Ubuntu installation. I would very much appreciate any suggestions on how to fix this problem.

---

### Post by sotirisa on 2010-12-27
Just to let you know that I have been able to access the command prompt of my original (unbootable) ubuntu installation on drive sda using the directions found in this post: [http://ubuntuforums.org/showthread.php?t=1652269&highlight=passes+grub](http://ubuntuforums.org/showthread.php?t=1652269&highlight=passes+grub), Reply #12, method 2 suggested by VonFilmjölk two days ago. However the “apt-get dist-upgrade” command has not installed anything.

I then tried the aptitude commands suggested at:
*[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=65017](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=65017), Reply # 357500. I  run “sudo aptitude update && sudo aptitude install gtkorphan”, “sudo aptitude update && sudo aptitude upgrade” and “sudo aptitude -f”. I managed to upgrade the installation including a new Linux kernel but did not manage to do anything useful with the options given by “sudo aptitude -f”. 

I rebooted the system and still get the same boot failure as before. It is worth noting that the grub 2 file of my my original (unbootable) ubuntu installation in drive sda has double additional entries for the new kernel that I have just installed. In fact, now I have 8 entries for the 2 different kernels on that installation (and additional single entries of my new ubuntu installation on drive sdb). 

I updated the grub 2 file on my new ubuntu installation drive sdb and see the double kernel entries on drive sda there as well (None of the sda kernel options is bootable and they all hang). Could this be the problem?

I would really appreciate some help to resolve this matter.

---

### Post by sotirisa on 2011-01-05
anyone?

---

### Post by TeoBigusGeekus on 2011-01-05
The only thing I can think is to boot with a live cd, erase your home folder from the working ubuntu installation and copy everything from your home folder from your older, non working installation to it.
After that, just install all your necessary applications in your new ubuntu and you will magically have all your settings back.

At least that's what I'd do in order to avoid future trouble.

---

### Post by sotirisa on 2011-01-05
Thank you for your reply and readiness to assist!

My settings is a secondary issue for me, as I have already implemented many of them in my new ubuntu installation by now. 

What is important, is to be able to use the programs that I have installed on my old unbootable ubuntu installation. Some of these are customized, like Virtual Box with guest additions and ffmpeg with mp4 support. 

It took me quite a some time and effort to set them up. If possible, I would like to use these programs one way or the other, without having to reinstall then and try to add such capabilities again.

---

