---
title: "MS Access 2007 compatible on Linux"
date: 2009-08-22
forum: General Help
---

### Post by Brian88 on 2009-08-22
Hi,

does anyone know an application for Linux which can work with Microsoft Access 2007 files? 

I need it because I have to enter data very frequently on an MS Access 2007 file. 

Thanks,

---

### Post by earthpigg on 2009-08-22
> **Brian88 said:**
> 
I need it because I have to enter data very frequently on an MS Access 2007 file. 

if it is for work, and your livelihood depends on it, and thus it needs to be completely reliable, i strongly suggest installing Microsoft Windows in a Virtual Machine instead of working with WINE or OO.o. WINE may work. OpenOffice may work. Microsoft Windows (even in a VM) *_will_* work.

virtualbox is the most popular. the open source edition is in the repos, but has retarded functionality. no shared folders, for example. you will need to e-mail the file back and forth to yourself to transfer it from your VM to Ubuntu. very annoying.

virtualbox closed source, from [http://www.virtualbox.org/](http://www.virtualbox.org/) , includes things like printer support, *_folder sharing_*, etc.

to set up folder sharing, you will need to install 'guest additions' on the guest machine.

its crummy that your employer or institution is semi-forcing you to use non-free software, but thus is life. maybe when you are running the show you can stop that nonsense?

check wikipedia for any terms above you are not familiar with.

---

### Post by Brian88 on 2009-09-01
I tried to install it on Wine but it's very hard.

I have tried VirtualBox and installed Windows XP on it, it was pretty slow so I downgraded to Windows 2000, but it's still very slow. Everything runs like in a Pentium 1 system. My processor is an aging Pentium 4 Northwood 1.6Ghz circa 2001. :D

Any way to speed it up?

---

### Post by earthpigg on 2009-09-01
virtualization *is* resource intensive, as you are running two complete operating systems *at the same time.*

the only thing i would suggest - keep the VM installed as a backup, and use google docs and/or OO.o when possible... resort to XP in VM for that 5-10% of the time that docs and OO.o fail you.

lot's of RAM is usually a very solid investment, too, and cheap. in the case of someone relient on VM, it is an especially outstanding investment. how much ram would you normally use if you just had ubuntu? how much if you just ran XP? add those two together. :\

---

### Post by QIII on 2009-09-01
I know the Linux Gods will strike me dead where I stand, but...

You have to keep a sense of non-Linux-centric pragmatism here.  If you are bound to Access (OOo is not really completely compatible, because if you use VBA modules you'd have to rewrite them...), then it would be best to do your work in a pure (hack, cough) Windows environment.  Wine apparently doesn't work and a VM can tax your system enough to make it unusable -- especially with a single core and limited memory.

If you only have the one machine but you have room enough on the hd, install Windows in a dual boot configuration and deal with the 90 seconds it takes you to switch between the Windows and Ubuntu when you want to.

Alternatively, if you have two separate machines just switch between the two -- as much of a pain as that might be.  A KVM switch might come in handy here.

If you are so inclined, have the skills and can put your .mdb on a different machine on a network, you could write a front-end application for the Linux platform and connect to the .mdb to do the data manipulation.  That's the sort of thing I can do, but it's a tall order if you haven't done a lot of development.

---

### Post by HermanAB on 2009-09-01
Just get Crossover from Codeweavers.  It works. Nuf sed.

---

### Post by QIII on 2009-09-01
Access 2000 is Bronze, and I don't see Access 2007 listed.

Bronze:  "Bronze applications generally have enough bugs that we recommend that our customers use them with caution."

Access 2007 might work at the Bronze level...

---

### Post by earthpigg on 2009-09-01
> **QIII said:**
> I know the Linux Gods will strike me dead where I stand, but...


actually, i think the Linux Gods tend to be pragmatic in nature and would thus approve of your suggestions.

the Free Software Gods, on the other hand, are setting up a special place in hell just for you :D

---

