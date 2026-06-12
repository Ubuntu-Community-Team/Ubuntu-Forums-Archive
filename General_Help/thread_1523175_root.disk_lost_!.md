---
title: "root.disk lost !?"
date: 2010-07-03
forum: General Help
---

### Post by MajinSaha on 2010-07-03
Hi !
Yesterday, when I was working in Wubi, the laptop turned off by itself, probably because of excessive heating in the room. After that, all my efforts to boot Wubi were useless. The line I saw was

```
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
```

I loaded Windows and checked whether everything was ok with root.disk. The file was there.
I decided to move it to some place else ( I forgot what was the reason) by cutting and paste. The cut was fine, but when I tried to paste, it said something like "root.disk is no longer where it should be". When I returned to /disks directory, root.disk wasn't there anymore, and the paste command hasn't moved it anywhere ! It just disappeared. Search gave me nothing.

I restarted Windows. It started performing disk check by itself, and I didn't stop it. After the checking was over, I looked and the most terrible fear came to life: the memory on the disk drive got additional 17 GB of free space, and I remember that root.disk was about 16 ! root.disk vanished forever ! 

Has anything like that happend to you before? I remember I didn't click any "delete" buttons and had no intentions to destroy root.disk ! Sorry if it sounds naive, but is there any chance that the data is still alive and is hiding somewhere ?

Thanks for your help !

---

### Post by philinux on 2010-07-03
Does not look good. You could try photorec from a livecd. Or ask for help here.

[http://wubi-installer.org/support.php](http://wubi-installer.org/support.php)

---

### Post by jwbrase on 2010-07-03
> **MajinSaha said:**
> Hi !
Yesterday, when I was working in Wubi, the laptop turned off by itself, probably because of excessive heating in the room. After that, all my efforts to boot Wubi were useless.

Wubi is very vulnerable to hard shutdowns. It's more for testing Ubuntu and deciding if you like it than for everyday use. If you want to use Ubuntu regularly you should install it to its own partition.

> The line I saw was

```
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
```

I loaded Windows and checked whether everything was ok with root.disk. The file was there.
I decided to move it to some place else ( I forgot what was the reason) by cutting and paste. The cut was fine, but when I tried to paste, it said something like "root.disk is no longer where it should be". When I returned to /disks directory, root.disk wasn't there anymore, and the paste command hasn't moved it anywhere ! It just disappeared. Search gave me nothing.

What I think happened here is that Windows saw the file in its "list of files", but when you tried actually doing something with it, and it looked on the disk where the list of files said it should be, all it found was garbage, because of the shutdown and Wubi's vulnerability, so then it removed it from its list. 

> 
I restarted Windows. It started performing disk check by itself, and I didn't stop it. After the checking was over, I looked and the most terrible fear came to life: the memory on the disk drive got additional 17 GB of free space, and I remember that root.disk was about 16 ! root.disk vanished forever ! 

Has anything like that happend to you before?

No, but hard shutdowns always carry some danger of something like that happening, and I've heard that Wubi is especially vulnerable due to its "filesystem in a file within a filesystem" nature. 

> I remember I didn't click any "delete" buttons and had no intentions to destroy root.disk ! Sorry if it sounds naive, but is there any chance that the data is still alive and is hiding somewhere ?

Thanks for your help !

A professional data recovery service might be able to help, but that would cost lots of money, and there's no guarantee of how much they'd be able to recover, as it depends on what exactly the crash did to root.disk.

As far as I can tell, root.disk was dead as soon as the machine shut itself off.

(Also, if the laptop is overheating and there are no problems with the cooling system on it, continuing to operate it in that room could shorten its life considerably. How hot is the room?)

---

### Post by bcbc on 2010-07-03
If windows sees the file as corrupted it moves it into a hidden folder c:\found.000

If you can find it, you might be able recover your data. The wubi guide has some info on this. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If find it but still can't boot, then you may be able to mount it and run fsck on it via a live CD. Again the wubiguide has info on how to do this.

---

