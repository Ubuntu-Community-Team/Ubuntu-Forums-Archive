---
title: "VirtualBox?"
date: 2009-10-22
forum: General Help
---

### Post by sponsoredwalk on 2009-10-22
Erm, Virtualbox. From all my googling I'm not 100% sure what it is and whether it's actually what I think it is. Let me see,

**1:**When I get the new Ubuntu in a week and install virtualbox on it, while I'm in ubuntu, will I be able to open the windows vista part of my computer from inside a window?

**2:**If "Yes" to the above, Would I be able to run a program like Cubase from this window, would it be powerful enough?

**3:**Could I run Linux from windows via Virtualbox?

**4:** Could I run hydrogen or even Rosegarden from my virtual window in windows (assuming it's possible to even try)?

**5:**Usually there's a problem viewing the other operating system. I mean, when I had wubi install ubuntu 9.04 I couldn't access windows when I was on linux and Linux was an unopenable folder in my d drive while on windows. How does this affect it?

:tongue: Please let me know, Gratias Vobis Ago :tongue:

---

### Post by nerdistmonk on 2009-10-22
Well a short description of what is and does is this:

Its a virtual computer, it lets you setup up a "fake" machine with a certain amount of memory and Harddisk space, then it will let you load an operating system onto it (Either Windows, Linux, BSD what ever) 

The OS you load onto "thinks" its on a real computer, and you can use the OS on your desktop like its another program window,


Well there, I tried....


and yes if your using windows and install virtualbox, you can install linux into virtualbox

---

### Post by sponsoredwalk on 2009-10-22
Wow, that's amazing. But how does it access my vista and is using Cubase 4 out of the question?

---

### Post by Simian Man on 2009-10-22
> **sponsoredwalk said:**
> **1:**When I get the new Ubuntu in a week and install virtualbox on it, while I'm in ubuntu, will I be able to open the windows vista part of my computer from inside a window?
No.  Virtualbox lets you create a new virtual machine (vm) which you can install an OS such as vista on.  It uses a file stored on your computer as the virtual hard disk for this vm.  It won't let you run an OS off another partition.  If you mount this partition, and share it with your VM, you can access the file there however.

> **sponsoredwalk said:**
> **2:**If "Yes" to the above, Would I be able to run a program like Cubase from this window, would it be powerful enough?
I've never heard of cubase before, but google tells me its a music production tool so yes, if you have at least 2 gigs of RAM, you should have no problems at all running it under a VM.

> **sponsoredwalk said:**
> **3:**Could I run Linux from windows via Virtualbox?
Yes, but not the installation on your other partition (as I explained earlier).  You can setup VMs under Windows and put Linux on them.

> **sponsoredwalk said:**
> **4:** Could I run hydrogen or even Rosegarden from my virtual window in windows (assuming it's possible to even try)?
I don't know what those are either, but any Windows program will run fine under a VM except for high performance games (though they are working on that too!).

> **sponsoredwalk said:**
> **5:**Usually there's a problem viewing the other operating system. I mean, when I had wubi install ubuntu 9.04 I couldn't access windows when I was on linux and Linux was an unopenable folder in my d drive while on windows. How does this affect it?
You should be able to see your Windows drive under Linux because Linux supports Windows' NTFS filesystem.  I have heard it's possible to access your Linux partition under Windows by installing an ext userspace driver, but I've never tried it.


In general, you'd use Virtualbox *instead* of a dual-boot, not in addition to it.

---

### Post by P4man on 2009-10-22
No. You have to (re)install the OS inside the VM, you can not just boot an installed OS in the VM. Think of the VM as a separate and new machine.

You could install vista or any windows on a VM and run windows software on it. It works better than youd think, except for 3D acceleration, and I fear sound might be problematic for professional purposes. It works, but I dont know if it works well enough for things like cubase. Virtualbox virtualizes a very primitive soundcard (soundblaster 16 or AC97).

I dont know any of the other apps you listed, but generally speaking a VM would run close to the native speed of native apps (3d excluded). You just need enough RAM for the host and client OS.

As for the other way around. Sure you can install ubuntu on a VM hosted by windows with the same caveats.

---

### Post by sponsoredwalk on 2009-10-22
I see, well thanks very much for the answers, very thorough. Mayhaps I'll try linux mint in a vitual machine from vista and see how it goes, as a way to pass the time till next week lol.

(Smiley time\\:D/)

:-({|=  :-({|= \\:D/\\:D/

---

### Post by tacantara on 2009-10-22
> **sponsoredwalk said:**
> Erm, Virtualbox. From all my googling I'm not 100% sure what it is and whether it's actually what I think it is. Let me see,

**1:**When I get the new Ubuntu in a week and install virtualbox on it, while I'm in ubuntu, will I be able to open the windows vista part of my computer from inside a window?

**2:**If "Yes" to the above, Would I be able to run a program like Cubase from this window, would it be powerful enough?

**3:**Could I run Linux from windows via Virtualbox?

**4:** Could I run hydrogen or even Rosegarden from my virtual window in windows (assuming it's possible to even try)?

**5:**Usually there's a problem viewing the other operating system. I mean, when I had wubi install ubuntu 9.04 I couldn't access windows when I was on linux and Linux was an unopenable folder in my d drive while on windows. How does this affect it?

:tongue: Please let me know, Gratias Vobis Ago :tongue:

**Simian Man beat me to the answer.**  [B]I'm glad that you got this solved :)
[/B] 
1.  You install the OS inside of VirtualBox, on a "virtual drive."  To run the Windows OS, you open up VirtualBox and select the OS that you installed.  So, essentially you are running Windows in a separate window within Ubuntu.

2.  Once you have your virtual Windows machine set up, you can install programs on the virtual drive, just as you would if you were running it normally.  I have several programs on my XP virtual machine that have no viable Linux equivalent.

3.  Sun, the makers of VirtualBox, have a version that you can install in Windows.  If you choose to go that route, you can set up a Linux virtual machine.

4.  See answer #2.  Once you establish a virtual machine, you can install any programs designed to run on that machine's OS.  Caveat - graphics-intense programs (i.e. games) may not run well due to system constraints in the virutal environment).

5.  I don't foresee any problems with the Wubi installation if you add VirtualBox.  However, wubi was designed to allow you to run two OSes, but not simultaneously.  IMO, adding VirtualBox seems superfluous.  You may want to backup your data, then do a clean install of your host OS, then install the appropriate version of VirtualBox and set up a guest OS on it.

I hope this clarifies things a bit for you.

---

### Post by Ocxic on 2009-10-22
Actually you can give Virtualbox access to a hardrive and your current windows install BUT: I would NOT recommend it, as if you do give it access you can't boot windows normally as it will screw up virtual box, and I'm sure windows would have a fit trying to install all of the drivers for the new virtual hardware.

I would recommend creating an empty partition on your drive for Virtualbox to use as it is better performance wise then using a virtual hard disk.

If your interested read the virtual box manual, for instructions.

---

### Post by The Cog on 2009-10-22
Here is a screenshot that might give you an idea of what virtualbox is...

---

### Post by sponsoredwalk on 2009-10-22
Yep, thanks a lot. I'll try linux on the virtual machine. Seems to me to be a pretty good as I can use the linux hydrogen drum programme from the virtual machine then export those files (when made) to cubase and mix properly. That's awesome, you've saved me a lot of time just restarting the laptop to switch os'.

Magni Gratias Vobis Ago

---

### Post by sponsoredwalk on 2009-10-22
> **Ocxic said:**
> Actually you can give Virtualbox access to a hardrive and your current windows install BUT: I would NOT recommend it, as if you do give it access you can't boot windows normally as it will screw up virtual box, and I'm sure windows would have a fit trying to install all of the drivers for the new virtual hardware.

I would recommend creating an empty partition on your drive for Virtualbox to use as it is better performance wise then using a virtual hard disk.

If your interested read the virtual box manual, for instructions.

 No way, I wouldn't even chance it. No I'll just get mint going from within Vista that I'm on now. Should I have any problems I'll be back. 
 
On a side note: Your using your original XP Installation disk to install on the virtualbox right? A few questions;

**1** I don't have my Vista CD, bought the laptop second hand 2 days ago. The guy I bought it off said I could make a backup cd (however that's done) but if I were to do that would the program would give you the chance to do this and install it all inside the window? (I only ask as I wouldn't waste all that time now rushing to make the cd only for it to not work)

**2** Wouldn't it take forever, what with service packs and the day long initial installation. :-&

---

### Post by P4man on 2009-10-22
> **sponsoredwalk said:**
> 

**1** I don't have my Vista CD, bought the laptop second hand 2 days ago. The guy I bought it off said I could make a backup cd (however that's done) but if I were to do that would the program would give you the chance to do this and install it all inside the window? (I only ask as I wouldn't waste all that time now rushing to make the cd only for it to not work)

You mean one of those recovery cds/dvds. They probably wont work. they only work on the original hardware and the vm is a different machine. Which also means you're gonna have trouble with licences. You need a windows licence for both the VM and the normal install if you want to keep that. Worse yet, many versions of windows you're not allowed to install inside a VM period if you follow the EULA. Youd need the expensive premium or enterprise editions.
> 
**2** Wouldn't it take forever, what with service packs and the day long initial installation. :-&[

Yes. Especially with XP.  Youll spend most of the day installing service packs and drivers and essential tools. On the bright side, its in a window so you can do other work at the same time :)

---

### Post by sponsoredwalk on 2009-10-22
Yeah I wouldn't waste my time or my ram installing a virtual windows then, way too much hassle for too little.

However, I'm about to get Linux Mint but It says it's DVD under "Media" on this page [http://www.linuxmint.com/edition.php?id=40](http://www.linuxmint.com/edition.php?id=40)
Will this be a problem or should I get .ISO only? Again I wouldn't ask but it is 1.3GB of bandwidth, time and space I can save by askng. If it doesn't work I could just try out Fedora or Redhat or some other linux distro.

---

### Post by sponsoredwalk on 2009-10-22
oh god it is an iso file. I'm being too cautious, disregard any future worries lol :tongue:

---

### Post by []D.[].[]\/[].[]D on 2009-11-07
Hey,
did you manage to get Cubase working properly with virtualbox?
I'm trying to do the exact same thing and found this page through google.
My worry is that the latency on the soundcard will be too high because someone here said the soundcard beng simulated is quite old.

What was your expereince?

Thanks!

---

