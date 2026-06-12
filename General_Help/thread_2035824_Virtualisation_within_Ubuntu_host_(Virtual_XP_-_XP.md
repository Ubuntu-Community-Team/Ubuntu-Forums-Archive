---
title: "Virtualisation within Ubuntu host (Virtual XP - XP-mode)"
date: 2012-07-31
forum: General Help
---

### Post by tonyppe on 2012-07-31
Hi all, 
Firstly hi I am new and have been a bit of a lurker for some time. A couple of weeks ago my SSD drive died in my laptop and have decided I want to utilise Ubuntu 100% if at all possible. I have a lovely Ubuntu 64 bit 12.04 setup going, as a dual boot with Win7 64 bit just in case. My problem is that for some of my work I need to use applications that are only made for Windows. Sometimes those applications don't even work too great in Windows 7 either (Cisco applications for example).

For this reason I always have used XP mode as a secondary machine. Kind of like a phone-a-friend for Windows 7. I use the freely available XP mode from Microsoft which uses Virtual PC.

Now, my question is, is there a program I can use within Ubuntu that will run the same VHD file that is used from Windows 7 in XP Mode? 

My reasoning is that if so then I will not need to maintain two separate virtual machines. If I MUST switch back to Windows 7 then I can work from the same virtual XP machine as I have always done. 

Sorry for the long winded post and thanks in advance!

Regards,

---

### Post by collisionystm on 2012-07-31
I just tested for you.

It will run in Vmware Player. Not Virtualbox.

However.... You will get a blue screen in Vmware because XP is looking to load a harddrive controller that no longer exists.

You would essentially need to delete the problematic files using a live session of linux inside of your new virtual xp. You then boot Xp like normal and install the vmware tools which will load the correct drivers.

See here...

[http://www.wilderssecurity.com/showthread.php?t=262885]("http://www.wilderssecurity.com/showthread.php?t=262885")

---

### Post by tonyppe on 2012-07-31
Hi,
Thanks for testing this for me and thanks for the links. 
 
Would it not be easier to just boot up XP Mode under Virtual PC / Windows 7. Then install VMWare tools?

---

### Post by collisionystm on 2012-08-01
> **tonyppe said:**
> Hi,
Thanks for testing this for me and thanks for the links. 
 
Would it not be easier to just boot up XP Mode under Virtual PC / Windows 7. Then install VMWare tools?


No because the Windows registry still had the specific 'hard disk controller driver' loaded.

Installing Vmware tools in that situation will do nothing more than add the pool of available drivers.... either way you are going to have to manually delete the files in that article.

---

