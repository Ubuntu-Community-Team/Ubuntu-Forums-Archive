---
title: "Ubuntu 10.04: suddenly can't log in, no GUI, no nothing"
date: 2010-09-29
forum: General Help
---

### Post by Objekt on 2010-09-29
I don't know what happened, but suddenly I can't log in my Ubuntu 10.04 install.  It was working fine as recently as yesterday, and nothing nasty happened to the hard drive it's on (hardware failure, poweroff without proper shutdown, etc.).  When I tried to log in earlier, all that happened was this: the screen blanked momentarily, then I was back at the login screen again, as if I had never tried to log in.

It's not that I'm entering an incorrect password.  I don't get any kind of error message.  I just get kicked back to the login screen.

WTF is going on?  I'm posting this from my Ubuntu 9.10 install, which still works.  I guess I could use Ctrl + F1 to login to Ubuntu 10.04 on the command line, but I'm not sure what I could do from there to find out what's gone wrong.  Any ideas?

---

### Post by spiky001 on 2010-09-29
Have you tried logging in then startx

---

### Post by mocoloco on 2010-09-29
On the login screen, change your session type to "failsafe GNOME".  If you can log in with that there's something in your user settings or autostartup that's keeping you from logging in correctly and you could try disabling stuff in System -> Preferences -> Startup Applications.

---

### Post by Objekt on 2010-09-29
That's the other weird thing.  There aren't any choices of how to log in.  The menus that should be on the gray bar at the bottom of the screen simply aren't there.

---

### Post by mocoloco on 2010-09-29
I saw this once when a system was almost completely out of disk space.  Do you think that's possible the problem?  To deal with that you can boot in to recovery mode, and one of the options is something like "clear disk space".

---

### Post by Objekt on 2010-09-29
I fiddled with it some more while you guys were posting. 

I tried logging in console-mode by pressing Ctrl + F1 (or is it Ctrl + Alt + F1?) at the graphical login screen.  I was able to log in, and I then tried to start the GUI with the "startx" command.

It didn't work, I guess because the X server was still running in the background from the GUI login screen.  So I killed that X server process and tried again.

I got a black background with a mouse pointer, and I could hear my video card's fan running, but the system just sat there like that.

I then thought it might be a problem with the Nvidia drivers.  They have become broken spontaneously in the past.  I also tried booting in Recovery mode, attempting to use the "failsafe X" GUI.  It behaved exactly the same as I described in my initial post.

It occurs to me that the last time I was running 10.04, there were a number of updates.  Perhaps one of them broke something vital?  Sure looks that way.

The next thing I am going to try is, reinstalling the Nvidia drivers from the console.  I've had to do this before, to rebuild the kernel modules when I got a new kernel revision for Ubuntu 9.10.  Maybe that's all that's going on.

Drive space probably isn't the issue.  I have 5 GB free on the 8 GB system partition, and 4 GB free on the 5 GB /home partition.

update:
Nope, that did nothing.  I reinstalled the current Nvidia x86 drivers (256.53), but got the same result when I started the GUI.  I was just staring at a black screen with a mouse pointer, with nothing happening.

---

### Post by monnom on 2010-09-29
Just experienced what seems to be a similar problem...

Just ran updates on Ubuntu 10.04 and it said it wanted to reboot after the updates finished installing.  When it came back up the GUI would not start.  It gave the text-based login prompt.

-It was working fine right before the update.
-I tried STARTX but that wouldn't get the GUI running either.
-Plenty of disk space.  
-RUNLEVEL is "N2" (but I don't know what that means).

Any ideas what happened?

Any suggestions to troubleshoot and get the GUI back?

This is Ubuntu Studio 10.04 64-bit and I need the GUI for multimedia work on this workstation.

HELP?

---

### Post by Objekt on 2010-09-29
Well, nuts.  It does sound like the latest round of updates screwed us.

By the way, I'm running the 32-bit flavor of 10.04.  I had too many hassles with the 64-bit version of 9.10.

I have a netbook which dual-boots Ubuntu Netbook Remix 9.10 as well as desktop 10.04.  I haven't used it for a couple of days.  So it's time to turn it on, install the updates, & see whether its GUI gets all messed up as well.

update:
Nope, the netbook is fine.

I still can't get the 10.04 desktop to do anything useful.  Whether I start it up in low graphics mode or not, I get tossed back to the login screen every time I try to log in.

update2:
**OK, it's fixed now.**  I haven't a clue how it happened, but it seems *gnome-session* somehow got uninstalled.  We aren't the only ones to have had this problem with 10.04.  Here's a thread on this topic, with solution on page 2: [http://ubuntuforums.org/showthread.php?t=1507373&page=2]("http://ubuntuforums.org/showthread.php?t=1507373&page=2")

---

