---
title: "gnome-terminal starts in /"
date: 2009-12-08
forum: General Help
---

### Post by dadrc on 2009-12-08
So my gnome-terminal uses / instead of ~ as working directory when started. And while this is easy to fix (just put 'cd ~' in .bashrc), it's just a symptom and not the problem itself. Some icon pick dialoges (AWN's, in this case) behave the same way. D2 LoD in Wine also can't connect to battle.net and while this sounds unrelated, I'm pretty sure it's caused by the same underlying problem, because if Wine is started from a terminal with the working directory changed to ~, things work fine.

I suspect this weird behavior is caused by some window manager testing I did a few days ago (at least that's when the trouble started). I installed both mutter and xfwm4, played around a bit, decided they weren't what I'm looking and purged them. Ever since then, probably after the next reboot, I've got this problem.

Apparently one of these two changed some setting somewhere that causes my session to bug.

I know this is probably the worst error description ever, but I can't think of a better or more precise way to describe it since I'm totally in the dark about what happened.

I already tried googling and searched a lot of forums and while there are a few people describing the same problem, they usually just add 'cd ~' to their .bashrc and abandon the thread. 

I checked $HOME, points to my home dir, I checked /etc/passwd, points to my home dir, I reinstalled gnome-terminal and gdm (since a friend of mine suspected some breakage), no gain. I've checked all files in /etc/xdg/, nothing out of the ordinary there. I logged in on tty6, it sends me right to ~.

If you've got even the slightest hint as to what might cause this, please post it. If you need any more information or if I forgot to provide something vital, please let me know.

All installed packages are up to date (using both karmic-proposed and karmic-backports).
Ubuntu 9.10  2.6.31-16-generic #52-Ubuntu
GNOME Terminal 2.28.1

---

### Post by dcstar on 2009-12-09
> **dadrc said:**
> So my gnome-terminal uses / instead of ~ as working directory when started. And while this is easy to fix (just put 'cd ~' in .bashrc), it's just a symptom and not the problem itself. Some icon pick dialoges (AWN's, in this case) behave the same way. D2 LoD in Wine also can't connect to battle.net and while this sounds unrelated, I'm pretty sure it's caused by the same underlying problem, because if Wine is started from a terminal with the working directory changed to ~, things work fine.

I suspect this weird behaviour is caused by some window manager testing I did a few days ago (at least that's when the trouble started). I installed both mutter and xfwm4, played around a bit, decided they weren't what I'm looking and purged them. Ever since then, probably after the next reboot, I've got this problem.
.......

Your system probably has been changed, it is almost impossible to guess what it might be since no one else has access to your system.

If you really want to find the problem, you probably need to install a fresh 9.10 system and do a comparison between the configuration files on it versus the broken installation.

---

### Post by dadrc on 2009-12-09
That's what I was afraid of, was hoping to avoid it.

Did some thinking, it pretty much comes down to this: Where does gnome-terminal get its startup working directory from? Can't be $HOME of the current user. Does anyone know or is there another way to find out except for reading the whole source?

Edit: Alright, read through some parts of gnome-terminal's source (which basically seems to consist of black magic to make profiles work) and they get their startup working directory from glib's g_get_current_dir(), which, and here's the trick, seems to return / on error (and if the current directory is /, I suppose). Gotta check that code, too, I guess...

Edit2: Created a little (like 5 LoC) program that just prints g_get_current_dir()'s output, which confirms my suspicion: when called from any GUI, it prints /.

Edit5: Problem exists for a new user, too.

Edit6: Turns out this was caused by disabling gnome-panel and using another run-dialog thingy. Could have sworn it didn't work with panels enabled, neither. Well... thanks for trying to help me, even if there was nothing to help.

---

