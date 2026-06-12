---
title: "Problems topped off with AssaultCube crash"
date: 2009-12-03
forum: General Help
---

### Post by motonnerd on 2009-12-03
Alright, I'm posting a few problems here:

1st:  I think it started when I did one or two hard shutdowns (which I never liked anyway, but sometimes... yeah)  Anyway, it would reboot and after the little white xfce mouse on the black background went away (before login) it would sometimes freeze.  I could log into Windows, though, and the next time I tried it would be OK.  Any thoughts on what happened?  I wonder if I corrupted something or triggered some kind of flag on the HDD that freaked out XUbuntu.

2nd:  I downloaded/extracted AssaultCube, tried to run it (hadn't done any compiling or anything, kinda weird instructions. I ran it, my screen went black, and never returned until I did another hard shutdown.  I tried ctrl+alt+backspace, but nothing happened (PS/2 keyboard, USB mouse, I believe the computer was nonresponsive as concluded from my favorite test, hitting the num/caps/scroll lock keys and watching the lights) So I've sworn off AssaultCube until I can figure out what's going on there, or someone makes a good .deb/package for it.

3rd:  Now, I can't login using either xfce-session, however I can login to my GNOME sessions, the failsafe and the other, though since it's XUbuntu there's not much installed.  Login to the XFCE session is incredibly slow (orders of magnitude slower) if I am lucky enough to get past the splash screen, which often freezes.  Is there a way to edit XFCE-session settings remotely, without wiping everything?

I'm running a 2.5GHz machine with 512M of RAM (8M shared w/ the onboard video card) XUbuntu upgraded from 9.4 to 9.10 without issue, and PCI sound and wireless B cards.  I removed all the non-package applications I had put on excepting AssaultCube, which I deleted.

So, I want to know this:
     Any solutions to my problems?
     I'll take another look at the AssaultCube installation thread, but has anyone gotten a similar result? (I installed a bunch of dev packages as instructed, and have now removed them -- could that have messed up the system?)  I extracted the update into the same install folder as the 1.0 (watch, that's gonna end up being the problem) assuming that since it was smaller it must rely on at least part of the first.  Furthermore, I'm more concerned about restoring my system.
     In Puppy Linux ctrl+alt+backspace kills X and drops me into a commandline.  Is there an equivalent command for Ubuntu?
     Also a cool thing from Puppy Linux -- I'm able to do a 'version update' to the currently-installed version.  (thereby wiping a lot of bad configurations and halfway restoring the OS, but not wiping out the majority of my custom settings.  Is there a Ubuntu equivalent?
     And last, paling in comparison to everything else, a small annoyance:  is there a way to make my system remember to keep the numlock key on by default?  Should that be in the saved session?



Any help is greatly appreciated!
--Christopher

---

### Post by motonnerd on 2009-12-05
Well, I'm not sure how I did it, but I'm back in XFCE apparently unharmed.  Here's what I did:

I have been using a combination of Win. XP and the builtin GNOME/Failsafe GNOME sessions in order to maintain functionality, though missing the awesome black theme I had on XFCE.  Whether the GNOME use has any effect beyond just getting at the system, I don't know.

However, today I remembered my favorite old standby:  command prompt.  Furthermore, I remembered my favorite command, bar none:  hitting the tab key twice.  I typed in xfce and tabbed until I got a list of options (takes four, the first just completes the statement to xfce4-, common to all options) and went into the session editor.  I made some changes in there (removed GNOME support at boot and tried to look for sessions to delete, but none existed, probably because I wasn't in XFCE)  

So xfce4-settings-manager, and xfce4-session-settings were the two commands I used, which pop up windows (to my great delight) in the GNOME session, adn that's how I changed the settings.
If I was to choose one which probably was most beneficial, I would say that it was probably changing the splash screen from XUbuntu to 'none', as the computer would always hang when the splash screen came up.

It should be noted, though, that before this I went though the synaptic package-manager and removed anything with -dev, provided it had a non-development version which could be used in its stead.

What specifically worked I don't know, but that's what I did, and my computer's working now!

---

