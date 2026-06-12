---
title: "Possible to update Android version using Ubuntu?"
date: 2011-03-26
forum: General Help
---

### Post by t0p on 2011-03-26
A friend has an Android smartphone - LG GT45 I think - it's currently using Android version 1.6 and she wants to update to 2.1 or whatever.  But she doesn't own a computer.  So she came to me for help.

I only use Ubuntu, but I also have XP as a VirtualBox guest.  I've installed the LG updating program, and it works fine through the handset verification stage, downloads the software; but when we get to the install stage it will only get to 4% on its progress bar then stops there.  We wait and wait, it doesn't get any further, then eventually my virtual XP just freezes up.

I'd like to help her.  So if there is a way to do this natively in Ubuntu, maybe we can get her Android version updated.  Anyone know?

---

### Post by t0p on 2011-03-29
Bump

---

### Post by Kirboosy on 2011-03-29
Maybe [Unrevoked]("http://unrevoked.com/") will do the trick? I've never used it because I have a BlackBerry. :(

I know with my BB I can't use VB because it loses connectivity at a certain point in syncing the device

~Caboose

---

### Post by t0p on 2011-03-29
No, it looks like Unrevoked works only with a small selection of phones; and my friend's LG isn't one of them.

Can anyone help?  Surely a Linux-based OS like Android can be upgraded using a computer running Linux?

---

### Post by earthmeLon on 2011-03-29
I am not too familiar with updating androids, but...

Be careful:   Many android phones are locked into their version for hardware reasons.  It also has something to do with which applications they can run and such.

It may cause much instability to do such an upgrade.

---

### Post by t0p on 2011-04-01
> **earthmeLon said:**
> I am not too familiar with updating androids, but...

Be careful:   Many android phones are locked into their version for hardware reasons.  It also has something to do with which applications they can run and such.

It may cause much instability to do such an upgrade.

I get what you're saying; but the fact that LG has created an upgrading tool says to me that upgrading Android version *is* possible.

My problem is that the LG upgrading software is available only as an *.exe* file, and I don't have a Windows-running computer.  So I need an upgrading tool that will work with Linux (Ubuntu preferably, but I do know how to compile software, or how to use *alien* to convert a *.rpm* into a *.deb*).  So I really really need a link to a Linux version of the tool.  Anyone?

---

### Post by ojdon on 2011-04-01
Don't suppose you're able to actually upgrade it on the phone? 

On stock Android you go to something like Setting>About Phone then somewhere in there should be a Software Update option, with a "Check now2 button on the bottom of the menu. Though that might be for HTC Android phones since I've only had Android on a HTC.

---

### Post by tgm4883 on 2011-04-01
Find out the actual model of the phone. Google doesn't know what a LG GT45 is.

I would probably
1) Get root
2) Install rom manager
3) Install boot loader
4) Load custom ROM from boot loader

If you want to stick with stock, you will need to use their tool and need to do it from Windows

---

### Post by earthmeLon on 2011-04-01
My suggestion would be to run a windows virtualization under VirtualBox or VMWare.  There is good USB and such support in it.  You could then run it from within that virtualization?

However you do it, be sure to let us know :D

---

### Post by andrew.46 on 2011-04-02
I went through the same process a while back trying to update an HTC Legend with Froyo. The update software did not work properly using Windows 7 in VirtualBox and I will have to admit that I eventually found a full Windows 7 installation and upgraded from there :(. Froyo was definitely worth the effort though, pity I failed to get Linux to do the job though...

---

### Post by 3rdalbum on 2011-04-02
For starters, LG must approve any new Android versions for its phones, and then push out the update. So, this phone might be stuck on 1.6.xx unless LG makes a later version available.

And secondly, you shouldn't need to use an updating tool on your computer, just use the updater that's already built-in on the phone.

---

### Post by tgm4883 on 2011-04-02
> **3rdalbum said:**
> For starters, LG must approve any new Android versions for its phones, and then push out the update. So, this phone might be stuck on 1.6.xx unless LG makes a later version available.

And secondly, you shouldn't need to use an updating tool on your computer, just use the updater that's already built-in on the phone.

Not all phones allow over the air upgrades

---

### Post by Mark Phelps on 2011-04-02
> **tgm4883 said:**
> Not all phones allow over the air upgrades

In addition, the OP mentioned that LG does not provide any newer upgrades.  He is trying to FORCE 2.1 onto her phone.

To the OP, you sure the Updater allows for OS updates?  Some of those utilities only allow you to update the phone with Andriod apps offered outside of the Market.  They are not intended for OS updates.

And even then, they often require that you have "rooted" the phone first -- in order to have the permissions needed to replace the system files.

---

