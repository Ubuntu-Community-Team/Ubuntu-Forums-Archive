---
title: "iPad support in 10.04"
date: 2010-06-30
forum: General Help
---

### Post by T. G. Cid on 2010-06-30
I can't get 10.04 to work with iPad.  My current workaround is to use a Windows dual-boot for syncing.

[LIST]
[*]iTunes on WINE has bad performance and doesn't recognize when the iPad is connected.
[*]Rhythmbox can't load songs on to the device and deleting leaves phantom entries that don't play.  In all cases, there is no error message, rhythmbox acts like everything works, showing the updated playlist.  However, none of the files are on the device.  I can confirm the windows iTunes will sync the same files perfectly fine.
[*]There's no easy way to convert or load videos in Ubuntu, google searches lead to a "wishlist" bug on Launchpad dating back to 2006 and the only workaround is re-compiling ffmpeg with faac support (my next step if no one can help here).
[/LIST]

Ultimately, I'd like to treat my iPad as a working backup of everything valuable on my main computer.  But at the moment, simple things seem impossible without giving up Linux.

---

### Post by jmjohn on 2010-07-26
Same problem here.  Except I can't even get itunes to run in wine.  Just crashes or doesn't respond.

Further, I can't get iTunes to run in VirtualBox.  Just keeps crashing there, too.

Gtkpod doesn't seem to recognize my iPad, either.

So I'm left booting to windows on raw metal.  I never resort to that. 

Anybody have any advice?

Hell and balls.

---

### Post by tilapia on 2010-08-08
The iPad, I believe, uses the new version 5 proprietary Apple database for storing files and has some kind of new hash that the developers of Linux apps haven't yet managed to reverse engineer. As a result, there's no way to do this at present. Not the Linux devs fault, of course.

---

### Post by jmjohn on 2010-08-09
Of course.  I look forward to the reverse-engineering of Apple's stupid proprietary database.

---

### Post by stegouin on 2010-09-05
I also could not get iTunes 9.2.x to run in Virtual box... 

Upgrading to latest iTunes 10 however, and voila! Everything works... albeit very slowly.. but I managed to buy an album, sync it to my iPod in vbox... then mount the iPod in Rythmbox and transfer my files over to my Rythmbox music library.

I'm also running the latest version of vbox... seems the new iTunes version 10 has addressed a few bugs that just so happened to make it work in vbox.

I might be buying the new iTouch or iPad, but was holding back given the iTunes.vbox issues...

---

### Post by jspiers on 2010-11-02
I hope someone reverse-engineers the iPad's database format soon.

Here's [another thread]("http://ubuntuforums.org/showthread.php?t=1481799") about this problem (no solutions yet).

---

### Post by Zeedok on 2010-11-08
Has anyone tried to setup a network share between their iPad and Ubuntu??

I wondered whether this would be a way to get content on and off the iPad without resorting to Windows and iTunes.

There are a few third party apps which seem to offer something like this (from what I can tell).

Has anyone tried this sort of thing??

---

### Post by da Bajan on 2010-11-09
Ok, this is not 10.04 but in 10.10 I have got access to my iPad using iTunes running in Vista that is running in Virtualbox.

Maybe not ideal, but I do have full functionality.

I hope that soon there will be a native linux program that will mirror the iTunes functionality, and for the record, I have ALWAYS hated iTunes as a program.  

dB

---

### Post by tsh on 2010-12-05
A word of caution - trying an OS upgrade of the Ipad from a VM may not work. XP under VMware certainly fails - requiring a windows box to recover it. Something to do with the USB modes used for flashing.

---

### Post by jspiers on 2010-12-08
> **tsh said:**
> A word of caution - trying an OS upgrade of the Ipad from a VM may not work. XP under VMware certainly fails - requiring a windows box to recover it. Something to do with the USB modes used for flashing.

Hmm... indeed.  I've been managing my iPad via iTunes in VirtualBox (XP guest on Ubuntu 10.04 host), and I was about to attempt the upgrade to iOS 4.2.1.  Now I'm a little concerned.  Has anyone successfully upgraded their iPad OS via iTunes on a VirtualBox guest?

I might just go ahead and try it.  I'll report back if I do...

... ok so I tried the upgrade via iTunes in VirtualBox and it didn't work.  Worse, it set my iPad into the "Connect to iTunes" mode so I had to re-partition and install XP and iTunes to get it up and running again.  Do not upgrade to 4.2 via iTunes on VirtualBox, at least not an XP VirtualBox guest on Ubuntu host.

Cheers

---

### Post by jspiers on 2010-12-08
> **da Bajan said:**
> Ok, this is not 10.04 but in 10.10 I have got access to my iPad using iTunes running in Vista that is running in Virtualbox.

Maybe not ideal, but I do have full functionality.

I hope that soon there will be a native linux program that will mirror the iTunes functionality, and for the record, I have ALWAYS hated iTunes as a program.  

dB

I can confirm this also works in Ubuntu 10.04.  Mind you iTunes is almost intolerably slow, but I am running it in VirtualBox on a netbook, so I'm kind of asking for it.

I too am very much looking forward to a native Linux program to manage my iPad.

---

### Post by gunit888 on 2010-12-11
Not sure if any of you have seen this, but it might be a solution without resorting to Wine or VirtualBox:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

I just picked up an iPad yesterday for some development work, and not having any idea what I'm doing, I'm not comfortable using that solution myself yet, but it looks like a good concept to me.

---

### Post by jspiers on 2010-12-21
> **gunit888 said:**
> Not sure if any of you have seen this, but it might be a solution without resorting to Wine or VirtualBox:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

I just picked up an iPad yesterday for some development work, and not having any idea what I'm doing, I'm not comfortable using that solution myself yet, but it looks like a good concept to me.

Thanks for the tip.  I think I tried this last month but there wasn't support for the iPad's proprietary database when syncing music files, so I used VirtualBox.  Now I have an XP partition with iTunes to handle the iPad syncing, but I am looking forward to functional iPad support in RhythmBox (or another native Linux app).  By functional, I mean that it syncs and the files actually appear in the iPod app on the iPad.

Cheers

---

### Post by alones on 2011-01-03
Same issue here... Linux-based solution do not work for me as well. I found interesting work around that has decent performance:
* Install WinXP to virtual machine (VMPlayer), I gave 2 vCPU to it and 1G of RAM
* Mount my music collection as a shared folder under guest OS (same action repeat for photo and video)
* Install iTunes and create library under that mounted folder (iTunes does disk I/O to native drive)

As the result same collection is used both by Rhythbox and iTunes.
No needs for dual boot.

---

