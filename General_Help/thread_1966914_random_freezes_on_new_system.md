---
title: "random freezes on new system"
date: 2012-04-27
forum: General Help
---

### Post by gexi on 2012-04-27
Hi everyone,

I just assembled a cheap HTPC (Celeron G530, Samsung SSD 830 64GB, 4GB Ram, H61 Motherboard) and did a fresh install of Precise 64bit.

So now the system runs generally like a charm, but it just completly freezes about every hour or so, which is quite annoying. Only hard reboot helps. I tend to blame the SSD or the RAM, because I couldn't find anyone with a similar problem. So I guess it's not on the software-side.

The thing is: I don't know how to find out what is wrong. Is there a convenient way to see if any piece of hardware is broken?

---

### Post by techsupport on 2012-04-27
> **gexi said:**
> Hi everyone,

I just assembled a cheap HTPC (Celeron G530, Samsung SSD 830 64GB, 4GB Ram, H61 Motherboard) and did a fresh install of Precise 64bit.

So now the system runs generally like a charm, but it just completly freezes about every hour or so, which is quite annoying. Only hard reboot helps. I tend to blame the SSD or the RAM, because I couldn't find anyone with a similar problem. So I guess it's not on the software-side.

The thing is: I don't know how to find out what is wrong. Is there a convenient way to see if any piece of hardware is broken?

Drop to Ubuntu 2D session and see if the problem stops. It is a process of deduction. Once you locate what it could be, then we can try to fix that.

---

### Post by gexi on 2012-04-27
> **techsupport said:**
> Drop to Ubuntu 2D session and see if the problem stops. It is a process of deduction. Once you locate what it could be, then we can try to fix that.

Thanks for your quick answer. I just logged into Unity 2D and had the same problem. It doesn't seem to be connected to the workload though. Opening several high-res video-files at the same time didn't do the trick, whereas the system froze while i was sipping on a cup of tea ;) 

Another thing that might be connected to this issue is, that the system doesn't always wake up from suspend mode (the screen just remains in stand-by-mode, no response to keystrokes -- even though power-led and fans are starting). I haven't really tested it thoroughly, but it seems that the system is more likely to freeze, the longer it was in suspend (had no problems with immediate wake-ups so far).

---

### Post by gexi on 2012-04-28
OK, it seems like the XBMC session does not have the same problem. At least I used it for a long period of time (several hours) last evening and it didn't crash once, furthermore i put the system in suspend (from within XBMC) over night and wake up worked.

So this could be a problem with the software after all. Any ideas what it could be or what I should try to do? I might just downgrade to oneiric and see if the problem persists.

---

### Post by mörgæs on 2012-04-28
Yes, sticking to 11.10 a few months more is a good idea.

You could also try other 12.04 Buntus. As mentioned above it is a process of deduction.

---

### Post by 3rdalbum on 2012-04-28
It could be the RAM. Taking out one stick and seeing if the problem goes away is probably the easiest way of checking the theory. If you already have Phoronix Test Suite, though, running the memory benchmark might cause a crash within seconds if you have bad RAM.

I had unexplained crashes on this system for quite a long time. Taking out one of the Kingston RAM sticks fixed the problem and it's been solid and stable with the non-brand-name RAM ever since. In fact I think Kingston is generally quite bad as I've seen others have problems with Kingston memory.

---

### Post by gexi on 2012-04-28
Unfortunately I have just a single memory stick. So I can't take it out right now. But I will however check out the Phoronix Test Suite. Thanks for the hint!

---

### Post by gexi on 2012-04-28
The memory test from phoronix finished without any problems. It really might be the X-Server that messes things up.

---

### Post by gexi on 2012-04-29
Just embedded the xorg-edgers PPA. Want to try everything before downgrading to 11.10. I'll let you guys know if this fixed my system-freezes.

If anyone else got any pointers or ran into a similar problem, please let me know.

---

### Post by CHAMÆLEO on 2012-04-29
> **gexi said:**
> Hi everyone,

I just assembled a cheap HTPC (Celeron G530, Samsung SSD 830 64GB, 4GB Ram, H61 Motherboard) and did a fresh install of Precise 64bit.

So now the system runs generally like a charm, but it just completly freezes about every hour or so, which is quite annoying. Only hard reboot helps. 

My situation is similar, but not from a fresh installation.  I had Oneiric working perfectly, stupidly decided to upgrade (you’re calling it LTS, so it’s stable, right?!), and now the system randomly freezes up.  The capslock and scroll-lock indicators on my keyboard start flashing, and nothing but a hard reset of the computer will bring it back into operation.  

It’s not hardware; it’s Ubuntu 12.04.  Is there any way to diagnose or fix this?

I’ve been running this for a few minutes, and it’s happened three times already.  I hope I get to the end of this message!

---

### Post by CHAMÆLEO on 2012-04-30
I&#8217;ve played around with the other log-in options, and it seems that this only happens with the default Ubuntu (Unity).  It doesn&#8217;t happen with Ubuntu 2D, GNOME 3 or KDE.  So, I&#8217;ll just use one of those others until the problem is fixed.

---

### Post by gexi on 2012-04-30
you seem to have a different problem. as far as i remember, flashing scroll- and caps-lock indicate a kernel-panic, which does not happen in my case, furthermore, unity2d also freezes on my system.

btw. the xorg-edgers ppa did not help either. if there are no new ideas, i'll have to revert to oneiric. which is a pity, because i won't be able to file a bug report on this.

---

### Post by Ubun2to on 2012-04-30
> **CHAMÆLEO said:**
> My situation is similar, but not from a fresh installation.  I had Oneiric working perfectly, stupidly decided to upgrade (you’re calling it LTS, so it’s stable, right?!), and now the system randomly freezes up.  The capslock and scroll-lock indicators on my keyboard start flashing, and nothing but a hard reset of the computer will bring it back into operation.  

It’s not hardware; it’s Ubuntu 12.04.  Is there any way to diagnose or fix this?

I’ve been running this for a few minutes, and it’s happened three times already.  I hope I get to the end of this message!

I had to upgrade from 11.10, as I corrupted the filesystem by not doing a hard reboot (I didn't know pressing the power button was bad at the time). Nothing I tried worked.
Anyway, I have 8 GB of ram, and it was freezing on me right and left the first few times I booted.
Now, it's just occasional program freezes (rather than entire system lockups), and I still have no idea why. It can be as simple as scrolling down the list in the software center, and it locks up, or I could be on Chrome, and it freezes.
Seems like LTS should stand for Long Term (un)Stability, or it should be LTSI, Long Term Stability Issues.

---

### Post by gexi on 2012-04-30
> **gexi said:**
> you seem to have a different problem. as far as i remember, flashing scroll- and caps-lock indicate a kernel-panic, which does not happen in my case, furthermore, unity2d also freezes on my system.

btw. the xorg-edgers ppa did not help either. if there are no new ideas, i'll have to revert to oneiric. which is a pity, because i won't be able to file a bug report on this.


Just wanted to let you guys know: I'm now using GS and xorg-edgers PPA. It's far more stable then previous setups. I had one crash, but it was an "atypical" crash compared to my previous problems, so I couldn't say (yet) if it was the same thing causing it. Will let you guys know if I keep running into those annoying freezes. For now I'm really happy. :)

(But I'd still love to figure out what the exact problem was/is, so developers can work with that information ... )

---

### Post by gexi on 2012-05-01
Some news on this one:

I set up a UPnP- and a Samba-Server on this Machine. It froze again (yeah - still freezes), but I was still able to pull files from it. Both Servers were working just fine. So apparently it's not a system-freeze, and it's not some hardware problem.

I'm now quite sure there is something wrong with X and the integrated Intel Graphics Device. Is there a possibility to view the log from the x-server, so I could file a bug for this?

---

### Post by CHAMÆLEO on 2012-05-02
> **CHAMÆLEO said:**
> I’ve played around with the other log-in options, and it seems that this only happens with the default Ubuntu (Unity).  It doesn’t happen with Ubuntu 2D, GNOME 3 or KDE.  So, I’ll just use one of those others until the problem is fixed.

Update: I’ve found that it does actually freeze with everything except Ubuntu 2D, so that’s what I’m using now, even though it is ugly.

---

