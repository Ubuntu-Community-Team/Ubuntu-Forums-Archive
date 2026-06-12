---
title: "Should I Install  Ubuntu with Wubi or Virtual Box?"
date: 2011-01-24
forum: General Help
---

### Post by ranveerj on 2011-01-24
Hi, I have a Dell XPS 1530 (320GB, 7200 rpm HDD, 4GB RAM, 2.4GHz Core 2 Duo) with Windows 7 ultimate (64-bit) installed on it.

I wish to learn Ubuntu and I am totally new to it. It would be a great  help if experts in the filed can answer my questions. They are:

1. Should i install 32-bit or 64-bit Ubuntu? And why?

2. Will it be a good idea to install Ubuntu in Windows using Wubi? Or  shall i use Virtualbox and install Ubuntu as a virtual machine?

3. If i opt for the second option (VB), then would the RAM allocated to  Ubuntu, will always be reserved or it will be available for Windows when  VB is of/hibernated?
   
Thank you all in anticipation.
Best,
Ranveer

---

### Post by w1ll1am on 2011-01-24
1. In my experience I would have to say that the 32-bit version seems more stable but the 64-bit allows you to utilize all 4gigs of RAM you have installed and chances are you will not have major problems with the 64-bit. (my problems were very minor there is a chance the download was faulty I did not know check md5sum in the beginning)
 
2. I have installed Ubuntu as a VM never using Wubi but from what I have heard and read about Wubi it would be a good way to experience Ubuntu with little work. Using virtual box can be nice but it does use up more RAM and when the virtual OS is running it automatically uses so much RAM not the full amount you specified but always some. Another good thing about virtual box is you can switch between windows and Ubuntu quickly. 

3. When virtual box is off no RAM is being used when it is paused I believe it still uses some but not much.

I would say the safest quickest way would be using a VM and if you find that you like it install onto your hard drive by shrinking your windows partition down from an Ubuntu live cd or live USB and dual boot your machine. 

If you decided that you like it which I hope you do because it is the greatest OS on the planet and need help installing onto you hard drive you can send me a private message and I will give you instructions or search the forum because I am sure there are instructions on how to dual boot windows and Linux.

Good luck

---

### Post by Frogs Hair on 2011-01-24
1. I have always used 64bit with out any problems and Wubi installs 64bit by default.
 
2. Wubi is made for people who want to try Ubuntu without having to set up a traditional dual boot , it installs inside Windows and is simple to remove.  If you download the iso you will have the option of running from the disk you make ,  using Wubi from the disk, or installing a traditional dual boot.
If you like Ubuntu you will already have a disk.
 
3. I have never used VB , so I will leave that for someone who has.

---

### Post by Joe of loath on 2011-01-24
Wubi and VB are two different solutions.

VB allows you to run Ubuntu and Windows at the same time, with Ubuntu windowed. Good for testing, pointless if you want to make it your regular OS.

Wubi is essentially a dual boot install, without having to fiddle around with partitioning. You have to reboot to use it.

---

