---
title: "Migrate from 32bit to 64bit, questions"
date: 2010-08-23
forum: General Help
---

### Post by superubufan on 2010-08-23
Hello,

I have read "it is impossible to migrate from 32bit to 64bit ubuntu without a fresh install". But I couldn't find any reasons or explanations for this statement. 

From my beginners perspective I can only see problems with filesystem tools. 

Shouldn't it just work if I would replace any installed 32bit package with its 64bit counterpart including a new kernel, upgrade grub and reboot? If not, why?

Thanks to anybody bringing some light into this matter :)

Best
superubufan

---

### Post by Slim Odds on 2010-08-23
It seems like it should be that simple, but it never is.

You also have to watch out for any 32 applications that will be a 32 bit compatible libraries.

It probably can be done, but nobody has bothered. Probably because it's not that hard to just reinstall the 64 bit version. Especially if you keep a separate /home partition.

---

### Post by superubufan on 2010-08-23
> **Slim Odds said:**
> 
You also have to watch out for any 32 applications that will be a 32 bit compatible libraries.


Unfortunately I don't have a seperate partition for /home and since I have a lot of stuff on the harddisk it would just take less time to "upgrade" by just installing the 64bit packages. Since I would of to do a complete backup for both ways I think I just try and report back my results here.

---

### Post by howefield on 2010-08-23
> **superubufan said:**
> Unfortunately I don't have a seperate partition for /home and since I have a lot of stuff on the harddisk it would just take less time to "upgrade" by just installing the 64bit packages. Since I would of to do a complete backup for both ways I think I just try and report back my results here.

Can't wait for the post mortem ;-)

Bear in mind you risk an unbootable system, meaning access to your "lot of stuff" might be difficult.

Of course, if you have a back up of it, then it is a moot point.

---

### Post by dino99 on 2010-08-23
if you want the 64 bits advantages but not the issues, stay with 32 bits and install the pae kernel

---

### Post by Calash on 2010-08-23
In "theory" it can be done but you are looking at a path that you will have nearly no support for should anything go wrong.  You are looking at an in-place update of nearly every file on the system along with any necessary configuration updates.  If you have any custom drivers that required compiling it gets even worse.

I did find one reference to this type of upgrade, but on a Fedora system

[http://www.linux.com/archive/feature/123800](http://www.linux.com/archive/feature/123800)

Honestly, it is not worth the effort.  You will spend less time backing up your /home directory and doing a fresh install.

---

### Post by KdotJ on 2010-08-23
Surely if you're going to do a complete back up either way, isn't it the better option to just do a fresh install of a 64 bit version?? It will decrease your probability of something getting messed up? Plus you never know what old clutter will get left behind taking up space or having multiple libs with this conversion

---

### Post by cascade9 on 2010-08-23
> **dino99 said:**
> if you want the 64 bits advantages but not the issues, stay with 32 bits and install the pae kernel

All the PAE kernel gives you is access to RAM over 3.5GB, PAE still slower than 64bit.

*edit- it will be interesting to see if the OP borks the install trying this out......

---

### Post by jocko on 2010-08-23
> **dino99 said:**
> if you want the 64 bits advantages but not the issues, stay with 32 bits and install the pae kernelStop saying this. The amount of ram that can be used is **NOT** the only benefit of using 64 bit. And you **DON'T** need 4Gb or more ram to benefit from 64 bit...

And I guess there is one very serious roadblock that would prevent you from upgrading a running system from 32 bit to 64 bit:
While the upgrade process would run, it would replace 32 bit executable files with 64 bit versions, while still running a 32 bit kernel. During installation of packages several executable files need to be run (at least dpkg and a few other programs are needed for every one of the packages...). Once one of those needed programs have been replaced by their 64 bit versions, the install process would fail for every package (since the kernel is still 32 bit). Not to mention that the running operating system would probably become more and more unstable (or simply just crash) once some file it needed was not available as 32 bit...

I'm sure it's *possible* to design a method for doing it, but I guess it would either have to be done from a special "64 bit migration cd" or by some elaborate method that would download all the packages, install a minimal 64 bit install system, reboot and install the rest from there... But any such method does not exist for ubuntu, because no-one have designed it. And even if it would exist, I would not think it was a good idea to use it. There are just too many things that could go wrong, which is probably why no-one have thought it important enough to spend time on developing a system for doing this.


My advice is to:
1. Resize your partitions to make room for one more partition (ext4 or any other linux file system you may prefer).
2. Copy your home directory and any other files you want to keep from your current ubuntu partition to this new partition.
3. Install 64 bit ubuntu. Set up the file system manually to:
    a. Use your old ubuntu partition as root (/) file system. Make sure it IS reformatted (to ext4 or whichever other linux file system you prefer).
    b. Use the new partition as /home. Make sure it is NOT reformatted.
4. There is no 4.

---

### Post by superubufan on 2010-08-23
> **jocko said:**
> During installation of packages several executable files need to be run (at least dpkg and a few other programs are needed for every one of the packages...). Once one of those needed programs have been replaced by their 64 bit versions, the install process would fail for every package (since the kernel is still 32 bit). 


Thats a good point, the very first real plausbile explanation (all other threads just say: don't do it, its not working bla)

> **jocko said:**
> 
1. Resize your partitions to make room for one more partition (ext4 or any other linux file system you may prefer).
2. Copy your home directory and any other files you want to keep from your current ubuntu partition to this new partition.

 
I don't like seperate partitions for home / system. I tend to run out of space on one or the other at some point and then I am at no option or deleting files although I have enough on the other partition... I used to do it in DOS/win32 times... Got a headache everytime...

---

