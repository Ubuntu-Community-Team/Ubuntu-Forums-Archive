---
title: "Wubi Installation hangs for minutes at a time"
date: 2011-10-25
forum: General Help
---

### Post by inkhaton on 2011-10-25
I installed Ubuntu using Wubi on two separate windows 7 machines. 

One 32 bit and one 64 bit. 

In both of them I have some issues with random freezing of the system. 

It seems that when I have several windows open or when firefox is downloading or some process is running sometimes the system hangs and the mouse might move but nothing I click responds and no keystrokes (like Alt-Tab or Alt-F4) have any effect. If I leave it alone for a minute or two it comes back and I can do stuff again. 

For one this is annoying and two I am worried that the installation is somehow unstable and it will ruin my underlying windows file system (as I was warned against in the documentation)

I hope anyone can tell me how I can reduce this freezing and make the system more reliable. 

Any help is appreciated!

---

### Post by oldtimer7777 on 2011-10-25
That sounds like that could be what is happening. It would be better to shrink your Windows partition and do a side by side install of Ubuntu.
When you install Ubuntu from a disk or USB live stick of Ubuntu, it will provide you with a way to shrink and do a side by side installation:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **inkhaton said:**
> I installed Ubuntu using Wubi on two separate windows 7 machines. 

One 32 bit and one 64 bit. 

In both of them I have some issues with random freezing of the system. 

It seems that when I have several windows open or when firefox is downloading or some process is running sometimes the system hangs and the mouse might move but nothing I click responds and no keystrokes (like Alt-Tab or Alt-F4) have any effect. If I leave it alone for a minute or two it comes back and I can do stuff again. 

For one this is annoying and two I am worried that the installation is somehow unstable and it will ruin my underlying windows file system (as I was warned against in the documentation)

I hope anyone can tell me how I can reduce this freezing and make the system more reliable. 

Any help is appreciated!

---

### Post by Frogs Hair on 2011-10-25
The file system may be less stable because it is in a folder inside the Windows partition . I you want to use Ubuntu for the long term use the advice above .

---

### Post by JKyleOKC on 2011-10-25
FWIW, I've noticed similar behavior in virtual machines; apparently sometimes large data transfers go into a blocked state, in which the main scheduler within either the kernel or the shell refuses to respond until the block expires. I've even seen it, rarely, in my mainline session (which is not dual-boot; pure Linux installation). 

Since the mouse still responds, and most window-manager actions take place normally (i.e. I can minimize the offending window, and other active processes do not appear to be blocked) I suspect that this is happening in the shell rather than in the kernel, but I've not located any bug reports about it on Launchpad...

---

### Post by oldtimer7777 on 2011-10-25
Yes, I see some of those behaviors in very specific situations, but not using Ubuntu 10.10 however.  The worst I have seen so far, there are problems will Banshee on 11.10 where it has completely frozen (needed a logout to resume) and where I never had that problem before in 10.10.  Hopefully they are working on this.

> **JKyleOKC said:**
> FWIW, I've noticed similar behavior in virtual machines; apparently sometimes large data transfers go into a blocked state, in which the main scheduler within either the kernel or the shell refuses to respond until the block expires. I've even seen it, rarely, in my mainline session (which is not dual-boot; pure Linux installation). 

Since the mouse still responds, and most window-manager actions take place normally (i.e. I can minimize the offending window, and other active processes do not appear to be blocked) I suspect that this is happening in the shell rather than in the kernel, but I've not located any bug reports about it on Launchpad...

---

