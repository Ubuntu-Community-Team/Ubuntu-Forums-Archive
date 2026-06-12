---
title: "Mystery Usage Problem - Possibly Python"
date: 2010-11-30
forum: General Help
---

### Post by DOMS on 2010-11-30
[FONT="Verdana"]Hi guys,

I have a bit of mystery regarding my system intermittently freezing.

First off, the info. I using/running:
Ubuntu 10.10, 64bit version (clean installation)
Intel(R) Core(TM)2 Duo CPU E8500 @ 3.16GHz (not overclocked)
6GB RAM
Nvidia GTX260
Nvidia proprietary drivers
1TB Western Digital HD (32MB cache)

Now, the problem: A while ago, I started experiencing intermittent system freezes that would last for 2 or 3 minutes and happen about once every 45 to 75 minutes.

The Gnome System Monitor (GSM) would show 100% CPU utilization, but top, htop, and conky only show about 11% usage. I pulled up the process list in GSM. However, I had issues, for the obvious reason, when bringing it up when the CPU was spiking. Even when I could, it only showed the usual suspects (Firefox, Deluge, Ktorrent, and Xorg) running the high single digits. This was backed up in top, htop, and conky.

I also checked the RAM, but usage was down around 25%, with nothing in the swap.

I checked the messages log, but there was nothing there. Nor in dmesg. At least not that my limited Linux admin skills could find. The freeze just happened, so I've attached them in their entirety.

I've come to suspect that Python is the cause. It happens most often when I have Ktorrent or Deluge going.  I used to use Deluge, but moved to Ktorrent to test if Deluge itself was the problem.  They're both written in python though, and both seem to cause the slowdown. It also happens when other python-based programs are running, such as the updater, but not as much or as bad.

Things I've tried to fix the problem:
- Clean install (first time in over 18 months)
- Updated Nvidia driver by adding a repository
- Updated Deluge by adding a repository
- Enabled backports.
- Gave my PC the finger

This is driving me nuts. If it was just BT clients, I'd only run those at nights, but it's also parts of Ubuntu itself that relies on python, which I really think is the problem.

Any help would be more appreciated.

[/FONT]

---

### Post by czr114 on 2010-11-30
Is the app freezing, the GUI freezing, or the system itself freezing?

I spent the better part of a month being driven nuts by random freezes during torrenting, only to find that a buggy wireless driver was responsible. As soon as I strung over some cat6 and wired in, the problem was solved.

If Python is an unacceptable resource hog, look into qBittorrent, although I doubt Python is locking the system.

---

### Post by DOMS on 2010-11-30
It's the GUI (at least) that's freezing.

---

### Post by TiBaal89 on 2010-11-30
> **DOMS said:**
> [FONT="Verdana"]The Gnome System Monitor (GSM) would show 100% CPU utilization, but top, htop, and conky only show about 11% usage.[/FONT]

When top showed 11% usage, did it also show 89% idle? 

Just a thought, but maybe top interprets usage differently than GSM (i.e. top divides things based on user, sys, etc and maybe GSM doesn't?).  I don't know what GSM is doing, just a theory.

---

### Post by DOMS on 2010-11-30
It's entirely possible. The next time it happens, I'll check with GSM.

Any idea how can I tell if it's just the GUI that's freezing?

---

### Post by DOMS on 2010-12-02
I've continued to have the random freezing. When it's not freezing, the GSM shows a usage of only 5 to 15%. I have been able to bring it up to look at it during a freeze (by leaving it open) and the graph shows 100% usage, but the process list shows only what top, htop, and conky have. Which is a total CPU usage of ~25%.

Sometimes, I can still open a simple window (such as a terminal) and other times, I can't even run the htop command in an already open terminal.

Does anyone have ***any*** idea what it might be or how to figure it out?

Really, if I wanted my OS to be randomly unusable I'd have stuck with Windows.

---

### Post by DOMS on 2011-02-24
Okay, it turned out that it was the IOWait that was pegging my CPU.

I tried everything I could find to fix it:

- Reinstalled
- Updated to Natty Narwhal
- Purchased a new CPU
- Purchased new memory
- Gave my computer the finger
- Purchased a new driver (32GB SSD)
- Updated the BIOS
- Disconnected the DVD drive
- Got the non-kernel patch performance ([http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html))
- Went to the 32bit version
- Kicked the computer
- Used various mount options in the fstab
- Changed the RAID type in the BIOS from IDE to ACPI

Only two of those helped. While the non-kernel performance thing didn't fix it, it did lower the IOWait problem. It also did wonders for everything else in Ubuntu. 

In the end, is was changing the RAID type to ACPI that fixed it.

Just thought I'd throw this out there for those suffering like I was.

Good luck!

---

### Post by DOMS on 2011-03-06
Final update.

The CPU was spiking as often after I made the above changes, but it was still happening from time to time.

I changed my storage drives from EXT4 to XFS and know it doesn't spike anymore.

Perhaps that was the only thing I needed to do. I'm not sure, but do with the information what you will.

I'm out.

---

### Post by 3rdalbum on 2011-03-06
There is a program called 'iotop' that might help you find the program causing the IOWait.

---

### Post by DOMS on 2011-03-06
Believe me when I say that I've tried it. I've learned a lot about troubleshooting IOWait problems.

The application that was causing the problem was KTorrent. I purged and reinstalled it. I tried *so many* things.

The clue was that one of my (new) drives experienced corruption. Nothing bad enough to lose data, but corruption nonetheless.

Since switching to XFS, I've had zippo problems. My CPU sits around 10% utilization most of the time now. And no corruption so far.

I think there may be a performance/reliability issue related to Ubuntu 9.04 through 10.10 and EXT4.

---

