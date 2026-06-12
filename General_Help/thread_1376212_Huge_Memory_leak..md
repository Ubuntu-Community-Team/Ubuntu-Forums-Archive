---
title: "Huge Memory leak."
date: 2010-01-08
forum: General Help
---

### Post by carisch on 2010-01-08
i have a huge memory leak that i just can't pinpoint. being a windows geek (even though i hate the damn company). I did the simple thing i would have done on xp. 

1st i did a simple reinstall.
after installing my video card driver. (ati radeon 4850, the official one from amd) my computers ram was at about 500 mb. 4 hours later after not doing a thing my computer was at 3.6 gigs. however the system monitor did not add up. i have had this computer for 6 months and never had this problem in linux. i could leave it on over night and the ram stayed the same. (this was one of the reasons i turned my back on windows) 

so i basically am asking how should i go about this problem.   

[IMG]http://dl.dropbox.com/u/2219035/Screenshot-System%20Monitor.png[/IMG]

---

### Post by sandyd on 2010-01-08
what about running ```
top
```or ```
 htop
```?

theirs a memory leak on the ones you get from the ubuntu hardware drivers ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/450048](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/450048)), but there isn't one for the drivers from the ati site though.

---

### Post by lukeiamyourfather on 2010-01-08
There's no memory leak, its buffer caching. Everything that gets read from the disk or written to the disk is stored in memory until either the buffer cache is full or an application needs the memory (to speed things up if the system reads the file again). If it makes you feel better pretend its unused memory because it own't affect anything you do in a negative way. The command "top" will show you all of the memory and also how much of it is buffer cache. Cheers!

---

### Post by carisch on 2010-01-08
> **carlee said:**
> what about running ```
top
```or ```
 htop
```?

theirs a memory leak on the ones you get from the ubuntu hardware drivers ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/450048](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/450048)), but there isn't one for the drivers from the ati site though.

[IMG]http://dl.dropbox.com/u/2219035/Screenshot.png[/IMG]

---

### Post by sandyd on 2010-01-08
you got 4GB of memory, /2GB are currently in use.
ain't memory leak, considering i have more memory in use than you on a clean startup...

---

### Post by carisch on 2010-01-08
> **lukeiamyourfather said:**
> There's no memory leak, its buffer caching. Everything that gets read from the disk or written to the disk is stored in memory until either the buffer cache is full or an application needs the memory (to speed things up if the system reads the file again). If it makes you feel better pretend its unused memory because it own't affect anything you do in a negative way. The command "top" will show you all of the memory and also how much of it is buffer cache. Cheers!

When the memory gets full and it drops on to the swap my computer practically stops. it takes about 5 hours for this to occur.

---

### Post by carisch on 2010-01-08
> **carlee said:**
> you got 4GB of memory, /2GB are currently in use.
ain't memory leak, considering i have more memory in use than you on a clean startup...
can you explain why this never occurred before.

---

### Post by warfacegod on 2010-01-08
I have 2 GB RAM. In an idle state roughly 200 MB is used as RAM and 250 MB as cache. It *never* varies by more than 5 - 10 MB no matter how long I leave it ideal, hours or days.

If you shut down your GUI so your using only command line and look at RAM use, is it the same?

---

### Post by ZeroSpawn on 2010-01-08
Check your start up programs, get rid of all the ones you don't use.

---

### Post by carisch on 2010-01-08
> **warfacegod said:**
> I have 2 GB RAM. In an idle state roughly 200 MB is used as RAM and 250 MB as cache. It *never* varies by more than 5 - 10 MB no matter how long I leave it ideal, hours or days.

If you shut down your GUI so your using only command line and look at RAM use, is it the same?
 that is a good idea... for me until now i would idle at about 350 mb for days at a time. (dropbox ate up a lot of ram.)  i think what i should do is see if i can find the 9.11 version because that never had any problems on my computer. i only updated 3 or 4 days ago. 

btw my ram is at 3.4 gigs now. give it 10 minutes before it gets filled.

---

### Post by carisch on 2010-01-08
> **ZeroSpawn said:**
> Check your start up programs, get rid of all the ones you don't use.

this is a default install. other than driver and updates. :/ 

i am at 3.6 gigs now

---

### Post by warfacegod on 2010-01-08
I'm very much thinking that your ATI driver is doing this. Unless you have an external plugged in. With mine, if I watch a video or download a torrent to it or etc. my cache uses all my RAM until I unmount the drive. Then RAM use goes back to basically what it is when I first booted.

---

### Post by carisch on 2010-01-08
> **warfacegod said:**
> I'm very much thinking that your ATI driver is doing this. Unless you have an external plugged in. With mine, if I watch a video or download a torrent to it or etc. my cache uses all my RAM until I unmount the drive. Then RAM use goes back to basically what it is when I first booted.
i am too. i reinstalled the os again and this time i am going to install version 9.11. I personally had no problems with this version, so I guess I will see what happens.

---

### Post by warfacegod on 2010-01-08
Good luck.

---

### Post by carisch on 2010-01-09
> **warfacegod said:**
> Good luck.
everything works fine again. i believe there is some incompatibility with 9.12 and my setup....

thanks everyone for your help

---

### Post by warfacegod on 2010-01-09
Glad to hear you're running smoothly again. I can't say the same for myself. Any ideas on this one?

[http://ubuntuforums.org/showthread.php?t=1376252]("http://ubuntuforums.org/showthread.php?t=1376252")

Don't forget to mark as solved.

---

### Post by lukeiamyourfather on 2010-01-10
> **carisch said:**
> everything works fine again. i believe there is some incompatibility with 9.12 and my setup....

thanks everyone for your help

Glad you got it working! I figured it was the usual question related to the buffer cache showing as used memory (most new Linux users ask about it). If you haven't already please inform ATI support of the leak so its resolved in future releases. Cheers!

---

