---
title: "What is this I don't even..."
date: 2010-10-26
forum: General Help
---

### Post by Uruz on 2010-10-26
Everything seems to have gone wrong.

Last night I decided to find out if I could set my Clock in a different language (just for fun, you know?) so I went to Language-Support (or whatever it's called, I can't really check right now) and found the Numbers Dates and Currency language setting. I changed that and logged out and back in so that the changes would take place.

It worked! But then my internet didn't. I decided to reboot. It took a REALLY long time to shut down (normally it does it before the first animation of the bar is complete).

Grub loaded, I started booting Linux and... it hung before hitting the boot screen. After waiting a while, it decided that it had waited long enough and dropped to some weird command-line after telling me that it couldn't find my kernel based off of its UUID.

I had had an oddly similar problem (misplaced kernel)on my netbook just earlier and so I attempted the same fix I used there. It didn't work.

So I went to the recover mode thing (sorry, I'm not feeling well and my head is kind of fuzzy) and it got stuck repeating the same process in its boot process over and over again. I tried again and I got through and ran dpkg and the other things that seemed like they might help.

I tried booting again and it worked-ish. I got a report after the standard system-scan telling me that there errors on the disk (not that weird, I had been forced to turn off my computer when it got hung) so I fsck'd it and rebooted.

Ubuntu took forever to boot but seemed to be working until I tried to log in. The stuff disappeared as usual but nothing else loaded. I just had my login-screen background and my mouse. After a long while nothing happened so I dropped to TTY1 to shut down. It got stuck repeating the same portion of the log-in process over and over again. I went to TTY2. This actually worked but I couldn't remember the command to initiate gdm (as I said, I haven't been feeling well and this was LATE last night)so I rebooted. Tried to boot Linux and got the missing kernel error again.

Just before I went to be last night I tried everything over again and tried logging in this morning. I got logged in to my user but dropbox reinstalled itself after it was already running, all of my applets gave me errors and disappeared from my bar, my Nautilus bookmarks consisted of a single folder with a weird name (looked like it might be the location of where the data for the bookmarks is kept or possibly some sort of internal nautilus command. Nautilus was unable to open anything and gave me an error telling me that it could not handle it. Running Firefox seemed to make the toolbar hang and then attempting to open the shut-down menu produced a blank window. I dropped to TTY1 and got stuck in the login loop.

Now I can no longer even boot recovery-mode.
--

The only thing that I can possibly think might have done this is that I installed updates (I'm working to upgrade to Maverick) and it said that some stuff couldn't be reached (did this from my University's internet, could that have affected it?)

Anyway, I have not idea what to do now, any help would be much appreciated.

Thank you,
Uruz

---

### Post by ender4 on 2010-10-26
Did you attempt an upgrade to maverick, and stop in the middle, because that could definitely mess stuff up.  

If you can't find a better solution, you may need to boot from a LiveCD, backup any data, and reinstall Ubuntu.

---

### Post by Uruz on 2010-10-26
> **ender4 said:**
> Did you attempt an upgrade to maverick, and stop in the middle, because that could definitely mess stuff up.  

If you can't find a better solution, you may need to boot from a LiveCD, backup any data, and reinstall Ubuntu.

I never actually began the Maverick upgrade, only updating other programs.

Also, Re-installation is the absolute last thing I want to do. I've spent weeks tuning everything to be just how I want it and If I did reinstall, my nvidia drivers would break and I'd have to go that mess all over again.

**EDIT**
I tried booting it again, ran FSCK when it told me there were errors, rebooted and now it works. I don't know how stable it is though and I'm upgrading to Maverick ASAP.

---

