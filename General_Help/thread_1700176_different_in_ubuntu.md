---
title: "different in ubuntu?"
date: 2011-03-04
forum: General Help
---

### Post by pua06 on 2011-03-04
salmo allikm warhamt allah wa brakato

i am new in linux field want to know what make different between 
1-ubuntu ,kubuntu..........

and 
in ubuntu  maverick,lucid and so on
does the each community share some thing  example
ubuntu (lucid , mavercik)
share something

2-another different between saying ubuntu 10.10 and kernel for example   2.6.35.22 what be adding

sorry but this confuses me

---

### Post by spiky001 on 2011-03-04
Hi Ubuntu runs the Gnome desktop,
Kubuntu runs the KDE desktop more eye candy

Ubuntu Lucid  is an earlier version of ubuntu Maverick is the last version  and Now the latest is Natty Narwal They are just update  (" improved versions")

---

### Post by idoitprone on 2011-03-04
The difference between kubuntu and ubuntu is desktop environments: kubuntu = kde, lubuntu = lxde, ubuntu = default gnome, and etc.

The difference between lucid and mavericks is different versions of ubuntu eg. windows vista vs windows 7. Ubuntu lucid is 10.04, while maverick is 10.10. Lucid is a LTS, which mean Canonical will support 10.04 for three years, as oppose to the normal 2 years. To learn more, google ubuntu release cycle or something.

The difference in kernel number mean the revision upstream. Ask someone else who is a expert on it. Simply, left to right is ranging from minor to major revisions

---

### Post by jerome1232 on 2011-03-04
Ubuntu, Uses the Gnome Desktop Environment (the look and feel you could say)
Kubuntu, Uses the K Desktop Environment.

They both have different default installed applications that fit in well with their setup. You can install KDE apps on are regular Ubuntu install and vice versa...


Ubuntu 10.10 is the release (released October of 2010, it's a year and month of release) Just like Ubuntu 10.04  would have been released in April of 2010.

One release (ie 10.10) can have different kernels,, although I don't believe it will change major version numbers. So these are just security/stability updates.

---

### Post by pua06 on 2011-03-04
thanks so much for reply

but 
example  kernel 2.5.37 in lucid 
be not similar than kernel 2.5.37 in ubuntu 10.10?
sorry for this when u install for example ubuntu 10.10
means that install kernel when did update by terminal means that older kernel delete or change in some files?
there are  recommended book "good"to read t understand linux kernel "file system"
again thanks so much

---

### Post by idoitprone on 2011-03-04
I believe the kernel lucid and maverick are very similar as long they have the same version number. They should have the same driver and etc. Like the 2.6.36, I believe have power saving features for laptops or 2.6.23 have a different kernel scheduler. I know a little due the funny godwin flame wars Linus starts sometimes. There might be minor changes based on the distro to gear it to the certain version. Go ask the developer who know or package the kernel. 

When you update the kernel, not that many files are changed. They just add the kernel and change the grub files, in order to be able to boot off the new kernel. Ubuntu should keep the old kernel after update, in case of problems of the new kernel eg. nasty nvidia driver and etc.

About the file system, ??? dont understand what you are asking

---

### Post by WorMzy on 2011-03-04
> **idoitprone said:**
> I believe the kernel lucid and maverick are very similar as long they have the same version number.

A common misconception. The "10." merely signifies that it was released in 2010.

10.04 = released in 2010, in April (10/04).
10.10 = released in 2010, in October (10/10).
11.04 = expected to be released this April (11/04), if it gets delayed, and subsequently released in May, it'll be known as 11.05.

---

### Post by pua06 on 2011-03-04
thanks

file system=kernel right?
when install os means install kernel that's right?

 if there is good books explain file system cause i found lot of books want simple one

i downloaded this book  
           ubuntu for dummies 
           linux for dummies
           embeded linux premiere

---

### Post by WorMzy on 2011-03-04
The filesystem doesn't have much to do with the Operating System itself, it's just what the Operating System (and all your files) sits on. You could think of it as a big database which keeps track of where files are on A) the physical hard drive itself, and B) the logical hierarchy of files and folders.

The kernel is the heart of the Operating System. It sits between the hardware and the software and translates instructions between the two.

---

### Post by idoitprone on 2011-03-04
> **WorMzy said:**
> A common misconception. The "10." merely signifies that it was released in 2010.

10.04 = released in 2010, in April (10/04).
10.10 = released in 2010, in October (10/10).
11.04 = expected to be released this April (11/04), if it gets delayed, and subsequently released in May, it'll be known as 11.05.

Sorry, I worded it wrong. I mean version number comparison of the kernel between like 2.6.32 from maverick to 2.6.32 from lucid. I wasn't referring the version number of the os. It nice to know that the first 2 number refers to the year

And pua06, a file system is not a kernel. A file system is like firmware to a harddrive, which mean we need driver for access.

A kernel, too long explanation. Yes when you install an os, you also install a kernel, since os and kernel cannot live without each other. wiki a kernel

i post it too late, whatever the guy above me said

---

### Post by jerome1232 on 2011-03-04
If the version doesn't change than there is no reason for me to believe the kernel would have changed.

I suppose it's possible they could be compiled with different options? I don't know much about the Ubuntu policies on their versioning.

---

### Post by pua06 on 2011-03-04
thanks for reply more of things be clear
ok file system not kernel

when we install ubuntu i can see all file system that be like data base
kernel do translate to hardware right?
means that convert what i did to binary right?

---

