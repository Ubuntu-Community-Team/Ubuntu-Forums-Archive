---
title: "Black Screen on Wake"
date: 2010-04-10
forum: General Help
---

### Post by Daug on 2010-04-10
I've got Karmic installed on an HP 6930p, and with relatively little intervention, all hardware has been supported beautifully. I'm using the ATI driver for graphics. Battery life increased dramatically after an update a couple of months ago. However, occasionally (1 in 8 times maybe), the screen is black when waking from suspend. Disk wakes, etc, but the screen is off. Trying to re-suspend with fn key doesn't work. Ctrl-alt-f key combos don't work. I have to hold the pwr button down. Any tips on an acpi config file tweak to fix this, or anything? Thanks.

---

### Post by quixote on 2010-04-12
A friend of mine had a similar issue, and a couple of Ubuntu devs at a Linux show here (SCALE) told him what to do about it.  Now all we have to hope is that I remember it right....

Tell your computer to suspend, bring it back up.  It'll fail.  Hold down the power to force it off, and restart.  Then try to make sense of this log file: /var/log/pm-suspend.log.  Mine, for instance, has some lines like:```
Sat Apr 10 22:57:32 PDT 2010: performing suspend
Sun Apr 11 07:51:04 PDT 2010: Awake.
Sun Apr 11 07:51:04 PDT 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
```If it reports success resuming from suspend, but you have the black screen, then the issue is the graphics driver. The last step is find one that works.

The two they recommended for my friend, which work, are xserver-xorg-video-ati 1.6.12.1-0ubuntu2 and xserver-xorg-video-radeon 1.6.12.1-0ubuntu2.  You'll need to install them from the command line (unless synaptic will let you install old versions??).  Something like sudo apt-get install -f xserver-*exact-file-name*.  Check that to make sure of the exact syntax.  I'm pretty sure you ....

Hah.  I found the old link they pointed him to with the exact instructions: [http://swiss.ubuntuforums.org/showthread.php?t=1331522](http://swiss.ubuntuforums.org/showthread.php?t=1331522) and comment #16 in that thread.

The bit toward the end about "lock version" is very important or you'll lose it on the next upgrade.  After it's locked it'll be listed as "pinned."

---

### Post by Daug on 2010-08-31
Sorry it took me so long to reply and thank you, but thanks. The link in your post is now dead, but I found the same solution here:

[http://ubuntuforums.org/showthread.php?p=9791370#post9791370](http://ubuntuforums.org/showthread.php?p=9791370#post9791370)

I've applied this fix (downgraded to the Jaunty drivers), and thought it worked, but had the problem again (albeit after many successful resumes). I've posted about it @ the link above. =)

---

### Post by quixote on 2010-09-01
That actually looks like a somewhat different method, but, hey, whatever works!  The way to stop the updater from pestering you is, in Synaptic, go to the Package menu item and select "Lock Version."  

So far, Lucid has been better behaved than Karmic, so it might be worth upgrading to try to make the problem go away.  It'd be even nicer if there was a rollback feature so that if it didn't, it was easy to go back.

---

### Post by Daug on 2010-09-01
Yeah.. I actually started to upgrade to Lucid, but it looked like so many things were going to change, I was daunted, and faltered. You know how it is when you have everything "just how you like it." But, I suppose I'll probably roll with the tide eventually, if this problem persists. Thanks for the tip on Synaptic, too. =)

---

### Post by Daug on 2010-12-11
Just wanted to update; it's been a while, but...

I've upgraded to 10.10 Maverick, and it has been all joy. Everything works, acpi, sleep/wake, fn keys, etc. Loving life on my HP 6930p with Maverick. Seems that Ubuntu developers have really been on top of things, particularly laptop hardware.

Occasionally, Adobe Flash breaks when there's an upgrade, but reinstalling flash from scratch always works.

Happy Linuxing to all, and Happy Holidays! =)

---

