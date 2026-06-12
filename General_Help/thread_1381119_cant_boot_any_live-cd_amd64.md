---
title: "cant boot any live-cd amd64"
date: 2010-01-14
forum: General Help
---

### Post by DRAGSTER_TUNER on 2010-01-14
hi people, im really need help... i screwed up my system and now im needing chroot to restore it..

But here begans my endurance race!!!!

IM ABOUT 6 DAYS TRYING BURN A SIMPLE 64bits LIVE CD AND I CANT!

ERVERY ONE GIMME ERROR...EVERY!

Debian live, ubuntu, kubuntu...

I already try lots of midias...cd, dvd, lots of manufacturers...multilaser, tdk.... cd-rw, cd-r....low speeds....and nothing works!

Lots of programs (nero, isoburn, alcohool)..


Lots of different computers (3 at last) 

And simply nothing works!

Always have messagens like unable to loading kernel image or no image found or something like that...

What a hell?? This crap is not just put the cd in the tray, click burn image and boot?

You will not believe how i already try a lot of stuffs...

I need a 64 bits because the chroom system!

Some clue about how burn a simply live cd to boot?

---

### Post by audiomick on 2010-01-14
Hallo. Sounds like a real pain.
have you been trying to use the same iso image all the time?

If you haven't already, read this
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and particularly the link about the MD5sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

These are the normal steps in short:
download the iso
do the MD5sum check
burn the cd
   -do not use a cd-rw
   -do use the lowest possible burning speed

boot with the cd in the drive and choose the cd check option to let the cd check itself.

If you have done all of that, the problem might be with the system you are trying to start with it.

---

### Post by akakingess on 2010-01-14
I am at a loss as well, unless for some reason you are not choosing to burn it as an ISO image, I use Active ISO Burner within Windows, and Brasero within Ubuntu, but just be sure that you are choosing to burn it as an ISO, in other words, you are not just burning data to the CD, you are in affect turning the blank CD into the ISO that you have downloaded, and remember that some burning apps won't burn ISOs, or at least not correctly. I see in the list of software that you have tried is isoburn, which I would assume do the trick, but be sure that you are not doing just a simple burn to disc, but rather an ISO burn and in a sense turning that disk into the ISO that you have downloaded. I by no means am trying to sound condescending, just want to make sure all of the bases are covered, because it seems that you have tried everything. Also, what size is the ISO, if it is too large for a CD, than it may be a DVD ISO. Good luck and please don't take any of my suggestions the wrong way, just intended to assist and rule out some of the simple stuff.

---

### Post by DRAGSTER_TUNER on 2010-01-14
But here is the issue thats driving me crazy:

I EVEN SEE THE SPLASH SCREEN WITH THE OPTIONS!

therefore, i think the burn is ok...isnt it?

all the time i click in some option (check disk, memtest, install, run without install etc), the led of the drive just give a flash and stop...the disk beggans to run and stop at miliseconds after.

I already test three or more isos from debian-live, kubuntu e ubuntu, in three different computers...

And one of them im sure is 64 bits, whos is this mine that im trying to restore.

I cant understand!

:(

---

### Post by mister_playboy on 2010-01-14
Can you boot from USB?  If so, you could use the USB Startup Disk Creator to write an ISO to a USB drive.  This eliminates any problems from read errors caused by either the CD or the drive.  This should be doable from either a Linux or a Windows computer.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

