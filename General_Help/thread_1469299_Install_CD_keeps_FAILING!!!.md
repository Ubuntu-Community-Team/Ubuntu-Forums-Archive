---
title: "Install CD keeps FAILING!!!"
date: 2010-05-02
forum: General Help
---

### Post by ram2500 on 2010-05-02
Good evening everyone, 

I have been FRUSTRATINGLY trying to upgrade to 10.04 because I was impressed with it, however, as I have predicted, it was a headache. In all actuality, it is WORSE than a headache. Both my desktop and laptop are now decommissioned, (I have Windows 7 on the 2nd laptop, and since Ubuntu/GRUB hasn't installed completely, it won't boot--I have to fix that TOO) leaving me to depend on an old Pentium III in the closet to download and burn CD images, which is STILL failing. Unfortunately, I have burned 9.10 on a rewritable CD, which I erased long ago. I have NO computer now, other than the old Pentium III which was sitting in a closet. I am tired and want to go to sleep, but I am the kind of person who finishes  things that were started. 

My problem is that I have downloaded (and burned to a CD) Ubuntu 10.04 TWICE, because it's failed to install. I thought that the ISO was corrupted, so I downloaded it and installed it AGAIN. Same thing. I tried making a Live USB Flashdrive install--same old, same old. It's 12:00 MIDNIGHT (Pacific time) and I can't bear to stay up this long like some of you young ones can:). Thank goodness for caffeine:)

I KNEW that I shouldn't have done this, but I went ahead and proceeded to "upgrade". Well, the actual upgrade (thru Ubuntu Update tool) failed, so I decided to do a clean install. Thought that the process, from start to finish, would take 30-40 minutes, but was I wrong! I have been stuck with this issue since 7 P.M.! 

Well, to cut to the chase, is anyone else having issues with burning/installing from their own CDs? This Pentium III is only running Fedora Core 6 with 512MB of memory, so it can get a download/burn job done OK. I am using the K3b burner in Fedora and no errors regarding a corrupted ISO appear. Why then, won't it install, after downloading and burning two separate ISOs?

How can I get myself out of this mess of "supposedly" corrupted ISOs? I used two NEW, UNTOUCHED blank CD-R media, both of which failed, PLUS my flash drive.

---

### Post by Dayofswords on 2010-05-02
you didnt explain how it was failing =p

---

### Post by R[wc]BADFISH on 2010-05-02
Yeah, I was having a similar issue. Except mine wouldn't boot from a DVD. However would boot into a Dban CD. Burned the ISO onto CD and was good to go! Does it start the install process then fail? 

I just figured it was failing hardware.

---

### Post by ram2500 on 2010-05-02
A dialog comes up saying something along the lines of "The installation failed...Check to see if the CD/DVD is clean...make sure the PC is in a cool environment..." ---something of the like. The fact of the matter is, the CDs were BRAND NEW and no errors were appearing as the ISOs were being burned to the CDs. I tried the Live USB option, it had the same error. ***I'm beginning to think that the ISO image off Ubuntu's site is faulty.** Does anyone know if it is?*

So, now I'm changing course, and will try downloading the alternate (text) version, as I am thinking after two failed ISOs from the Live CD image, I will try the alternate(text) image. If that doesn't work, why then I'm giving up. This is too late in the night to be having to deal with this issue.

---

### Post by ram2500 on 2010-05-02
As an addendum, the_third_ ISO I've downloaded (I have three ISOs I have downloaded) has **failed**as well.

**My hypothesis is that the 10.04 image is a faulty image that affects everyone who uses it (the 10.04 i386 Live install version), and not just myself. **The same error message stopped at 50%--as the case with all of the other CDs. Evidently, the CDs were *known good* as they would have failed right in the burning process, so CD problems are ruled out in addition to knowing that it's also failed with the USB drive method. It can't be my drives because I've tried the first one on my laptop, the second and third on my old unused Pentium III--it would be a STRANGE coincidence for both *totally different drives* to quit working. [B]It has to be a faulty image on Ubuntu's site. 
[/B]
Is there anyone out there experiencing the same issue with it going ahead with the install and then stopping at around 50%, claiming that the CD is corrupted and that it can't proceed?

I give up with the live CD; I am in the process of downloading the Alternate version, in hopes that only the Live version is indeed corrupted and the other versions are not affected.

---

### Post by ram2500 on 2010-05-02
I was thinking to myself after browsing to see if any others had corrupted ISO issues that since Ubuntu is hosted on multiple servers, I happened to be the un-lucky one to download from a mirror with a corrupted image. It appears that a lot of people already have installed/upgraded to 10.04 without installation failures, so I am thinking it is the individual mirror. In my case, I live in Washington state and thus, I probably downloaded it from the Walla Walla University mirror (I'm not sure.)

The Alternate CD is almost downloaded and so I am going to go ahead and try this out on my desktop machine, and then in the morning, repair the Windows install on my laptop and reinstall Ubuntu (that's if the image I am downloading right now works.)

If this ISO I am downloading right now doesn't work, I am **not** going to put any more effort into downloading the image and will just go to Best Buy or Walmart (wherever they have Ubuntu CDs) and pick up a copy tomorrow, if they have 10.04. If not, I'll buy them on-line. This is really tedious, and from now on, I will never, ever burn any more ISOs and will purchase them from now on so that I will _never_ go through this again. It is now 1:00 in the morning and I haven't even begun to get anything done. I still have to configure different things and restore files from backups. It appears as if I will be doing this until about 3 am. 

I hope 10.04 is worth all this trouble. I think it will be:)

---

### Post by plucky on 2010-05-02
Did you check the [MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) of the ISO?

---

### Post by crossy on 2010-05-02
I've got two suggestions, based on the solutions found to similar problems I've found in the past (the 9.04 install went through a stack of CD's before I got one that worked - and 20/20 hindsight is frustrating!)

1. Are you using the same mirror each time? If so, then maybe it's that mirror that's wrong. I'm based in the UK, and definitely the UK mirror is working - since I managed to provision an Acer laptop with it last night.

2. Are you using the same burn process each time? If so, try something different. Again, I had issues with using Brasero to burn an OpenSuse CD, and switching to Nero on Windows sorted that out.

I'm not sure you'll be able to see it at Wallmart anytime soon - if you want a CD copy I'd try one of the Linux specialists, (there's a raft of them over here in the UK, so I guarantee that there's more in the US)

Persevere with it - I've got issues with a corrupted python-pygame, NX support (although that's probably Acer's fault) and a weird power niggle. Apart from that, the Lucid looks good. So much so, that I'm in the process of doing a clean install on my main office development system now.

Bob. :guitar:

---

### Post by Rubi1200 on 2010-05-02
See this:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

---

### Post by dino99 on 2010-05-02
follow [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by ram2500 on 2010-05-02
I have tried the alternate install, on a flash drive. It stopped installing, with an error (it said that the Choose Software part had failed or something of a like...it was a red-colored text screen). I looked on Walmart and Best Buy's site...unfortunately, I guess they don't sell the CDs, so I suppose I will have to wait for a week or so to get up back and running again and buy the CD online. This is one of the worst computing disasters I've had in the 35+ years I've been using computers...my worst was when I was an assistant professor teaching at a community college and had inadvertently deleted a drop box with all my students' assignments vanishing into thin air. (I still had a job afterwards, as it was an accident, and the students were spared from a suffering grade, but it was the humiliation that was the worst). That was when I was getting acclimated to Unix. Anyways... 

I have contemplated dropping back to 9.10 and downloading the ISO for it, but I am finished with the downloads. It's been too much for me. Maybe when I have a better attitude towards getting this resolved, I will probably try the download and burning in Windows, which I haven't tried yet. However, I am convinced that the image is corrupted.

By the way, I have done the md5sum comparisons, and all the ISOs have matching keys. I think the image is corrupted. So...I am going to go back to sleep (I woke up to read the paper and have some coffee). I have gotten Windows up and running on my laptop, so I got that part out of the way.

---

