---
title: "Ubuntu will not boot! PLEASE HELP!"
date: 2011-05-18
forum: General Help
---

### Post by arizonagirl11 on 2011-05-18
ok so I had 10.04 and it was giving me trouble. So I updated to I think it was 10.10 and as soon as the PC rebooted, I got a message to update to 11,04 I think it is. So I did that and in the middle, the PC froze. It wouldn't do anything. So I rebooted it, and now it won't boot! I am getting two messages.8

INIT: Plymouth-splash main process (104) terminated with status 2
INIT: plymouth main process (58) killed by SEGV signal

Please what's going on! I don't want to loose everything in this PC! It's my main computer! :(

---

### Post by arizonagirl11 on 2011-05-18
Never mind, I'm just going back to Windows. I had a clamAV error, no one helped me with it, so I updated to the new ubuntu, which screwed up my whole computer. This happened once before to me. It's like ubuntu releases updates, that some are just filled with bugs, which leaves the user with having to reformat. So I"m out. Been fun. Thanks. Bye.

---

### Post by Lateralis on 2011-05-18
It is probably possible to recover your current Ubuntu installation using a LiveCD, although I'm a little hazy on the precise details as I've never done it myself.  But from memory, I think it may be possible to complete the upgrade from a LiveCD by chroot'ing into the Ubuntu install and running the updates from there.  

With regards to going back to Windows, if you haven't already done so, or didn't already know, you can use a LiveCD to boot your computer in order to recover any data, files or whatever that are not backed up somewhere else.

---

### Post by oldfred on 2011-05-18
You do know that 10.04 LTS is Long Term Support. The 6 month updates are the bleeding edge and have newer but not always fully working on virtually every configuration of system out there. Sometimes it is just a setting or two. If you really want stability stay with the LTS versions.

Upgrade Guide/Issues Including 11.04 mörgæs
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by arizonagirl11 on 2011-05-18
thank you, Yes, I already reinstalled Windows, and am now having trouble with video card stuff, etc...

---

### Post by wildmanne39 on 2011-05-18
> **arizonagirl11 said:**
> thank you, Yes, I already reinstalled Windows, and am now having trouble with video card stuff, etc...
Problems with those things on windows, or did you install ubuntu again also?

---

### Post by arizonagirl11 on 2011-05-18
with windows. So I give up. Gonna go and lay down.

---

### Post by wildmanne39 on 2011-05-18
> **arizonagirl11 said:**
> with windows. So I give up. Gonna go and lay down.

Ok, I am sorry to hear that, I think you said you are running xp, you probably have to reinstall those drivers for the stuff that is not working.

---

### Post by arizonagirl11 on 2011-05-19
thank you. I got it working now, this whole thing has just been a nightmare. It was my main PC, with ALL my files on it. Now, everything is gone.

---

### Post by Quackers on 2011-05-19
Didn't you make backups? Clonezilla works well with Windows and Linux.
That's a shame.

---

### Post by wildmanne39 on 2011-05-19
> **arizonagirl11 said:**
> thank you. I got it working now, this whole thing has just been a nightmare. It was my main PC, with ALL my files on it. Now, everything is gone.
Hi, your welcome glad to help.

---

### Post by arizonagirl11 on 2011-05-19
nope, no backups. I never heard of clonezilla. I'm hoping a friend of mine could help me with backing up since I have never done it before. I still can't believe I lost EVERYTHING. I still have Ubuntu in my laptop, since that is fine. It was my main PC that went South. Like I said, this whole thing has just been a big nightmare.

---

### Post by essaydean on 2011-05-19
I am  upgraded my self after reading this,back up is must.

---

### Post by Lateralis on 2011-05-19
Yes they are.  But they are just one way to mitigate against things going wrong with an upgrade.  A separate /home partition is another, but you don't think about doing that when you're new to Linux!  

But even with a broken system there are myriad of things you can do to either recover the system or to ensure you don't suffer radical data loss.  If the OP had only waited a little longer or bumped the thread to help get it noticed, then they may actually have a fully operational system by now with no data loss at all.

---

### Post by arizonagirl11 on 2011-05-19
That would have been nice, but alas, not what happened. Instead, I now have a totally empty PC. Of course now, no getting my files back, so whatever, I guess I'm screwed at this point.

How exactly do you "bump" a thread up? And honestly, I'm not totally sure how to do backups of a whole entire PC.

---

### Post by HappyHoward on 2011-05-19
It's theoretically possible to recover some of the files you've lost. There are tools that scan whole discs, and it's very possible a lot of the data still is present on the disc.

I've used [http://www.r-studio.com/](http://www.r-studio.com/) for this purpose. I'm sure there are free alternatives also.

---

### Post by lmn. on 2011-05-19
> **arizonagirl11 said:**
> That would have been nice, but alas, not what happened. Instead, I now have a totally empty PC. Of course now, no getting my files back, so whatever, I guess I'm screwed at this point.

How exactly do you "bump" a thread up? And honestly, I'm not totally sure how to do backups of a whole entire PC.

if you are on linux use testdisk, windows; recuva.
no need to backup everything, only take with you what you need.. which you can do by burning cds/dvds or uploading to an online storage site such as dropbox or rapidshare.

---

### Post by Lateralis on 2011-05-19
> **lmn. said:**
> if you are on linux use testdisk, windows; recuva.
no need to backup everything, only take with you what you need.. which you can do by burning cds/dvds or uploading to an online storage site such as dropbox or rapidshare.

Or in Ubuntu, the 2GB of free space you get with the Ubuntu One cloud service.  Which is also accessible from an internet browser on any other OS.

---

### Post by briapro on 2011-05-19
> **arizonagirl11 said:**
> That would have been nice, but alas, not what happened. Instead, I now have a totally empty PC. Of course now, no getting my files back, so whatever, I guess I'm screwed at this point.
 
How exactly do you "bump" a thread up? And honestly, I'm not totally sure how to do backups of a whole entire PC.
 
You bump a thread by posting in your own thread. That moves it to the top again. As said most of your files are probably recoverable whatever you did. If you are interested in this you should not use the disk you want to recover. The more you use it the more you can lose. If you need to use the computer right away you might want to buy a new hard disk and install on that. You can do the recovery yourself or have it professionally done.

---

### Post by arizonagirl11 on 2011-05-20
thank you. i am going to try that tomorrow. Someone showed me a program that I downloaded to do that, but you had to pay 100 dollars for it, so I am going to try what you suggested :D Thanks again

---

### Post by linuxinstalledfromhdd on 2011-05-20
[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

free.. and will recover your stuff with a live usb ubuntu bootable drive.

---

### Post by arizonagirl11 on 2011-05-20
thank you :D I am running recuva on the computer now.

---

