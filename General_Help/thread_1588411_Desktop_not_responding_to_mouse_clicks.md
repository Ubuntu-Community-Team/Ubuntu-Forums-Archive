---
title: "Desktop not responding to mouse clicks"
date: 2010-10-04
forum: General Help
---

### Post by weyrava on 2010-10-04
Hi all,

I have a problem in that after I log in, windows on my desktop stop responding to mouse clicks.  This doesn't always happen immediately, but usually after starting a couple applications I lose the ability to click on anything.

The keyboard continues to work, and windows that respond to mouse-over appear to function normally.

I'm running 10.04 64-bit.  This started after an upgrade from 9.10, which was working (relatively) fine.  I've since tried a clean install of 10.04 and still had the problem.  It seems to affect 10.10 RC1 as well, or at least I wasn't able to click past the first couple windows in the installer.

Looking around Google, it seems like the most common solution for this type of problem is disabling Compiz, which I've done, but the same thing happens in Metacity.

Any ideas?

---

### Post by taavi on 2010-10-08
I've seen something like that myself. What videodriver are you using? I installed ATI drivers from their page (built deb and installed them), but I don't know if it's related. It's very annoying...

Actually I'm currently having this :(

---

### Post by weyrava on 2010-10-09
I was using the latest nvidia binary drivers from the repository.  The problem actually went away after I removed them, though that may just be a coincidence...  it comes and goes.

---

### Post by weyrava on 2010-10-11
So, I just tried the official 10.10 release, and the problem is still there.  This is just running the default setup on the live CD, so I think it's safe to say it's not related to the nvidia drivers.

---

### Post by taavi on 2010-10-13
Yes, I have 10.10 too and I uninstalled ATI drivers altogether, running on radeon drivers hopefully. How can I confirm which drivers are on use, I don't have xorg.conf and that "Additional Drivers" which listed ATI proprietary drivers before, displays nothing now.

Are you using Flash with Firefox? I'm having thoughts about that being root of all evil.

---

### Post by pushkin22 on 2010-10-13
I have the same problem with compiz and latest nvidia drivers.

---

### Post by hibit on 2010-10-13
I've reported a similar issue as a big here (perhaps incorrectly):

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/658751]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/658751")

I'm not entirely convinced its an issue around flash, but for me it appears to bring on the situation. I've tried swapping between nouveau and nvidia drivers with no discernable difference.

As a starting point can it be isolated to 64-bit and / or nvidia?

Is it just the left button for you too?

Perhaps you could add you thoughts to the bug report to fill it out?

Issues like this were also highlighted in a now closed thread here:

[http://ubuntuforums.org/showthread.php?t=1572412]("http://ubuntuforums.org/showthread.php?t=1572412")

---

### Post by weyrava on 2010-10-13
> **hibit said:**
> I've reported a similar issue as a big here (perhaps incorrectly):

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/658751]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/658751")

I'm not entirely convinced its an issue around flash, but for me it appears to bring on the situation. I've tried swapping between nouveau and nvidia drivers with no discernable difference.

As a starting point can it be isolated to 64-bit and / or nvidia?

Is it just the left button for you too?

Perhaps you could add you thoughts to the bug report to fill it out?

Issues like this were also highlighted in a now closed thread here:

[http://ubuntuforums.org/showthread.php?t=1572412]("http://ubuntuforums.org/showthread.php?t=1572412")

That does sound like the same problem I'm having, except that pretty much any application will trigger it for me.  I don't actually have flash installed.

It's possible that the problem is only in 64-bit.  I haven't tried the 32-bit release on this machine.  It really doesn't seem related to nvidia though, since we both saw it on different drivers, and taavi has an ATI card.

It does seem like it's just the left button that's affected.

I'll add some comments to the bug report once I can come up with something constructive.

The x11vnc problem mentioned in the other thread sounds like it could plausibly be what's going on here.  I'll see what happens with -noxrecord.

---

### Post by weyrava on 2010-10-13
> **weyrava said:**
> The x11vnc problem mentioned in the other thread sounds like it could plausibly be what's going on here.  I'll see what happens with -noxrecord.

Well that was silly.  I don't have the record extension in my xorg.conf, nor do I even have x11vnc installed.  Oh well.

---

### Post by weyrava on 2010-10-13
To throw a little more fuel on the fire, here is a sequence of actions that consistently breaks my desktop.  It's certainly not the only way to do it, but it doesn't involve Firefox or flash.

- Restart computer, log in
- Open a terminal window
- Start Update Manager
- Click on "Check"

At this point nothing on screen will respond to a mouse click.  Occasionally I'll also get a "could not grab your mouse" message.

After doing this, I can Ctrl-Alt-F1 out, type "sudo service gdm restart", and then everything works fine until I restart the computer again.

---

### Post by taavi on 2010-10-14
I cannot give such fixed reproduce path, because my mouseclick-hangs are very randomatic and unpredictible -- thus very annoying, because I use Ubuntu at my work and can happen on busy times.

One thing is quite sure, it happens when I click buttons -- I think GTK based buttons. And I'm pretty sure it's 100% on left clicks, because you click buttons with left button duh.

I have 64bit install too.

What worries me, is that we can't give a fixed reproduce path and cannot debug it anyhow to raise a bug. Or should we try?

---

### Post by taavi on 2010-10-14
It occured just minute ago; I was able to get terminal up, kill compiz and start metacity. Click-hang disappeared, but I recall the same hang in metacity too, like mentioned by weyrava. So it's not a solution. I am starting to love compiz too because of window rules for example.

---

### Post by voronizer on 2010-10-14
> **weyrava said:**
> Hi all,

I have a problem in that after I log in, windows on my desktop stop responding to mouse clicks.  This doesn't always happen immediately, but usually after starting a couple applications I lose the ability to click on anything.

The keyboard continues to work, and windows that respond to mouse-over appear to function normally.

I'm running 10.04 64-bit.  This started after an upgrade from 9.10, which was working (relatively) fine.  I've since tried a clean install of 10.04 and still had the problem.  It seems to affect 10.10 RC1 as well, or at least I wasn't able to click past the first couple windows in the installer.

Looking around Google, it seems like the most common solution for this type of problem is disabling Compiz, which I've done, but the same thing happens in Metacity.

Any ideas?
Maybe the same issue I have?
[http://ubuntuforums.org/showthread.php?t=1596355](http://ubuntuforums.org/showthread.php?t=1596355)

---

### Post by kernel_232 on 2010-10-14
This i came across working with debian5.0 better u check the arch details, u had specified the bit only 

Also i installed x86 of debian5.0 on an amd machine, may be because of this and also i found performance was poor

---

### Post by weyrava on 2010-10-16
> **voronizer said:**
> Maybe the same issue I have?
[http://ubuntuforums.org/showthread.php?t=1596355](http://ubuntuforums.org/showthread.php?t=1596355)

Maybe.  I've never had using the keyboard trigger the problem, but it seems like it's something different for everyone.

Also, I'm not using bluetooth, just a plain old USB mouse.  Unplugging it and plugging it back in does make the the problem go away, so it's similar in that regard.

---

### Post by weyrava on 2010-10-20
So...  I noticed there was a kernel update today.  Perhaps coincidentally, my usual methods for reproducing this no longer work.

I'm not very hopeful that it's actually fixed, but did anyone else suddenly stop having problems?

---

### Post by taavi on 2010-10-21
Hm, I'm running with 2.6.35-22-generic right now some days and everything is stable. Noticed the update, but havent restarted yet. I'll let know here after some time I've tested both kernels.

---

### Post by taavi on 2010-11-10
I must confirm -- after kernel update, this hell-bugging behavior is gone. Whatever that was, it's fixed now, I suppose.

Anyone has better details what was the fix specifically?

---

### Post by Solostian on 2010-11-11
It's not a 64bits related issue.
I did a clean install of 10.10 32bits on my Dell Mini 9 and the left mouse button does the same crazy stuff.
It's making it nearly impossible to work.

---

### Post by taavi on 2010-11-24
I installed 32bit 10.10 on HP dv2000 and got it again. And this happens most up to date soft.

---

### Post by Huss on 2010-11-28
Update: The problem partly fixed itself after a few restarts. Now mouse clicks only stop working in some applications. I can touch the screen and then clicks work again. It would be good to fix this properly.

Any advice?
 
Original post:
I have the same issue after testing the 'netbook' edition. Unity froze constantly so I uninstalled the netbook packages. Like everyone else, I can't click after a few clicks.

The only solution I have seen is on this site:
[http://ubuntuguide.net/fix-left-click-not-working-after-upgrading-to-ubuntu-10-10-maverick](http://ubuntuguide.net/fix-left-click-not-working-after-upgrading-to-ubuntu-10-10-maverick)

Not sure which file is the appropriate xsever-xorg-input-uvdev package to download.

Has anyone else tried this solution?

---

### Post by DanPerecky on 2010-12-01
Mouse is erratic. Touchpad buttons work no problemo, every time. Using Ubuntu 10.04 LTS
               
You probably already tried this... Found that switching USB ports (for the mouse) helps.

---

### Post by ephemerat on 2011-01-11
I've just started getting this issue today in Ubuntu 10.10 as well. Only left-click on the mouse is affected and then only intermittently (but it's happening a *lot*). Deeply frustrating.

I've installed quite a few games today so am unsure of what may have triggered the behavior. Looks like this one is going to run and run.

Anyone who posted earlier on this thread had any luck in resolving this?

EDIT: Should probably mention that I'm using a PS/2 mouse so changing the USB port is a non-starter. Also, I'm using the 64-bit version of Maverick with a dual-monitor set-up and nVidia's proprietary driver.

---

### Post by ephemerat on 2011-01-12
Have temporarily rolled back to the 2.6.35-23 kernel which seems to have corrected the problem. Will wait for the next kernel rollout and see what happens then.

---

### Post by Huss on 2011-02-07
Hi Ephemerat,

I still have the issue. I have a kernel update waiting to be installed, hopefully that fixes it. 

Any clues to what's causing this? In my case is it the touchscreen firmware? 

...

---

### Post by ephemerat on 2011-02-08
Sorry, Huss; I'm still none the wiser. I think it unlikely that it has anything to do with your touchpad firmware given that most people experience it with mouse and keyboard (like myself). Hope you're kernel update fixes it.

---

### Post by killabee44 on 2011-08-06
Guys, 

Did anyone ever figure this out? I am dealing with the exact same issues on Lucid 64bit. Thanks.

---

### Post by killabee44 on 2011-08-10
Got some updates today that seem to have fixed the problem. Fingers crossed...

---

### Post by darthhiggy23 on 2012-11-21
i'm still having this issue, 12.10 64-bit nvidia card... latest drivers. any advice or fixes yet?

---

### Post by coffeecat on 2012-11-21
@darthhiggy23, your version of Ubuntu is very different from the one that this thread was about. If you need help, please start your own new thread.

Old thread closed.

---

