---
title: "Freeze up, Low disk Space, cannot install App..."
date: 2011-03-22
forum: General Help
---

### Post by RobotoidHuman on 2011-03-22
Hi Guys... need your help...

I've been using ubuntu since 2 weeks ago along with other 2 different OS...

I have 3 HDDs, 1st HDD is XP OS installed, 2nd HDD is no OS, 3rd HDD is XP & Ubuntu installed.

At the first time Installing Ubuntu, i don't choose to create partition on 3rd drive. I let the Ubuntu installed alongside XP. 

so here are my problems:

1. Today I try to cleaning the system using BleachBit, then i get the "Low Disk Space" Warning message after several minutes operation and the program can't continuing the operation with tons of errors list.

[http://i52.tinypic.com/ap8cqh.png](http://i52.tinypic.com/ap8cqh.png)

[http://i56.tinypic.com/kcm592.png](http://i56.tinypic.com/kcm592.png)

what actually happend...? Can someone explain why this operation needs more free disk space for deleting unused files...? 

take a look on my disk usage screenshot, can someone please help explains to me...

[http://i55.tinypic.com/d5zra.png](http://i55.tinypic.com/d5zra.png)

- 42 GB NTFS seems that is the windows partition. CMMIW
- what is "Extended 38 GB", "37 GB Ext4", and "1.6 GB Swap..."? 

In which partition the Linux Files system are stored...? How can I increasing the "1.6 GB Swap" partition...? 

2. Since the first time Installed, until now, the system is often suddenly freeze up... what causing the system freeze up...? the only solution for this is hard restart... Since i typing this message, the system already been freezed up 3 times! *LOL*

3. Always fail to install Nvidia VGA Driver, my current Graphic card is Nvidia GeForce 4 MX4000, the driver package name is "NVIDIA-Linux-x86-96.43.19-pkg1.run", Does Ubuntu 10.10 Support MX4000?

The errors are about: SystemError: E:Unable to correct problems, you have held broken packages, etc... etc... I forgot what exactly error message says... 

Tried to following the instructions i found around this forum, Trying to install from terminal or from Pref > Adms > additional driver also resulting the same error...

4. Cannot play any video files... error happens while installing video plugin 
[http://i54.tinypic.com/2hgczn9.png](http://i54.tinypic.com/2hgczn9.png)
[http://i55.tinypic.com/67mlhc.png](http://i55.tinypic.com/67mlhc.png)

I prefer to use VLC or KMPlayer, when i try to install, warning message says "Package dependencies cannot be resolved"... Also try to install Kaffeine, It says "available from the "main" source" what's that mean...? 

=====

FYI, these my Hardware:

AMD Athlon 64 1.8 Ghz
1.5 GB RAM
1st HDD MAXTOR SATA 80 GB 
2nd HDD WD SATA 500 GB
3rd HDD MAXTOR 80 GB
Samsung DVD Combo Optical drive

2 Win XP OS
1 Ubuntu 10.10 i386 OS (Installed from USB, after its always fail to install from live CD)


Wish You all Ubuntu Geeks could help to solve my problems... I'am totally n00b on Linux system... Thanks in advance

Regards

PS: I'm a non native English, please my apologize for my poor English... :)

---

### Post by deathadder on 2011-03-22
> 1. Today I try to cleaning the system using BleachBit, then i get the "Low Disk Space" Warning message after several minutes operation and the program can't continuing the operation with tons of errors list.

[http://i52.tinypic.com/ap8cqh.png](http://i52.tinypic.com/ap8cqh.png)

[http://i56.tinypic.com/kcm592.png](http://i56.tinypic.com/kcm592.png)

what actually happend...? Can someone explain why this operation needs more free disk space for deleting unused files...?

I don't have any experience using the app you're got in your screen shots, the only problem that I can see is you are trying (??) to remove files from outside your home directory. Your user doesn't have permission to remove the files in /usr/share/* so you're getting a [Errno 13] Permission denied error. I can't see where it's trying to use more disk space...

> 
take a look on my disk usage screenshot, can someone please help explains to me...

[http://i55.tinypic.com/d5zra.png](http://i55.tinypic.com/d5zra.png)

- 42 GB NTFS seems that is the windows partition. CMMIW
- what is "Extended 38 GB", "37 GB Ext4", and "1.6 GB Swap..."?

In which partition the Linux Files system are stored...? How can I increasing the "1.6 GB Swap" partition...?

I can understand why this is misleading, there are two types of partitions, a primary and extended partition. For various reasons the number of primary partitions on a disk is limited. So extended partitions are created which then allow you create more partitions within them. So, you may be seeing 4 partitions (1 Windows, 1 Extended, 1 ext4 and 1 swap) but what you've actually got is 1 42GB NTFS, 1 37GB ext4 and 1.6GB Swap. 

You're install will be placed within the ext4 partition. So that's the one that will need space cleared out of to get rid of the "low disk space" error. You can try clearing you're apt cache for example, or prune log files. 

> sudo apt-get clean

The swap space is used when your physical memory runs. Unless you find yourself constantly running low on memory you shouldn't end up using it. 

> 
2. Since the first time Installed, until now, the system is often suddenly freeze up... what causing the system freeze up...? the only solution for this is hard restart... Since i typing this message, the system already been freezed up 3 times! *LOL*

A number of things can cause the system to freeze, more details about what you're doing etc will be needed. You should create a new thread to deal with it so nothing gets over lapped. I would look into memory problems though. Try running memtest from the grub menu (if it's there). 

> 
3. Always fail to install Nvidia VGA Driver, my current Graphic card is Nvidia GeForce 4 MX4000, the driver package name is "NVIDIA-Linux-x86-96.43.19-pkg1.run", Does Ubuntu 10.10 Support MX4000?

Ubuntu lets you install the different binary packages from nVidia, so Ubuntu don't control which cards are supported etc. You can look on the nVidia site to see if your card is support. But since you're getting errors while trying to use apt to install them I would imagine that a combintation of low disk space and previously failed installed files. Have a look around the forum for the errors your getting and do a few Google searches to see if you can find the error. Failing that start a new thread with the error and see if anyone can offer advice.

Ubuntu does have some great how-to's, have a look at the one for nVidia drivers to see if that helps: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

> 
4. Cannot play any video files... error happens while installing video plugin
[http://i54.tinypic.com/2hgczn9.png](http://i54.tinypic.com/2hgczn9.png)
[http://i55.tinypic.com/67mlhc.png](http://i55.tinypic.com/67mlhc.png)

I prefer to use VLC or KMPlayer, when i try to install, warning message says "Package dependencies cannot be resolved"... Also try to install Kaffeine, It says "available from the "main" source" what's that mean...?

Basically it means that there has been a problem downloading the software from Ubuntu's repo's. It could be a number of reasons, but a few commands to try are:

> 
sudo apt-get update
sudo apt-get -f install
sudo apt-get install vlc


Have a look around the forum for specfic errors or create new threads to deal with individual problems. It'll make it a lot easier for everyone in the long run to help you and get help themselves. :D

---

### Post by Krytarik on 2011-03-22
I agree with what *deathadder* said, and I have a few additions:

1.) Check if your disk space is really almost used up:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

2.) I'm using a similar old video card, the installation of the "recommended" proprietary driver via "System -> Administration -> Additional Drivers" should be fine.

3.) You may need to run this additional command, after "apt-get -f install":
```
sudo apt-get --fix-missing install
```And I would also do an upgrade after that:
```

sudo apt-get upgrade
```Good luck!

---

### Post by RobotoidHuman on 2011-03-23
Thanks for the response...

> **deathadder said:**
> 

I can understand why this is misleading, there are two types of partitions, a primary and extended partition. For various reasons the number of primary partitions on a disk is limited. So extended partitions are created which then allow you create more partitions within them. So, you may be seeing 4 partitions (1 Windows, 1 Extended, 1 ext4 and 1 swap) but what you've actually got is 1 42GB NTFS, 1 37GB ext4 and 1.6GB Swap.

You're install will be placed within the ext4 partition. So that's the one that will need space cleared out of to get rid of the "low disk space" error. You can try clearing you're apt cache for example, or prune log files.

The swap space is used when your physical memory runs. Unless you find yourself constantly running low on memory you shouldn't end up using it. 

thats what i confused about, if the File system is installed on ext4, why the free space remains only 6xxx MB. where's the the 36 GB gone...? is that a normal operation...?

> **deathadder said:**
> A number of things can cause the system to freeze, more details about what you're doing etc will be needed. You should create a new thread to deal with it so nothing gets over lapped. I would look into memory problems though. Try running memtest from the grub menu (if it's there). 

Sorry for that, will create another thread later... Memtest is running well... some says Firefox & chrome (including their plugins) causing that freeze, gonna try to remove FF & Chrome... let it run and what would happens then... 


> **deathadder said:**
> Ubuntu lets you install the different binary packages from nVidia, so Ubuntu don't control which cards are supported etc. You can look on the nVidia site to see if your card is support. But since you're getting errors while trying to use apt to install them I would imagine that a combintation of low disk space and previously failed installed files. Have a look around the forum for the errors your getting and do a few Google searches to see if you can find the error. Failing that start a new thread with the error and see if anyone can offer advice.

Ubuntu does have some great how-to's, have a look at the one for nVidia drivers to see if that helps: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)


Solved!! Great advice... Thank you mate... :)

> **deathadder said:**
> Basically it means that there has been a problem downloading the software from Ubuntu's repo's. It could be a number of reasons, but a few commands to try are:

Have a look around the forum for specfic errors or create new threads to deal with individual problems. It'll make it a lot easier for everyone in the long run to help you and get help themselves. 

yes yes.. i'm confused on my own thread too.... :D

---

### Post by RobotoidHuman on 2011-03-23
> **Krytarik said:**
> I agree with what *deathadder* said, and I have a few additions:

1.) Check if your disk space is really almost used up:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

2.) I'm using a similar old video card, the installation of the "recommended" proprietary driver via "System -> Administration -> Additional Drivers" should be fine.

3.) You may need to run this additional command, after "apt-get -f install":
```
sudo apt-get --fix-missing install
```And I would also do an upgrade after that:
```

sudo apt-get upgrade
```Good luck!

Hi, Krytarik...

1. Thank you, gonna read a whole that thread... i will let you know when it's been applied... 

2. Solved!

3. Solved after ticking the proposed release update

Thanks, Mate... :)

---

### Post by deathadder on 2011-03-23
> **RobotoidHuman said:**
> 
thats what i confused about, if the File system is installed on ext4, why the free space remains only 6xxx MB. where's the the 36 GB gone...? is that a normal operation...?
You can very quickly find the largest directory by the following command:
```
$ cd /
$ sudo du -Sh 2>/dev/null | sort -n -r | head -n10

```
Or if you prefer something a easier and more intuitive, the Disk Usage Analyser from the "Application/Accessories" menu works wonders. 
> 
Sorry for that, will create another thread later... Memtest is running well... some says Firefox & chrome (including their plugins) causing that freeze, gonna try to remove FF & Chrome... let it run and what would happens then...
Yeah which is why tracking down a system freeze can be a bit of a nightmare, you might want to try disabling plugins and seeing if that fixes the problem.

---

