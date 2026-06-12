---
title: "Need help regarding dual boot"
date: 2010-10-30
forum: General Help
---

### Post by limjix on 2010-10-30
Hi guys, i recently had a problem with the Ubuntu 10.10 installation, so what I did was that I reinstalled 10.04 on another side of the hard disk partition.

Now i want to remove all the files on the Ubuntu 10.10 and also remove the boot screen that comes up asking me to choose.

How do i do it?

---

### Post by coreyscx on 2010-10-30
so you just want to keep 10.04? well..go to your partition software and delete the 10.10 then, but as for the loading screen..its called grub and its apart of linux, its linux's boot loader and cannot be deleted trust me i tryed before lol, unless! you completly wipe your drive, so..you can chage it though..but you are pretty much stuck with it sorry, just get rid of 10.10 and you should be good, why did u have problems with it?

---

### Post by matsuzine on 2010-10-30
Hi, limjix:

I just want to make sure that I understand that you did a fresh install of 10.04 on another partition?  This was after you installed 10.10, right?

What I would do is boot into the linux that I plan to keep.  Install gparted:

```
sudo apt-get install gparted
```

Use gparted to remove the unwanted partition.  

Run the following command:

```
sudo update-grub
```

This should rebuild your grub configuration file.

Install startupmanager from the repository:

```
sudo apt-get install startupmanager 
```

Open a terminal window ( Ctrl + Alt + T ) and type command 

```
uname -r
```

Find the Startup Manager program under System > Administration.  Choose the correct version of ubuntu you want to use as the default from the drop-down menu ( this will be the kernel you saw listed in the uname -r command ).  Set the timeout to zero.  Then, you won't get a menu, it will just boot to the default.

---

### Post by innkeeper on 2010-10-30
[SIZE=3]The mistake here was installing 10.10, which, from all indications is a real POS.  I tried 4 times to install it with no success - luckily.   10.04 works just fine.  I've not read a single positive post concerning 10.10.  Aren't the 10.10 developers getting the message?
  [/SIZE]

---

