---
title: "Complex problem: sound, graphics, user rights etc."
date: 2012-03-23
forum: General Help
---

### Post by El_Calavera on 2012-03-23
Hi,

I am in serious need of help and couldn't find an answer anywhere.

Today, the following problems simultaneously appeared in my 11.10 system:
– sound stopped working, I am only seeing a "dummy device" in the Sound Settings
– graphics acceleration will not work any more, i.e. I am using the fallback 2D interface now
– I cannot use the User Accounts setting any more, the "Unlock" button is greyed out
– the machine will not shut down or reboot, instead gets stuck somewhere after the usual "Pulseaudio" notice
– Update and Software Center do not work any more: clicking on the "Install" buttons will not do anything
– Log File Viewer does not show anything (literally)

All of these problems appeared at the same time, so they should be connected. It seems like some complex user rights issue, but I have no idea what it might be or how to tackle it.
I am using autologin, in case this is of relevance.


By the way, this problem has a short history:
I ran into a similar issue (just the graphics and Unlock button thing) after upgrading to 11.10 earlier this week. Someone with similar problems on another forum suggested switching from lightdm to gdm and back again. After I did that, the system would not boot any more, always getting stuck after "pulseaudio" or "checking battery state" messages.
Since I had planned on migrating to another HD anyway, I begrudgingly reinstalled Ubuntu and took only the most important data with me (Thunderbirdprofiles etc) in order not to import any bugs.
Everything worked fine for two days, now the problems are back, and more.


Reinstallation did not work, what can I do now? Thanks for reading this post, and any help!

---

### Post by El_Calavera on 2012-03-23
Okay, I solved the problem, although I still don't really understand what happened.

Turns out a dumb hack is to blame which I did years ago:
I am using ecryptfs to encrypt a folder. For some reason, I didn't want it to automount, so crudely I renamed the "auto-mount" file in ~/.ecryptfs/ to something else. That worked well, until the 11.10 upgrade.

I haven't really found any evidence of this in the log files, and only changed it back out of some weird intiution.

Suppose this theaches me not to mess with powers I don't understand… #-o

---

### Post by buckeyered80 on 2012-03-23
Wow. That's interesting. Yeah, I know that encryption can cause alot of weird issues. I guess the OS couldn't read the parts it needed.

---

### Post by El_Calavera on 2012-03-24
Well, the system as such was not encrypted. I only encrypted one folder in which I keep personal stuff, but the rest of my home directory is unencrypted.

Somehow, the impaired exryptfs must have gotten into a lock with lightdm, effectively stripping me of all user rights (sound, shutting down the system etc).

---

