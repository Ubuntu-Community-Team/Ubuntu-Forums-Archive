---
title: "how to access my D drive root from ubuntu"
date: 2010-03-21
forum: General Help
---

### Post by unpresedented on 2010-03-21
Dear all,
I'm a new comer to Linux world, and I wish I can find help with some difficulties that I might face.
I have a machine with Window 7 and Ubuntu (dual boot), windows 7 is installed on C drive and ubuntu installed on D drive, when I'm on Window, I put a folder named folder1 on D drive root beside (not inside) the main ubuntu folder. when I open ubuntu I can't see that file on D drive, I tried to search for it but couldn't find it, how can I access this file please ?
 
thank you in advance

---

### Post by 3rdalbum on 2010-03-21
> **unpresedented said:**
> Dear all,
I'm a new comer to Linux world, and I wish I can find help with some difficulties that I might face.
I have a machine with Window 7 and Ubuntu (dual boot), windows 7 is installed on C drive and ubuntu installed on D drive, when I'm on Window, I put a folder named folder1 on D drive root beside (not inside) the main ubuntu folder. when I open ubuntu I can't see that file on D drive, I tried to search for it but couldn't find it, how can I access this file please ?
 
thank you in advance

I assume you used Wubi to install Ubuntu. So you will find your Windows system if you go to Filesystem and open the 'host' folder.

---

### Post by unpresedented on 2010-03-21
> **3rdalbum said:**
> I assume you used Wubi to install Ubuntu. So you will find your Windows system if you go to Filesystem and open the 'host' folder.
 
yes I used Wubi, and I can see both drives, but what i exactly want is to see the file that I have added on D drive root when I was on Windows OS .. I can't see when I open the same drive from Ubuntu ... this is really a huge headache !!
 
can anyone help me please ?

---

### Post by vanadium on 2010-03-21
"host" will probably contain the files of the partition known as the C: drive under Windows. My guess is that the partition known as the D: drive is not mounted by default. You will therefore not see these files unless you mount that partition. Can you see the d: partition under "Places" (obviously, it will have another name)? Then clicking it should mount it.

---

### Post by unpresedented on 2010-03-21
> **vanadium said:**
> "host" will probably contain the files of the partition known as the C: drive under Windows. My guess is that the partition known as the D: drive is not mounted by default. You will therefore not see these files unless you mount that partition. Can you see the d: partition under "Places" (obviously, it will have another name)? Then clicking it should mount it.
 
I can see C: drive when I am on ubuntu with all of its contents (its name is not C drive of course), and I can see another drive (it's name not D drive) and I can access it and see ubuntu files, but the files that I put on its root when I was on windows. 
really weird :(

---

### Post by vanadium on 2010-03-21
Open a terminal and post the output of the commands "mount" and "sudo blkid" here. Then I can see what is mounted where.

```

mount
sudo blkid

```
For the second command, you need to supply your normal user login password.

---

### Post by 3rdalbum on 2010-03-21
> **unpresedented said:**
> I can see C: drive when I am on ubuntu with all of its contents (its name is not C drive of course), and I can see another drive (it's name not D drive) and I can access it and see ubuntu files, but the files that I put on its root when I was on windows. 
really weird :(

Not really weird. There are three disks on your system. There's the one that holds Windows (your C drive, as Windows would call it). There's another one that Windows calls the "D drive". And sitting on the D drive is a file that contains a virtual hard disk, that contains Ubuntu.

When you boot up Ubuntu, it treats this file as though it was a real hard disk. So when you look at "Filesystem", it won't contain the folder you put in, because the folder is outside the virtual hard disk; it's on the real hard disk.

The Places menu might not show the real D hard disk, because in a way the real hard disk is already mounted, to get at the virtual hard disk. You should certainly be able to exchange documents with the C drive by going to Filesystem/host

This is one of the reasons I dislike Wubi as a method of installation - it's quite confusing to think about the real hard disks and the virtual hard disks and which ones will be visible to Ubuntu. If you are going to use Ubuntu for any length of time, I'd recommend booting up from the Ubuntu CD and installing Ubuntu that way. It will use a real partition or a real hard disk, rather than a virtual one. Trust me, you'll be much happier this way.

---

### Post by unpresedented on 2010-03-21
> **3rdalbum said:**
> Not really weird. There are three disks on your system. There's the one that holds Windows (your C drive, as Windows would call it). There's another one that Windows calls the "D drive". And sitting on the D drive is a file that contains a virtual hard disk, that contains Ubuntu.
 
When you boot up Ubuntu, it treats this file as though it was a real hard disk. So when you look at "Filesystem", it won't contain the folder you put in, because the folder is outside the virtual hard disk; it's on the real hard disk.
 
The Places menu might not show the real D hard disk, because in a way the real hard disk is already mounted, to get at the virtual hard disk. You should certainly be able to exchange documents with the C drive by going to Filesystem/host
 
This is one of the reasons I dislike Wubi as a method of installation - it's quite confusing to think about the real hard disks and the virtual hard disks and which ones will be visible to Ubuntu. If you are going to use Ubuntu for any length of time, I'd recommend booting up from the Ubuntu CD and installing Ubuntu that way. It will use a real partition or a real hard disk, rather than a virtual one. Trust me, you'll be much happier this way.
 
yes exactly as you said Mr. 3rd Album ...
I think I have to make a bootable DVD first, I have an ISO image (size 4 GB) which I downloaded from [here]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/9.10/release/") , chose the .iso file in the list down. I extracted this image and installed it, now If i made a bootable DVD from this image, will it work and install ubunutu without problems ?

---

### Post by unpresedented on 2010-03-21
does installing ubuntu after booting from its DVD support dual boot with windows or not ? i'm afraid that it will delete my windows, what do you think ?

---

