---
title: "Insufficient Space"
date: 2012-07-04
forum: General Help
---

### Post by vkadal on 2012-07-04
I am using ubuntu 12.04. It displays insufficient space for while update or down loading torrents. I booted in Windows mode and checked that all the drives have sufficient space. Still the warning is coming. How to resolve this problem?

---

### Post by arubislander on 2012-07-04
The only way to solve insufficient space warnings is to free up some diskspace :)

You have to check your disk space in Ubuntu, not in Windows. Windows cannot see your Ubuntu partitions. The easyest way to do so is to load the System Monitor. And look on the last tab.

---

### Post by coffeecat on 2012-07-04
@vkadal, you say that you are running Ubuntu, yet you prefixed the thread Lubuntu. And are you running a wubi installation? Post the output of these two terminal commands:

```
df -h
cat /etc/lsb-release
```

You can paste the output into your post by highlighting it with the mouse and right-click -> copy.

---

### Post by mojo risin on 2012-07-04
I had the same problem before too(forgot about it as I havent used torrent for a while.)
```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        24G   16G  7.1G  69% /
udev            241M  4.0K  241M   1% /dev
tmpfs           100M  824K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M   88K  248M   1% /run/shm
```

---

### Post by coffeecat on 2012-07-04
@mojo risin. Are you wanting help? If so, please start your own thread.

---

### Post by vkadal on 2012-09-28
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            601M  555M   16M  98% /
udev            429M  4.0K  429M   1% /dev
tmpfs           175M  784K  174M   1% /run
/dev/sdb1       7.6G  1.3G  6.3G  18% /cdrom
/dev/loop0      667M  667M     0 100% /rofs
tmpfs           437M  8.0K  437M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            437M  208K  437M   1% /run/shm

---

### Post by vkadal on 2012-09-28
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            601M  555M   16M  98% /
udev            429M  4.0K  429M   1% /dev
tmpfs           175M  784K  174M   1% /run
/dev/sdb1       7.6G  1.3G  6.3G  18% /cdrom
/dev/loop0      667M  667M     0 100% /rofs
tmpfs           437M  8.0K  437M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            437M  208K  437M   1% /run/shm
ubuntu@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2012-09-28
@vkadal, this:

```
ubuntu@ubuntu:~$
```

Tells us that you are running the Ubuntu live session, either from a CD or USB. Which? If a USB have you set it up with persistence?

This:

```
/cow 601M 555M 16M 98% /
```

Tells us you have less than 1GB available RAM and what is available for the live session is 98% used up. When running a live session, you run everything in RAM, unless you have persistence.
 
And this:

```
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

Tells us you are running a live session of Ubuntu, not Lubuntu. Was there any reason why you prefixed this thread Lubuntu instead of Ubuntu? Do you have a permanent installation of Ubuntu or Lubuntu? Are you getting the insufficient space message when running a permanent installation or a live session?

---

### Post by vkadal on 2012-09-29
> **coffeecat said:**
> @vkadal, this:

```
ubuntu@ubuntu:~$
```

Tells us that you are running the Ubuntu live session, either from a CD or USB. Which? If a USB have you set it up with persistence?

[COLOR="SeaGreen"]I am running using USB. I could not install in the hard drive. The installation could not complete successfully. So I opted for USB version.

I did not set up with persistence. Kindly tell me how to do it?[/COLOR]

This:

```
/cow 601M 555M 16M 98% /
```

Tells us you have less than 1GB available RAM and what is available for the live session is 98% used up. When running a live session, you run everything in RAM, unless you have persistence.
 
And this:

```
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

Tells us you are running a live session of Ubuntu, not Lubuntu. Was there any reason why you prefixed this thread Lubuntu instead of Ubuntu? Do you have a permanent installation of Ubuntu or Lubuntu? Are you getting the insufficient space message when running a permanent installation or a live session?

[COLOR="rgb(46, 139, 87)"]I am using Ubuntu , not Lubuntu. In another machine, (laptop) I got the same error with permanent installation.  Prefixing this thread as Lubuntu is an error.  The error message is from a live session (running from USB) 

I have clarified to the best of my efforts. Can you help me to get over my problem?[/COLOR]

---

### Post by trellis2 on 2012-09-29
With anything new the more you do it the better you become. "Practice makes adequate." I trust this is an old experimental back-up computer.
If the system requirement are met it's a good bet your hard drive is going bad. You can possibly send the torrent to another partition on the native drive. Try GParted. 

Got an external drive available?

---

### Post by spaceshipguy on 2012-09-29
I had similar issues after switching to Ubuntu because a Windows computer died. I don't know what Windows did to my computer but I had to wipe the whole disk with Gparted before I could get Ubuntu to install. 
Are you trying to rescue a laptop that Windows killed, like I was?

---

### Post by spjackson on 2012-09-29
> **vkadal said:**
> I am using ubuntu 12.04. It displays insufficient space for while update or down loading torrents. I booted in Windows mode and checked that all the drives have sufficient space. Still the warning is coming. How to resolve this problem?When you run from Live USB, it does not use any of your internal hard disk partitions unless you mount them and specify the appropriate directory for your torrent downloads.

---

### Post by coffeecat on 2012-09-29
> **vkadal said:**
> I am running using USB. I could not install in the hard drive. The installation could not complete successfully. So I opted for USB version.

That would explain this problem:

> **vkadal said:**
> I am using ubuntu 12.04. It displays insufficient space for while update or down loading torrents.

While running in live mode you are not using the hard drive at all, unless you deliberately mount a partition. If you try to update or use a torrent, the system is trying to save to RAM, so with less that 1GB RAM you rapidly run of out memory. Persistence would avoid this, but if you are wanting to create a permanent installation in the hard drive, this is somewhat irrelevant.

If you are trying to create a permanent installation and you are unable to, then you would need to give details of your hardware and what problems you encountered, apart from running out of memory when you tried to download something. Now that you have clarified that you are using Ubuntu and Lubuntu, I'll change the thread prefix. However, if your machine is an older one, and the less than 1GB RAM suggests it is, you might be better off with Lubuntu anyway, but let's see what your system specifications are.

---

### Post by vkadal on 2012-09-29
You may be correct. Both the laptop and this desktop are old machines. I finding problems to install some programs. Will it solve if wipe clean entire drive and install fresh?

---

### Post by vkadal on 2012-10-02
my RAM memory was faulty. It caused all the problem. The memory test while installing ubuntu from usb helped to identify this problem

---

### Post by vkadal on 2012-11-03
I am using Ubuntu 10.04. Once I got a warning that insufficient disk space and it offered to clear the trash. After cleaning the trash, the message did not appear once again. My concern is if I put more files in the user area, the error may appear once gain even if I have more space in the disk. Once I experience the problem in Ubuntu 12.04

---

