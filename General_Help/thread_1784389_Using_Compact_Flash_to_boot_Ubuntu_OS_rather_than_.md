---
title: "Using Compact Flash to boot Ubuntu OS rather than HDD"
date: 2011-06-16
forum: General Help
---

### Post by jukingeo on 2011-06-16
Hello All,

Of late I have been doing experiments with using computers for specific tasks.  For example, I have a game room and I want to use MAME as well as a jukebox program.

Being a fan of Ubuntu (Studio) for some time now, I have tested SDLMAME and also my jukebox program (under Wine) and I found I need a very fast computer to pull it off.

So I decided to bounce back to a stripped down version of Windows XP (using nLite) for my projects.   I actually did get everything set up on my spare computer and overall it seems to be working fine, but then I read something that shot my plans down out of the sky in one swift blow.

As it turns out, Compact Flash cards have a limit to the amount of writes that can be made to it.  But reading is OK.   Most of my work is based on reading files only, but I was told that using Windows XP, that "it doesn't matter".  Windows XP has so many operations going on that it is constantly reading and writing to the hard drive. Such an action on a Compact Flash driver would certainly destroy the compact flash card in short order.

So this now puts a limitation on my using Windows XP as an operating system for my project.  I have heard that there is Windows XP Embedded, which specifically can be set to not allow writes to the hard drive (Compact Flash in my case).  But I am worried that Windows XP Embedded would be a steep purchase.

So what does this all have to do with Ubuntu?  Well, I am thinking about falling back on my original plan to use Ubuntu, but I am wondering if Ubuntu constantly needs to write to the hard drive.   As it stands I am currently writing this on an Ubuntu Studio (10.04) machine and the hard drive light steadily flashes once per second.  If Ubuntu does constantly write to the hdd, is there a way to turn stop it from doing so?  In other words, once I set up my system, could I make the main OS hard drive read only?  If so, then it would seem that I would have made my choice in OS for my project.

The last alternative I was thinking about was going with DOS (FreeDos), but this seems to be very limited in regards to what I can do with USB as well as with using more modern programs.  The good thing about DOS is that it is a perfect OS candidate for my "conditions" in the fact that it is a small OS that doesn't constantly need to write to the OS partition.

Any advice would be much appreciated.

Thank You,

Geo

---

### Post by janmyszkier on 2012-01-26
Well, I'm using CF card for my /boot partition. And I set my fstab to not do checks on that card so there are less writes. 
If you're not going to change anything (like update-grub or installing new kernels) you could propably mount this partition to 'ro' mode which is read-only and save even more writes.

---

### Post by C.S.Cameron on 2012-01-27
I have never heard of anyone in these forms bricking a decent flash drive running Ubunru from it.

A flash drive is good for 10000 writes, at 10 MB/s that is:
16 GB x 10000 / 10MB/s = 111 forty hour work weeks.*

See also:

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

I have been using XP running off of a Kingston flash drive for my living room intertainment center for over 3 years now.

(only because I can't get Ubuntu to see the S-Video port on the Mini ITX MB).


Edit:
* That is writting 40 hours per week full time.

---

### Post by jukingeo on 2012-06-23
> **janmyszkier said:**
> Well, I'm using CF card for my /boot partition. And I set my fstab to not do checks on that card so there are less writes. 
If you're not going to change anything (like update-grub or installing new kernels) you could propably mount this partition to 'ro' mode which is read-only and save even more writes.


WOW!  This was an old post that initially no one replied to and I forgot about it.  I just came back after a long hiatus to look at some of my posts and noticed that I had a reply to this one.

Ok, so how do you use fstab and 'ro'?

> **C.S.Cameron said:**
> I have never heard of anyone in these forms bricking a decent flash drive running Ubunru from it.

A flash drive is good for 10000 writes, at 10 MB/s that is:
16 GB x 10000 / 10MB/s = 111 forty hour work weeks.*

See also:

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

I have been using XP running off of a Kingston flash drive for my living room intertainment center for over 3 years now.

(only because I can't get Ubuntu to see the S-Video port on the Mini ITX MB).


Edit:
* That is writting 40 hours per week full time.

3 years huh?  Sounds pretty good, but lets see what happens in year 4.  Windows is BAD for flash drives as the OS CONSTANTLY is writing to the HDD.  However, as it stands, there is a way to set up Windows using something called EMS.  It basically converts the Windows OS to a read only setup and all changes are discarded rather than saved to the hard drive.  This basically eliminates ALL writes to the flash drive.  And yes you can turn it off to make updates and then re-enable it.

Now that is fine and dandy for my gaming systems which do use Windows, but for most of my other work, I use Linux.

I did think about if there way was to 'can' a read only system on a DVD which I can then use to set up on a flash drive on a per given system.  I figured doing it this way, I can have a 'canned' set up that I can use on just about any computer I wish.

Thanx,
Geo

---

