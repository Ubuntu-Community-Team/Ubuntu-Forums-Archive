---
title: "encrypted flashdrive"
date: 2010-09-22
forum: General Help
---

### Post by richardi on 2010-09-22
Hi,
My local government employer gave me an encrypted usb flash drive which I am supposed to be able to use to take stuff home to work on. I just can't get it to work on 64bit Lucid Lynx Ubuntu. 

Its a Hypertec drive ([www.hypertec.co.uk](www.hypertec.co.uk)) using a product called encryptPLUS which they say is only compatible with windows..I can see the unencrypted cd part of the drive which contains manual and installer. I've got wine installed but wine doesn't like this .exe file. 

any idea how I can gain legitimate access to the contents and do some work 
at home?

cheers
Richard

---

### Post by robsoles on 2010-09-28
Unless hypertec supply a Linux version of their software which is compatible with Ubuntu you can only access it using windows. What I will write depends heavily on you having a copy of windows you can run. (See if you can get XP if you don't have a copy of windows already).

Checkout [www.virtualbox.org]("http://www.virtualbox.org"), Virtualbox OSE is in the repository but last I checked it won't do USB so cleanly so it is best to follow the instructions on the virtualbox website to install the closed source edition.

There is a little mucking around getting your USB stick connected through to the VM but it shouldn't present to great a challenge and you can ask what you need to as you come across it anyway :)


This is a workable way to not surrender any PCs at your house to MS and access that memory stick.

---

### Post by mastablasta on 2010-09-28
> **robsoles said:**
>  
This is a workable way to not surrender any PCs at your house to MS and access that memory stick.
 
Still you will need a full copy of windows to run it.
 
I HATE these kind of sticks!!!!!!

---

### Post by robsoles on 2010-09-28
> **mastablasta said:**
> Still you will need a full copy of windows to run it.
 
I HATE these kind of sticks!!!!!!

I've got a kingston 8Gb that used that kind of stuff but I found that I could nuke it with 'System'->'Administration'-'Disk Utility' so it didn't get it's software and manual back on itself and, if I wanted to the disk utility would encrypt the underlying file-system in a way I'd have more faith in, if I could be bothered with encrypting anyway.

I ***don't love*** those kinds of sticks either :)

---

