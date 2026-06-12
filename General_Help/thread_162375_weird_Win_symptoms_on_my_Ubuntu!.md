---
title: "weird Win symptoms on my Ubuntu!"
date: 2006-04-18
forum: General Help
---

### Post by damu on 2006-04-18
When I start Ubuntu in the morning , for another day of work on my preferred distro, I now have these symptoms :

.Metacity takes ages at boot...looks like stuck after the first icon of the metacity start menu shows up
. I have to end the process Ekiga, and restart it , otherwise I don't have any GUI (but the process is running!).
. 2 instances of Skype start at the same time. I have to close one.

Mmmm

Could it have a link with the WMware player that I installed?

:confused: X2 3800+, 2 Go DDR, K7 SMP kernel, Ubuntu Breezy

My system :

---

### Post by Face1 on 2006-04-19
I had the same problem as your first one--the splash screen thing.  Turns out it had something to do with gnome's saved session.  I made a new one, and everything began to start normally again.  Unfortunately I stupidly deleted the old one, so I can't diagnose the exact problem.   If you don't care, I'd start using a new session, and my guess is that your other problems will be fixed as well, they seeem related.  If for some reason you want to keep your session, you can try looking at ~/.gnome2/session (it's a text file), and maybe you'll see some weird things.

---

### Post by damu on 2006-04-19
thanks...you're right. I remember now. I tried to save another session than the default, trying to find a way for Ubuntu to start different apps at boot, and hopefully remember in which workspace/window they were. I didn't find the way to do that, but for sure I found a nice way to create a mess ... :)

---

### Post by Phalanx747 on 2006-05-20
I'm experiencing the exact same problem, as also described here: [http://ubuntuforums.org/showthread.php?p=1034733#post1034733]("http://ubuntuforums.org/showthread.php?p=1034733#post1034733"). Unfortunately I don't understand the above solution. What exactly do I have to do to get rid of this problem? Thanks in advance.

---

### Post by Ramses de Norre on 2006-05-20
Your current gnome session (what to start up, config for a lot of things etc) is stored in ~/.gnome2/session. Probably there is something wrong in that file..
I think you might just close all unneeded apps and log out gnome with the save session box checked. But I'm not sure. Or maybe you can just remove the session file to start with clean settings. (just move it to try, you can still put it back then)

---

