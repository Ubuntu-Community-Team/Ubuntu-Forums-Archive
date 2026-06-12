---
title: "HP Psc 1300 5012 communication error"
date: 2010-01-13
forum: General Help
---

### Post by clandrummond on 2010-01-13
Hi, in desperate need of help I am afraid,
Just installed Ubuntu 9.10 after vista I never want to go near windows again, I want to make it clear I am a complete novice at this, wouldn't know what a command line was if it jumped up and bit me on the bum, let alone how to edit one.

Installed an HP PSC 1300 all in one printer, system sees it, installs it without any trouble, as soon as I try to print it just hangs there in pending till it defaults and I get communication error 5012, also the message  /usr/lib/cups/backend/ hp failed.

I have removed and re-installed the printer and the latest version of hplip more than once but  am getting nowhere, the printer and cable work fine when attached to my laptop which is running xp until i learn more about Linux.

Can anyone help me as my printer is essential

---

### Post by KPDXHAM on 2010-01-13
Sorry clandrummond,
I don't have the answer to your situation. I'm learning this Linux stuff also.
One thing I'm learning here in the forum is to have patience. ;)
They say you should give at least 24 hrs before bumping your post.

Reason I'm here is that I too have a similar situation, but my printer (HP 990c) has been working fine on my network, until today. I get this also:
/usr/lib/cups/backend/hp failed
Both my pc in another room with the printer wired directly to it, and this pc (with the new problem) are up-to-date on the Update Manager. I un-installed, then re-installed the printer on this (remote?) pc, but that made no difference. :(

Here's screen pictures of the problem:
[[URL=http://img338.imageshack.us/i/49075335.png/][IMG]http://img338.imageshack.us/img338/8757/49075335.th.png[/IMG]]("http://picasaweb.google.com/CliffHammer/FailedPrinterOnLAN?feat=directlink")[/URL]

[[IMG]http://img44.imageshack.us/img44/8205/11889811.th.png[/IMG]]("http://img44.imageshack.us/i/11889811.png/")

Hopefully someone out there will be able to help us out! ;)

---

### Post by clandrummond on 2010-01-14
Well its nice to know I am not alone, my problems look exactly the same as yours,  but it seems so far that everybody out there is as confused as us or there is no fix for the problem.

Looks like I may have to go crawling back to Bill Gates

---

### Post by KPDXHAM on 2010-01-14
> **clandrummond said:**
> Well its nice to know I am not alone, my problems look exactly the same as yours,  but it seems so far that everybody out there is as confused as us or there is no fix for the problem.

Looks like I may have to go crawling back to Bill Gates

Sorry to hear that, but I've said the same thing in other posts. After needing to reformat both my pc's because I screwed something up in XP. I've reinstalled so many times in the past 8 years or so that I'd have to contact M$ to prove that I'm the owner!  ....really fired me up to try Linux! A FREE system!
After all, I had 2 pc's custom built locally (I could do it myself now) and I "paid" $$$$ for both XP Pro disks, so you would think you own the software and could reload as many times as you please without "proving" anything to anyone.
I still have XP on one drive, on each computer ONLY because I have a couple programs that will not run on Linux, even with Wine.
Also, I'm not in a big hurry regarding this printer problem because I can use either system & either computer to print from. And if I don't get an answer after a while, I'll just re-install again. Could almost do this blindfolded...;)

I would just like to see Ubuntu settle down a bit more since I want to be able to recommend it to others I know. :D

Another reason I like Ubuntu, is that it's a leaner running system and Firefox doesn't take as long to load. There's other reasons also.

---

### Post by KPDXHAM on 2010-01-14
> **KPDXHAM said:**
> Sorry clandrummond,
I don't have the answer to your situation. I'm learning this Linux stuff also.
One thing I'm learning here in the forum is to have patience. ;)
They say you should give at least 24 hrs before bumping your post.

Reason I'm here is that I too have a similar situation, but my printer (HP 990c) has been working fine on my network, until today. I get this also:
/usr/lib/cups/backend/hp failed
Both my pc in another room with the printer wired directly to it, and this pc (with the new problem) are up-to-date on the Update Manager. I un-installed, then re-installed the printer on this (remote?) pc, but that made no difference. :(

Here's screen pictures of the problem:
[[IMG]http://img338.imageshack.us/img338/8757/49075335.th.png[/IMG]]("http://img338.imageshack.us/i/49075335.png/")

[[IMG]http://img44.imageshack.us/img44/8205/11889811.th.png[/IMG]]("http://img44.imageshack.us/i/11889811.png/")

Hopefully someone out there will be able to help us out! ;)

"Update"
I made sure that my router wasn't causing this problem by doing a print job from this remote pc using XP. First I had to boot into XP on the printer that has the printer wired to it locally, then boot into XP on the remote pc and do a print job. It worked!
Then I re-installed CUPS on the remote pc since the error mentions CUPS. This didn't make any difference. Still get error.
If I do a fresh install it will probably work again since every time I've installed Ubuntu it hasn't had any problem finding the network printer and using it.

---

### Post by KPDXHAM on 2010-01-16
> **KPDXHAM said:**
> "Update"
I made sure that my router wasn't causing this problem by doing a print job from this remote pc using XP. First I had to boot into XP on the printer that has the printer wired to it locally, then boot into XP on the remote pc and do a print job. It worked!
Then I re-installed CUPS on the remote pc since the error mentions CUPS. This didn't make any difference. Still get error.
If I do a fresh install it will probably work again since every time I've installed Ubuntu it hasn't had any problem finding the network printer and using it.

After performing all of the above and got no where, I decided to do another fresh install of Ubuntu on another partition since all of the fresh installs have had no problem at all finding my networked printer.
Well, so much for that idea! :(
The install of the system went fine and now I have 2 Ubuntu's to choose from. I chose the newest one and it has the same error message as the other system has regarding a firewall when I have it search for the printer! I'm not using any firewalls with Ubuntu...
Like I said previously, XP uses the same printer on the network with no problem.... Go figure :-k

Is there "anyone" out there reading this thread that can help?

---

### Post by clandrummond on 2010-01-16
Do you know if there is a way of getting posts noticed? as it seems to be we are being ignored, maybe its something we typed?

---

### Post by KPDXHAM on 2010-01-16
> **clandrummond said:**
> Do you know if there is a way of getting posts noticed? as it seems to be we are being ignored, maybe its something we typed?

I know what you mean..... I've seen this happen on other threads also. They may have more important issues to deal with...

At present I'm still trying to sort it out. I just found this :
[http://screencasts.ubuntu.com/MoS2007/15_Connecting_to_Printers](http://screencasts.ubuntu.com/MoS2007/15_Connecting_to_Printers)

I used this link:
[768x432 Ogg/Vorbis/Theora]("http://screencasts.ubuntu.com/videos/20070915_connecting_to_printers_theora_400k_vorbis_768x432.ogg")

Interesting. Since I have xp on my host computer with the printer, I plan to boot into xp and check out my settings again even though I know it's setup for sharing.
Thing is, I'm trying to connect this second (networked) computer while I have Ubuntu running on the host computer, so I don't see what the problem would be.....it says to check firewall settings, but I have no firewall setup in Ubuntu!

---

### Post by KPDXHAM on 2010-01-16
> **clandrummond said:**
> Do you know if there is a way of getting posts noticed? as it seems to be we are being ignored, maybe its something we typed?

Okay. Apparently it's not as easy to connect the client or second computer to the host printer if the host or server computer (the one with printer connected directly to it) has Ubuntu on it also!
I booted up XP on my host or server computer and made sure it was sharing the printer. Then did the "New" printer thing on the other computer using the "Search" and when it couldn't find the printer I chose "Network Printer, Windows Printer via SAMBA" and then it located the printer and I continued with the rest of it and then printed my own test paper. I don't like to use so much ink, so I just use gedit or something like that and type "test." Otherwise the Ubuntu test page uses much more ink.
So, I know the connection is possible if I have XP running on the server,but now I'm trying to find out how to find the host IP address in Ubuntu so I can enter it in window under "Network Printer" Host:
Then, hopefully it will find the printer.
I'll let ya know what happens. ;)

---

### Post by KPDXHAM on 2010-01-16
> **clandrummond said:**
> Hi, in desperate need of help I am afraid,
Just installed Ubuntu 9.10 after vista I never want to go near windows again, I want to make it clear I am a complete novice at this, wouldn't know what a command line was if it jumped up and bit me on the bum, let alone how to edit one.

Installed an HP PSC 1300 all in one printer, system sees it, installs it without any trouble, as soon as I try to print it just hangs there in pending till it defaults and I get communication error 5012, also the message  /usr/lib/cups/backend/ hp failed.

I have removed and re-installed the printer and the latest version of hplip more than once but  am getting nowhere, the printer and cable work fine when attached to my laptop which is running xp until i learn more about Linux.

Can anyone help me as my printer is essential

Hey clandrummond,
Check this out!
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I haven't had opportunity to try it yet, but I think this will make a difference.
I tried & tried to find the IP address of my printer..even in XP, no labels on my 10 year old HP 990cse that show the IP. So.. I'm really hoping that this HPLIP thing does the trick to get the second computer connected with Ubuntu on both pc's!

---

### Post by clandrummond on 2010-01-17
> **KPDXHAM said:**
> Hey clandrummond,
Check this out!
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I haven't had opportunity to try it yet, but I think this will make a difference.
I tried & tried to find the IP address of my printer..even in XP, no labels on my 10 year old HP 990cse that show the IP. So.. I'm really hoping that this HPLIP thing does the trick to get the second computer connected with Ubuntu on both pc's!
I have tried the hplip twice, formatted re-installed the Ubuntu and started with a completely clean slate, still no joy, it detects the printer, knows its there, but cannot/will not communicate with it even though i know for certain that all the cables etc are fine.

I have to say I am at a complete loss as to what to do

---

### Post by KPDXHAM on 2010-01-18
> **clandrummond said:**
> I have tried the hplip twice, formatted re-installed the Ubuntu and started with a completely clean slate, still no joy, it detects the printer, knows its there, but cannot/will not communicate with it even though i know for certain that all the cables etc are fine.

I have to say I am at a complete loss as to what to do

Hooray! Almost.....
I followed the HPLIP automatic instructions to the tee on the host and the printer could not be found when I used the parallel connection. I completely removed HPLIP via the instructions (though I may not have had to do this), then I started over again.
This time I connected the printer via usb and things are fine now on the host computer.:D

BUT, I've tried & tried & tried a few more times..to connect my networked computer, but it can't see the host through HPLIP!!!

Someone, _Please_ help!!

---

### Post by KPDXHAM on 2010-01-19
[B]So much for Ubuntu! :(

[/B]I've spent way too many hours trying to get my network printer set-up. Now I can't even use it on the server!

So much for HPLIP and CUPS.

I'm back to XP on both pc's so I can get back to somewhat normal life.

Until I KNOW that Linux has simplified setting up a home network with HP printer and Epson scanner on the client pc, I'll be using M$ again.

When I say "simplified" I mean like when I set up my windows network without spending hours of my time.


Adios;)

---

### Post by clandrummond on 2010-01-20
Wish I could follow suit,when your printer doesn't work on a system, what good is the system!! unfortunately it means I have to buy Windows 7, what has upset me most though, well lets just say "so much for the fabled Ubuntu community support" not even one reply.
I really liked Ubuntu but as it turns out it is not yet usable and there doesn't seem to be any support available if your not a programmer. 
Well nice to meet you anyway, I expect I will be joining you back on Microsoft soon

---

