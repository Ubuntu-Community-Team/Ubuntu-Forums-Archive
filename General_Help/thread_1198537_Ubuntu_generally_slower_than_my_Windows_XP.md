---
title: "Ubuntu generally slower than my Windows XP"
date: 2009-06-27
forum: General Help
---

### Post by sensory on 2009-06-27
Hi all,

I'm posting to get some information on how I can speed up Ubuntu on my laptop to be at least as fast as my Windows XP installation while doing most average tasks. I heard that Ubuntu generally was faster than XP but that hasn't been my experience so far.

I'm running a pretty slow system. It's a laptop, "boasting" an AMD Turion64 1.5gHz, 1GB of RAM, an ATI Radeon Xpress 200m.. and as said, Windows XP primarily. I often boot into Ubuntu 9.04 (installed via Wubi) when I don't want to play WoW. I'm trying to learn as much as I can so I can use Ubuntu a lot more often and only boot into Windows on the odd occasion.

The only problem is that I've found myself wanting to boot back into Windows while doing various random tasks because Windows is so much faster on my machine. For instance, unzipping/unraring a 350mb file takes at least 3-4 minutes to complete, while on Windows it's done in 15 seconds max. The same goes for transferring files from one folder to another. I tried transferring 1GB worth of downloads to another folder and sat there for over 5 minutes waiting for it to complete.

Browsing with Firefox 3.0.11 on the other hand is fine. But any thing else, like updating drivers, reading repositories, transferring files, unpacking zip/rar feels like it's 2x slower than on Windows.

I've turned down the appearance settings to none but other than that, I can't really think of any thing else that would help. I know ATI has stopped supporting my chipset and since 9.04 was released I haven't been able to get my video card drivers working correctly, but this problem was around in 8.10 as well.

Is there any thing I can do to fix the general sluggishness of Ubuntu on my machine?

Thanks ahead of time for any help. :)

---

### Post by TenPlus1 on 2009-06-27
Ubuntu isn't running at it's full potential if you have it installed via Wubi...  It's on a virtual filesystem stored on your Windows XP NTFS partition so this slows things down a bit...

In my opinion Ubuntu runs a lot faster than my XP install when it has access to it's very own partition during install, but that's a leap you have to take if you want to run XP and Ubuntu together...

---

### Post by raymondh on 2009-06-27
> **TenPlus1 said:**
> Ubuntu isn't running at it's full potential if you have it installed via Wubi...  It's on a virtual filesystem stored on your Windows XP NTFS partition so this slows things down a bit...

In my opinion Ubuntu runs a lot faster than my XP install when it has access to it's very own partition during install, but that's a leap you have to take if you want to run XP and Ubuntu together...


Ditto on wubi installs.  Also, poor disk performance may be due to low memory or a fragemented drive.  Try to defrag c:\ubuntu file.

Some performance tips when it comes to browsing

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I have done those tips and have noticed improvements.  Note, I am using a solo, non-wubi install.

---

### Post by rob1408 on 2009-06-27
HDD access is slower when using Ubuntu via Wubi this is why tasks such as extraction and moving files take longer.

---

### Post by pizza-is-good on 2009-06-27
I run Ubuntu in its own partition, with dual boot, and that is way faster than Vista.
But, if you want to runt them both together, I recommend you try Sun's VirtualBox. I haven't used it the way you want to (XP host, Ubuntu guest), but I have used it, and I can tell no difference between running an OS as either host or guest. It works the same.

If you do that, you might want to add more RAM, but that's your choice, VirtualBox will adapt to whatever you have.

If you decide to try that, look around in the forum, there is a lot of help with Virtualization.

---

### Post by Redsandro on 2009-06-27
I've been struggling this speed issue for years now. People pop this question a lot and fanboys say Ubuntu should run faster.

But here's my plain experience: I use Ubuntu for years now, from as low as a P2 266MHz to a P4 2.4GHz, some middle class AMD and a laptop. Although the P2 has become pretty useless, my old computers are always worth more to me than they are on the market.

Anyway, I've also had XP on all of them, and *XP has proven to be faster on all of them*.

The point is, I don't exacly have 4 XP licenses. Not only is Ubuntu free, it is also highly customisable, very versatile and very stable if you don't mess around.

So here's what I do: Run XP [SIZE="1"](or actually Windows 7 now, I skipped Vista)[/SIZE] on your main workstation and use (x)Ubuntu for the rest. Server, media center and laptop in my case.

-edit-
All stand alone installs on ext2 or ext3, 8.04 though, I don't like to update when stuff works.

---

### Post by philcamlin on 2009-06-27
wubi is slow 

partition is way faster!!!!!!!

---

### Post by sensory on 2009-06-27
Damn, that's one thing they never mentioned on the Wubi site.

If I go the whole hog and install Ubuntu on a seperate partition, say about 10GB, will I still be able to access or mount my C:\ drive? I remember installing Ubuntu (Wubi again) on a seperate partition before and it only being a case of mounting the C:\ drive under the place menu.

Thanks for the speedy replies, guys!

edit: I found this post ([536450]("http://ubuntuforums.org/showthread.php?t=536450")) about Wubi slowness while googling and I'm going to try using [LVPM]("http://lubi.sourceforge.net/lvpm.html") to make things easier. If it doesn't work out I'll just backup my Home dir and do a clean install. I'll also defragment my harddrive tonight since it more than likely needs it.

---

### Post by pizza-is-good on 2009-06-27
Yes! If you boot into Ubuntu, you CAN mount your C drive.
 
That's the way I do it. Only use my linux partition for the OS itslef and apps, and save all my data in my windows drive. Probably not the safest way to do it, but I back-up often....
 
Now if you want to see your Ubuntu files while you're in Windows, I think that there is a driver or something for it, but I can't tell you, as I don't use that option.
 
Good luck!

---

### Post by sensory on 2009-06-28
While that took a while.. it was mainly my own doing that messed things up. Accidentally deleted the partition that had Grub on it. Whoops!

All's sorted now, though. And Ubuntu is indeed running at least 4x faster(!) than it was when using the Wubi mess. The transfer rates have gone from 3.5mb/s to over 10mb/s when moving about files. I'll still defrag my harddrives because I'm positive they need the lovin'.

Thanks guys for the help and support! :)

---

