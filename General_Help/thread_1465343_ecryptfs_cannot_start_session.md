---
title: "ecryptfs cannot start session"
date: 2010-04-29
forum: General Help
---

### Post by fabjoa on 2010-04-29
Hey everybody

I recently encountered a quite critical issue on my level. So on my GRUB i have 2 OS, both Xubuntu 9.10, one is for storing data such as videos and mp3s and the other is the one i use for work. So lately I did something wrong, I manually shut down computer while Windows XP was running in Virtual Machine (Sun). Next time I boot, I enter Xubuntu, enter my password, it thinks and takes me back to the enter password prompt without telling any error messages such as Authentication Failure. You probably know that in xubuntu you can choose your session on startup. If I choose GNOME or Term, I can access my session, but regular xubuntu session won't work. So I enter a GNOME session and i see that there is a .ecryptfs folder next to my user folder in /home. It kinda links because when I try to enter a regular xubuntu session (the one that does not work) I can see a black screen with written 'starting init crypto disks' for a second and then it takes me back to login screen as decsribed above. So i did a big rookie mistake, I manually deleted the .ecryptfs folder and since then nothing is working. I then opened a Xterm session and run fsck but it's a no-no too.

Am I clear enough? Is there somebody out there who knows some magic formula? I must say too that i can access data of the disk through the other disk running xubuntu with dolphin.

Any help more than appreciated? THX

---

