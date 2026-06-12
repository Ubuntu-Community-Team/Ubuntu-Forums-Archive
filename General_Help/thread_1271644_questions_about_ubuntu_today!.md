---
title: "questions about ubuntu today!"
date: 2009-09-21
forum: General Help
---

### Post by Thowsen on 2009-09-21
Hi im a former ubuntu user, really enjoyed having ubuntu back in the days, but as time passed by i had multiple problems that i kept google'ing for and solved. but i got pretty sick n tired of all that google'ing.

Im wondering how the operatingsystem is today.

back in the days ubuntu had a major problem with usbstorage devices. and this were one of the problems that i never solved. When i plugged my Usbmemory into the computer and transfered my files the files became invisible on mac and windows computers and i had to format the device to use it again. so i had to mail everything back then.

and how is it with HD movies? . does emerald still make movies laggy? or do u guys even use emerald nowadays?

pls tell me about the latest major buggfixes. i really want ubuntu again. Im gettin sickn'tired of vista.

// thowsen

---

### Post by jarrah-95 on 2009-09-21
i have one thing to say
come back and get rid of the hog (vista)
ive been using ubuntu for about a year and i have never herd of any of those problems (although i have never seen a hd movie as my laptop doesnt have a hd screen) but all of the other problems i have never come accross

---

### Post by 3rdalbum on 2009-09-21
> **Thowsen said:**
> back in the days ubuntu had a major problem with usbstorage devices. and this were one of the problems that i never solved. When i plugged my Usbmemory into the computer and transfered my files the files became invisible on mac and windows computers and i had to format the device to use it again. so i had to mail everything back then.

Never heard of this problem.

> and how is it with HD movies? . does emerald still make movies laggy? or do u guys even use emerald nowadays?

Some people use Emerald. It doesn't affect video playback. Compiz does affect video playback if you have an ATI graphics card because the ATI drivers are still as terrible as ever; but you can just turn off Compiz temporarily.

Get an Nvidia graphics card if you don't already have one.

---

### Post by Thowsen on 2009-09-21
> **3rdalbum said:**
> Never heard of this problem.



Some people use Emerald. It doesn't affect video playback. Compiz does affect video playback if you have an ATI graphics card because the ATI drivers are still as terrible as ever; but you can just turn off Compiz temporarily.

Get an Nvidia graphics card if you don't already have one.
thanks for posting. well i had a 4850 back then, now Im using gtx275.
the flashstorage thing is sadly true though, really need to know if it's fixed now. got 1tb external hdd, and i dont want the music and such to just .... disappear.

now, how are the nvidia drivers? just as good as windows?

---

### Post by 3rdalbum on 2009-09-21
> **Thowsen said:**
> thanks for posting. well i had a 4850 back then, now Im using gtx275.

Well, that would have been your video problem.

> the flashstorage thing is sadly true though, really need to know if it's fixed now. got 1tb external hdd, and i dont want the music and such to just .... disappear.

I don't believe this can actually happen on Linux unless your filesystem is dodgy to begin with. Has your bug report been marked as Fixed? If you didn't submit a bug report... then you really should have.

Or, was it just that Windows could not see certain files? This can happen if you have an NTFS-formatted hard disk and you try to use filenames with question marks and other "special" characters. They are legal in NTFS, but Windows cannot see them. I have come across this Windows bug before now, back when I had Windows on an older computer :-)

> now, how are the nvidia drivers? just as good as windows?

I don't use Windows so I don't know. They work well; the performance seems pretty good and since I removed that bad RAM I haven't had any crashes. VDPAU (Nvidia video decoding acceleration) still requires a manual compile of Mplayer, or you can add a PPA, but it works well.

---

### Post by muteXe on 2009-09-21
I have 3 external hard disks and 2 memory sticks.  All are different makes.  They are all recognised and auto-mounted successfully in both my desktop (ubuntu 8.04), and my laptop (ubuntu 8.04, slackware 12.2). No problems at all.

---

### Post by Thowsen on 2009-09-21
> **muteXe said:**
> I have 3 external hard disks and 2 memory sticks.  All are different makes.  They are all recognised and auto-mounted successfully in both my desktop (ubuntu 8.04), and my laptop (ubuntu 8.04, slackware 12.2). No problems at all.
well the problem is between the operatingsystems .. ubuntu to windows or ubuntu to mac, u get my point

---

### Post by Thowsen on 2009-09-22
bump, anyone?

---

### Post by pmlxuser on 2009-09-22
[Thowsen](Thowsen)

question not very precise. clarify problem please ..

---

### Post by 3rdalbum on 2009-09-22
> **Thowsen said:**
> well the problem is between the operatingsystems .. ubuntu to windows or ubuntu to mac, u get my point

Been there, done that, no problems observed, all files accessible between operating systems (except for files with question marks in the filename, which are illegal in Windows XP but legal on NTFS).

---

### Post by themusicalduck on 2009-09-22
I've used both usb sticks and a usb drive between windows and linux and had no problems.

NVidia drivers are pretty much on par with windows as far as I know. At least, the current linux version is 185 whereas windows latest is 190, so they can't be too far off.

HD video works great too on my gtx260 up to 720p (1080p is choppy, but its the same on windows and my processor is old), even with heavy compiz effects enabled.

---

### Post by P4man on 2009-09-22
> **themusicalduck said:**
> I've used both usb sticks and a usb drive between windows and linux and had no problems.

NVidia drivers are pretty much on par with windows as far as I know. At least, the current linux version is 185 whereas windows latest is 190, so they can't be too far off.

HD video works great too on my gtx260 up to 720p (1080p is choppy, but its the same on windows and my processor is old), even with heavy compiz effects enabled.

You should be able to play 1080p content smoothly with that videocard, if you use GPU accelerated playback. have a look here:

[http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/)

---

### Post by themusicalduck on 2009-09-22
> **P4man said:**
> You should be able to play 1080p content smoothly with that videocard, if you use GPU accelerated playback. have a look here:

[http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/](http://blog.avirtualhome.com/2009/05/29/how-to-compile-mplayer-with-vdpau-support-on-ubuntu/)

Wahey! It worked, 1080 is now perfectly smooth. Cheers.

It would be great if this was supported for VLC too since I use it for just about everything. Guess I'll look into it.

---

### Post by P4man on 2009-09-22
its being worked on, (and apparently works if you can figure out the sort of brief instructions here:
[http://forum.videolan.org/viewtopic.php?f=13&t=53928](http://forum.videolan.org/viewtopic.php?f=13&t=53928) )

Dont ask me how to make it work though :)

---

### Post by Thowsen on 2009-09-22
> **3rdalbum said:**
> Been there, done that, no problems observed, all files accessible between operating systems (except for files with question marks in the filename, which are illegal in Windows XP but legal on NTFS).

ok thanks alot.. i just read that it could've been an old architecture problem on budget usbstoragedevices..

now Im gonna download karmic koala so i can once again have 
satisfied mind

---

### Post by Thowsen on 2009-09-22
> **themusicalduck said:**
> I've used both usb sticks and a usb drive between windows and linux and had no problems.

NVidia drivers are pretty much on par with windows as far as I know. At least, the current linux version is 185 whereas windows latest is 190, so they can't be too far off.

HD video works great too on my gtx260 up to 720p (1080p is choppy, but its the same on windows and my processor is old), even with heavy compiz effects enabled.

just wanna tell u, 1080p may be choppy because non-full-hd-monitors displays 1080p but cannot play it without lagg.

i thought my computer was crap too ;)

---

