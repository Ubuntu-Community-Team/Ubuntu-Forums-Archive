---
title: "external optical drive icon disappears when inserting disk"
date: 2011-01-31
forum: General Help
---

### Post by davidstoll on 2011-01-31
I have an external CD/DVD usb drive and as soon as I insert a disk (I've tried both CD and DVD), the drive icon disappears (unmounts?).

I thought it was a bus power issue because it is a mini laptop (Asus Eee PC).  This small/slim external drive has two USB cables, one for power and one for power/data.  So, I plugged the power cable into my nearby Windows desktop computer and just the power/data into the Ubuntu PC.  Same issue.

It works in Windows.

I'm running 10.10 32bit and I have gotten all the updates as of today via apt-get.

---

### Post by TeoBigusGeekus on 2011-01-31
Can you post us the output of 
```
lsusb
```
both before and after you insert a cd/dvd?

---

### Post by coffeecat on 2011-01-31
@davidstoll, this may or may not be relevant to your situation but because I'm going to log out soon I'll post it now. If the lsusb command TeoBigusGeekus suggests gives you a line something like this:

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```... then look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

The Bus and Device numbers may be different, but if you get the same ID number (05e3:0701) then that thread will tell you all you need to know. The first post  is little more than a rant, but there's some useful discussion with other forum members and I've posted some workarounds.

If you don't get 05e3:0701 in lsusb, then ignore this post. :)

---

### Post by davidstoll on 2011-01-31
> **coffeecat said:**
> @davidstoll, this may or may not be relevant to your situation but because I'm going to log out soon I'll post it now. If the lsusb command TeoBigusGeekus suggests gives you a line something like this:

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```... then look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

The Bus and Device numbers may be different, but if you get the same ID number (05e3:0701) then that thread will tell you all you need to know. The first post  is little more than a rant, but there's some useful discussion with other forum members and I've posted some workarounds.

If you don't get 05e3:0701 in lsusb, then ignore this post. :)


That is indeed my issue.

Bus 001 Device 005: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter

I'm glad you mentioned that posting.  Based on the search terms I was using to describe my issue, I don't think I would have run across that post.  Thank you.  ):P

So, I have moved my further discussion to that thread....regarding how to make it run that mount command automatically when I plug in the drive.

---

### Post by coffeecat on 2011-02-01
> **davidstoll said:**
> So, I have moved my further discussion to that thread....regarding how to make it run that mount command automatically when I plug in the drive.

I'll move over to that thread to make a comment. Perhaps I should  ask a member of staff to rename it to the ID 05e3:0701 Genesys Logic megathread! :wink:

---

### Post by TeoBigusGeekus on 2011-02-01
Good to have you with us coffeecat :D

---

### Post by coffeecat on 2011-02-01
> **TeoBigusGeekus said:**
> Good to have you with us coffeecat :D

Good to have you around as well, TBG. :D

It was the thread title that enticed me to take a look at this thread. I thought, "Aha, that sounds familiar." A lesson to all those who start threads with titles like 'Help!!!!!!!!' or 'Arghhhhh!!!!!', if only they would take heed.

---

