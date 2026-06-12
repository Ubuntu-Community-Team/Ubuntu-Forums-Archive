---
title: "Virtual Box / VMWare and Dell restore disk"
date: 2009-10-14
forum: General Help
---

### Post by lukew on 2009-10-14
Has anyone ever tried installing from a restore disk? Does it install correctly or does everything go to pot and you end up with how dell shiped your machine.

Thanks

Luke

---

### Post by phillw on 2009-10-14
> **lukew said:**
> Has anyone ever tried installing from a restore disk? Does it install correctly or does everything go to pot and you end up with how dell shiped your machine.

Thanks

Luke

If u mean installing XP from the Dell restore disk - I'll let you know in an hour - I'm doing just that !!
(Dimension 3100) - From memory, i think it worked okay last time i did a dell - tbh, I don't play with windows much these days !!

Phill.

p.s.  It doesn't put the drivers back on :-O
#@!£$ !!!!! (Or, words to that effect)

---

### Post by dunkar70 on 2009-10-14
are you talking about creating a virtual machine from the hardware restore disk? I have not, but I would imagine it is possible. There are posts in the Virtualbox forums for changing drivers when you want to run an installation on the hard drive in a virtual environment. The same instructions may apply as long as the restore program does not verify the "hardware" on which it is installing. The restore may cancel if it does not detect the type of hardware for which it was created.

---

### Post by rifak on 2009-10-14
i used my parents' dell win xp reinstall disc in virtualbox and it worked fine. you'll need a registration key though (the numbers are found on the bottom of any windows based computer..and im pretty sure you can use any key).

---

### Post by lukew on 2009-10-15
> **ego-sum-deus said:**
> i used my parents' dell win xp reinstall disc in virtualbox and it worked fine. you'll need a registration key though (the numbers are found on the bottom of any windows based computer..and im pretty sure you can use any key).

Thank you for firstly reading my post and secondly answering my question! ;)

That's great to know. I have a new machine turning up with vista and windows 7 restore disks (probably) and would like to use one of these to create a virtual box OS. (Before you ask

I don't suppose you know if I could dual boot with windows 7 and also use the same key for installation inside virtual box? I suspect MS have that one covered. My new laptop only has 4GB of memory and so running windows 7 in virtual box would probably not be suffice. Beside the vista and windows 7 are 64 bit and from the sounds of things the repositories (mostly 4rd party) are not fully supporting 64 bit ubuntu yet!

Thanks once again for you help; it is much appreciated.

Luke

---

### Post by P4man on 2009-10-15
> **lukew said:**
> Thank you for firstly reading my post and secondly answering my question! ;)

That's great to know. I have a new machine turning up with vista and windows 7 restore disks (probably) and would like to use one of these to create a virtual box OS. (Before you ask

I don't suppose you know if I could dual boot with windows 7 and also use the same key for installation inside virtual box? I suspect MS have that one covered.

Indeed, you can't. In fact, its even worse than that. You can not install vista in a VM legally, unless you have Vista ultimate or business.

[http://www.winsupersite.com/showcase/winvista_licensing.asp](http://www.winsupersite.com/showcase/winvista_licensing.asp)
> 
Virtualization licensing

One final area that's come under a lot of scrutiny--and, as it turns out, misguided interpretations--regards virtualization. With Windows Vista, Microsoft is finally addressing virtualization in the EULA. And it goes something like this:

Any version of Windows Vista can host virtual machines (VMs), whether in Microsoft's Virtual PC solution or a rival product like VMWare Workstation. **However, only two retail version of Windows Vista are licensed for use as a guest OS in a VM: Windows Vista Business and Ultimate.** (A third--non-retail--Vista version, Vista Enterprise, has different licensing terms, which I'll address in a bit.)

Let that one sink in for a second. You cannot install Windows Vista Home Basic or Home Premium in a virtual machine, at least from a legal standpoint. (There is nothing technical preventing you from doing so, of course.) And on a related note, each retail copy of Vista you purchase is only licensable for one install.** If you install a copy of Windows Vista in a virtual machine and then activate it, you cannot install the same copy of Vista on a physical machine and reactivate it** (unless you take advantage of the transfer rights mentioned above, of course). One license equals one installation.

Im not sure how this changed with windows 7, if at all.

>  My new laptop only has 4GB of memory and so running windows 7 in virtual box would probably not be suffice.

IT depends on your apps of course, but for most uses you'll be fine. Windows 7 is quite okay with ~1.5GB or RAM, and ubuntu typically even needs a lot less.  I got windows 7 in a VM under ubuntu with just 2 GB Ram (1.2 GB for the VM) and its quite good as long as I dont go bananas launching apps in the VM.

---

### Post by lukew on 2009-10-15
> **P4man said:**
> Indeed, you can't. In fact, its even worse than that. You can not install vista in a VM legally, unless you have Vista ultimate or business.

[http://www.winsupersite.com/showcase/winvista_licensing.asp](http://www.winsupersite.com/showcase/winvista_licensing.asp)


Im not sure how this changed with windows 7, if at all.

.

IT depends on your apps of course, but for most uses you'll be fine. Windows 7 is quite okay with ~1.5GB or RAM, and ubuntu typically even needs a lot less.  I got windows 7 in a VM under ubuntu with just 2 GB Ram (1.2 GB for the VM) and its quite good as long as I dont go bananas launching apps in the VM.

Thanks for your reply.

The version of vista and windows 7 are the 64 bit ultimate version. So 2gb of ram as a min. Also I would need to use the ubuntu 64 bit; which would then mean I would not be able to use my stanard xp home; which would probably be more useful.

ohhhh decisions decisions! ;)

Thanks once again for your help; much appreciated.

---

### Post by P4man on 2009-10-15
> **lukew said:**
> Thanks for your reply.

The version of vista and windows 7 are the 64 bit ultimate version. So 2gb of ram as a min.

Dont know if MS states that as minimum requirements, but it works fine with less. Im runnning  64 bit windows 7 ultimate here as well (RC). Dont forget windows loves to use tons of RAM as cache, but ubuntu's cache memory will help just as well, since it would cache the .vdi file (which is your windows virtual disk). Like I said, it all boils down to the windows apps you intend to run, but OS itself is quite happy (and snappy) with barely a 1GB. Give it 2 and you're golden, and still have 2 left for ubuntu, which is usually (much) more than needed.

>  Also I would need to use the ubuntu 64 bit; which would then mean I would not be able to use my stanard xp home; which would probably be more useful.


Not sure I follow you here. FWIW, you can virtualize XP home under 64 ubuntu without issues, except possibly for the legal variant. IIRC, the eula from XP did **not **disallow installation in a VM. It was however very unclear about wether or not it allowed running a single licence both in a VM and installed on the same machine. Windows vista and 7 took away that ambiguity (and on top of that disallowed any usage in a VM other than for the most expensive versions). Though I seriously doubt the EULA would hold up in court if ever challenged (breaking a EULA != necessarily breaking the law).

Regardless, there is no problem legal or other running a legal copy of  XP Home in a VM if you don't use the same licence installed on the same machine. And even the last part may or may not be legal, its unclear.

---

### Post by lukew on 2009-10-15
> **P4man said:**
> .

Dont know if MS states that as minimum requirements, but it works fine with less. Im runnning  64 bit windows 7 ultimate here as well (RC). Dont forget windows loves to use tons of RAM as cache, but ubuntu's cache memory will help just as well, since it would cache the .vdi file (which is your windows virtual disk). Like I said, it all boils down to the windows apps you intend to run, but OS itself is quite happy (and snappy) with barely a 1GB. Give it 2 and you're golden, and still have 2 left for ubuntu, which is usually (much) more than needed.



Not sure I follow you here. FWIW, you can virtualize XP home under 64 ubuntu without issues, except possibly for the legal variant. IIRC, the eula from XP did **not **disallow installation in a VM. It was however very unclear about wether or not it allowed running a single licence both in a VM and installed on the same machine. Windows vista and 7 took away that ambiguity (and on top of that disallowed any usage in a VM other than for the most expensive versions). Though I seriously doubt the EULA would hold up in court if ever challenged (breaking a EULA != necessarily breaking the law).

Regardless, there is no problem legal or other running a legal copy of  XP Home in a VM if you don't use the same licence installed on the same machine. And even the last part may or may not be legal, its unclear.

I was more referring to the fact that to use my windows vista / 7 installs under Virtual box through ubuntu as these are 64 bit versions i will need to use the ubuntu 64 bit version. However my xp version is not 64 bit.

Thanks for your help.

Luke

---

### Post by P4man on 2009-10-15
> **lukew said:**
> I was more referring to the fact that to use my windows vista / 7 installs under Virtual box through ubuntu as these are 64 bit versions i will need to use the ubuntu 64 bit version. However my xp version is not 64 bit.


Yeah I read that, but it doesnt matter, you can use a 32 bit OS client (XP) on a 64 bit host (ubuntu). No problem, no performance penalty. 

(Oddly enough with  virtualbox,  even the opposite is possible, ie, virtualizing a 64 bit client OS on a 32 bit host though Id expect a serious performance penalty there).

---

### Post by lukew on 2009-10-16
> **P4man said:**
> Yeah I read that, but it doesnt matter, you can use a 32 bit OS client (XP) on a 64 bit host (ubuntu). No problem, no performance penalty. 

(Oddly enough with  virtualbox,  even the opposite is possible, ie, virtualizing a 64 bit client OS on a 32 bit host though Id expect a serious performance penalty there).


Hay man that is really good to know. It would be good to have xp and windows 7 64 bit ultimate through VB on Ubuntu 32.

Thanks for your help.

---

