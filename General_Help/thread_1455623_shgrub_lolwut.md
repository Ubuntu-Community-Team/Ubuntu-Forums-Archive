---
title: "sh:grub lolwut?"
date: 2010-04-16
forum: General Help
---

### Post by friedshan on 2010-04-16
Hello,

I am currently on windows on my PC...

I always use ubuntu and have lots of important files in there..

What happened before?
I was working on the comp...pop messages were getting downloaded on evolution mail...pidgin was running...google chrome was running..
My version: 9.10

Found this somewhere: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://answers.launchpad.net/ubuntu/+source/grub2/+question/107653](https://answers.launchpad.net/ubuntu/+source/grub2/+question/107653)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104?comments=all)

When i select ubuntu from dual boot screen..
It dosen't do the usual thing of asking me some options second one would be recovery mode..

It takes me to some Grub loader beta4 (don't remember name)

I get to type something as..

sh:grub> (type here)

something like that...

Help me please.

Thank You!

---

### Post by mikecrowe on 2010-04-16
I just developed the same problem.

---

### Post by friedshan on 2010-04-16
Seems bad..

But i didn't download any new updates.

---

### Post by friedshan on 2010-04-17
help ?

---

### Post by friedshan on 2010-04-17
added more links

---

### Post by oldfred on 2010-04-17
Your error is usually from a wubi install, is that what you have?

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

 [wubi] Wubi 9.10 + upgrade ubuntu = sh:grub> 
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

---

### Post by friedshan on 2010-04-18
Yes it was installed via wubi..

Is there anyway to make it to the D: partition and not keep it look like a wubi install?

[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10](http://sourceforge.net/apps/mediawik...lems:Wubi_9.10) completed..but no help..

Trying..[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)
but it's stuck at 40 percent of stage 4
performed the function in D: (where ubuntu is present)

---

### Post by coffeecat on 2010-04-18
edit: sorry, posted in error.

---

### Post by friedshan on 2010-04-18
Update 
Completed:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

But no help from any of those..

I could try anything which can be done via a live CD if possible...

If i have to re-install...ok...but i need to backup all data in it.

---

### Post by oldfred on 2010-04-18
If you want to convert your D: partition it will not be D: and visible from windows as that would be a total new install to a ext3 or ext4 partition. 

You have to total backup everything on D: as changing the format will destroy all data. 

Often with dual boot it is worthwhile to create a shared NTFS partition like D: to store data, then your Ubuntu install only needs 10-20GB to install and 2GB or more (if you want to hibernate and have more RAM) for swap.

IF D: is large enough just use gparted to shrink it by 10-20GB (defrag in windows first) and reinstall to the free space then D: is your shared and you have a full install.

IF D: is not large enough:
You will have to delete your D: and install into free space or manually partition changing D: to ext3 and adding a 2GB swap. Then you use manual install and manually choose the partitions previously created.

---

### Post by friedshan on 2010-04-19
D: has nothing else than ubuntu in it..
I want every data stored in profiles of ubuntu..such as in folders like desktop,documents,etc....

D: has more than 20GB Space...

I would be going with something that could get my backup...then reinstall without wubi.

---

### Post by friedshan on 2010-04-21
huh?

---

### Post by oldfred on 2010-04-21
If you have space you can do a full install and then mount the wubi file and copy all the data over. If not you have to back it up and can then copy the data into the new install.

---

