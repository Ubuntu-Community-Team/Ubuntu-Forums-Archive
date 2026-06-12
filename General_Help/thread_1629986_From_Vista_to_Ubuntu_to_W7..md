---
title: "From Vista to Ubuntu to W7."
date: 2010-11-24
forum: General Help
---

### Post by OlimarandLouie on 2010-11-24
Skip down to the link and large sentence if you don't want to read the story.

-------------------------------------------------------------------------------------------

I began with Vista.

Last Thursday evening, when I was about to turn off the computer and go to sleep, the shutdown button said something-or-another close to "Click this to install updates and shutdown your computer."

Naturally, I clicked it, then saw the "installing update 1 of 3". I turned off the monitor and went to bed.

Lo and behold when I came back Friday morning, it was still turned on.

Confused, I turned on the monitor, and saw the pre-login screen which said "configuring update 3 of 3: 0%".

I gave it no second thought, and I was about to go do something for 15 minutes when I saw it briefly flash to my login screen, then immediately say "shutting down".

I waited a few seconds for something to change. The computer shut down, then immediately restarted and soon after said "configuring update 3 of 3: 0%", then a brief one-second flash of my login screen, then "shutting down" again.

Apparently it had been stuck in an endless loop all night.

I tried each and every one of the startup options (safe mode, normal, etc.) but it performed the same loop told above. One option, "last known good setup", showed a text wall of windows starting up each of its individual .system files, and when it got to one in particular, (for the life of me I can't remember which one), it stopped, then continued to follow the loop.

I then assumed that my OS was broken and I needed a new one, because there was an important school project I needed to get done on Microsoft PowerPoint (No I couldn't use anything else). I didn't have the money on me at the moment to get a Windows OS at the time.

I burned the ubuntu OS onto a cd from my other computer, and installed it on this computer with no problems (although I had to delete all of Windows Vista)

A few days later, I acquired the money to buy Windows 7, I put the files on an empty 60 gb external hard drive, because it wouldn't work for some reason on the CD.

(Lots of crazy stuff that I now realized was completely unnecessary happened here over the course of 5 hours)

I downloaded WINE so I could run the setup.

The setup ran, then...

-------------------------------------------------------------------------------------------

[http://oi51.tinypic.com/jubxph.jpg](http://oi51.tinypic.com/jubxph.jpg)

[SIZE="5"]No freaking clue how to "partition" 689+ MB for the Windows 7 install program to do it's thing.[/SIZE]

*Note* It wouldn't work if I set the priority to USB in the BIOS thing.

*Note* I already have a computer with ubuntu on it. This one is supposed to be my Windows computer. (Also I lost the Vista install disc a long time ago)

---

### Post by blueridgedog on 2010-11-24
> **OlimarandLouie said:**
> I downloaded WINE so I could run the setup.

You do not run the setup for Windows7 from within Ubuntu.  If it is your plan to install Windows7 over Ubuntu, just boot of the disk and follow the instructions.  If you want to setup a dual boot, you should use gparted to reduce the size of the Ubuntu partition in order to make room for a Windows7 partition.  If you explain what your end goal is (clean in stall or dual boot), then perhaps I and/or others can suggest a path forward.

If you want to dual boot, this is a great place to start:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you just want to do a clean install of Windows, you should be able to do that by booting off of the install media.

---

### Post by RJ12 on 2010-11-24
Have you tried booting from the CD? Your not suppose to run the Windows Setup in Wine. You can however install it in a VM, or boot from the Setup Medium (whatever you have the setup on) and install Windows 7.

Edit: I would just follow what blueridgedog said. :)

---

### Post by OlimarandLouie on 2010-11-24
My ultimate goal is to either

A - Erase Ubuntu entirely with Windows 7 (since I already have another computer that runs it). (Preferably)

or 

B - Dual-boot W7 and Ubuntu

Whichever is easier I'll go with.

---

### Post by blueridgedog on 2010-11-24
> **OlimarandLouie said:**
> My ultimate goal is to either

A - Erase Ubuntu entirely with Windows 7 (since I already have another computer that runs it). (Preferably)

or 

B - Dual-boot W7 and Ubuntu

Whichever is easier I'll go with.

If you want to dual boot, my feeling is that it is always easier to start with a clean windows install.  So, in your case I suggest you boot off of the Windows7 install disk and do a clean install.  

When you get to the install portion that deals with disks and partitions, delete all the existing partitions and then create a new "C" drive.  Here is a great site that has images of the process:

[http://pcsupport.about.com/od/operatingsystems/ss/windows-7-clean-install-part-1_11.htm](http://pcsupport.about.com/od/operatingsystems/ss/windows-7-clean-install-part-1_11.htm)

---

