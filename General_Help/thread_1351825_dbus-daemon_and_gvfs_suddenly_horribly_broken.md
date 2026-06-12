---
title: "dbus-daemon and gvfs suddenly horribly broken"
date: 2009-12-10
forum: General Help
---

### Post by Exüberance on 2009-12-10
Whenever I start my computer dbus-daemon uses up full CPU on one of my 2 processors, and gvfsd now has a memory leak that continuoulsy uses up more and more memory until there's no memory left, so I'm unable to use Ubuntu now. (Though I can still get on for a while until I have to reboot, so I will be able to do any fixes necessary)

I noticed this when I installed xscreensaver, and closed gnome-screensaver. Doing this caused dbus-daemon to use up full cpu (which is normally does when I do anything to restart or close any startup program. Even restarting gdm using RAlt+PrintScrn+K would cause dbus-daemon to crash until I reboot). But this time, rebooting didn't fix it. Now whenever I startup my computer, dbus-daemon uses full CPU and gvfsd has a memory-leak. (and yet, somehow, it's still faster than Vista <_<)

EDIT: Screensaver wasn't at all related to the problem. Turns out it was glipper wrecking havok on my computer. Probably because somewhere it restarts a system process, which for some reason caused dbus to freak out.

What can I do to fix this and what could have possibly made this happen. And if it was just closing gnome-screensaver that did this and not something else, I would say that's a pretty huge security vulnerability!!

---

### Post by Exüberance on 2009-12-10
Also, when I log in as root (and I assume it would work on other accounts too if I had any others), dbus is fine, and gvfs only uses a few megs as it should instead of... well an "infinite" amount, so it must be something on my account that is broken. I would prefer not to make another account again. :/

However, if I log out of root, log into my main account which is broken, log out of it, then log back into root, dbus is broken on root as well. That's strange... and kind of worrysome.

---

### Post by capscrew on 2009-12-11
> **Exüberance said:**
> Whenever I start my computer dbus-daemon uses up full CPU on one of my 2 processors, and gvfsd now has a memory leak that continuoulsy uses up more and more memory until there's no memory left, so I'm unable to use Ubuntu now. (Though I can still get on for a while until I have to reboot, so I will be able to do any fixes necessary)

I noticed this when I installed xscreensaver, and closed gnome-screensaver. Doing this caused dbus-daemon to use up full cpu (which is normally does when I do anything to restart or close any startup program. Even restarting gdm using RAlt+PrintScrn+K would cause dbus-daemon to crash until I reboot). But this time, rebooting didn't fix it. Now whenever I startup my computer, dbus-daemon uses full CPU and gvfsd has a memory-leak. (and yet, somehow, it's still faster than Vista <_<)

What can I do to fix this and what could have possibly made this happen. And if it was just closing gnome-screensaver that did this and not something else, I would say that's a pretty huge security vulnerability!!

Could it be [***[COLOR="Red"]_this_[/COLOR]***]("http://www.google.com/search?q=screensaver+malware+ubuntu&btnG=Go!")?

---

### Post by Exüberance on 2009-12-11
Nope. I didn't download any other screensavers, but just a program that displays them. I tried the fix listed on those pages anyways, but it didn't do anything.

I guess I could just make a new user account, move everything over, delete my old one, then rename it... meh.

---

### Post by Exüberance on 2009-12-12
A-HA!!

The screensaver wasn't the problem, that was just a red herring. It was glipper that was causing the problem and I somehow didn't notice it until I opened system monitor to kill the screensaver.

Dbus is still, and always has been since the start, very very very fragile on my computer, however. Log out and back in? Dbus crashes. Log into another user without restarting the computer? Dbus crashes. Restart gdm? Dbus crashes. Kill or restart gnome-screensaver? Dbus crashes. Restart Dbus? Unable to use keyboard, mouse, or any input device except the power button (if that counts as an input device).

But at least this problem is solved.... too bad now I'm back to sucky copy-pasting tools, that forget what I copied as soon as I close the program :|

EDIT: I found out what was causing dbus to "crash". It wasn't crashing, it was working as intented, but being spammed with messaged from gvfsd. I looked up in synaptic what gvfs does: Gnome Virtual File System. So something is wrong with my mounted drives: Windows.... the program I used to permanently mount /dev/sda1 to /media/windows kind of blew it. I guess it wasn't being unmounted upon logging out or something, but that's what was causing the problem. Unmounting that partition, then mounting it normally with sudo mount /dev/sda1, fixed the problem. It still automatically mounts that partition when I log in, but no more memory leak.

Windows... causing problems when you're not even running it lol. (Well, OK it wasn't actually Windows's fault this time, but it was still pretty to find out that my problem was because of Windows.

---

