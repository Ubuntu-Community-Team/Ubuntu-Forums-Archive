---
title: "shutdown/reboot don't work"
date: 2010-03-12
forum: General Help
---

### Post by LK_gandalf_ on 2010-03-12
Hi, i have a freshly installed Kubuntu 9.10 64bit, and I have a serious issue. If I try to shutdown it or reboot, or even disconnect user, nothing happens. 
To do this, I have to type in the console sudo halt/reboot now every time.
 
I have all the last system updates (not the proposed one, only the official), kernel version is 2.6.31-20-generic, my video drivers are manually installed from Nvidia website.
How to find the cause and fix this?
Thank you

---

### Post by matrix14 on 2010-03-12
It's sound your problem related to both between KDE library and libc. Some unknown symbols in updated libc in which current KDE app's won't recognize it may cause similar problems.

---

### Post by LK_gandalf_ on 2010-03-12
uh, if this is correct, how can i fix the issue?

---

### Post by ubunterooster on 2010-03-12
figure out all running processes and try to find the trouble causing one(s). :(
 Or add the gnome desktop and use that until bug is fixed. :(
  Or manually configure libc (not my level of expertise)

Really wish I could give more optomistic "help".

---

### Post by LK_gandalf_ on 2010-03-24
adding gnome would be really weird :( I don't think (and I hope) it's a bug in kde, otherwise also other users would experience this, right?

An info which maybe could help to solve it. I just formatted my pc keeping my home, and guess what? the issue is still here! SO, at least now we know that it's caused by something in the home.....can you help me finding the reason?

---

### Post by ubunterooster on 2010-03-24
Well I was going with matrix14's assumption of kde being the problem. If you go to synaptic you can get the gnome desktop through the "ubuntu-desktop" package. It can be uninstalled if this does not work, so the only thing lost is some bandwidth. 
  Sometimes one piece of software will conflict with another piece only on certain hardware. 

By the way did this problem begin with an install or did it occur after ubuntu had been installed for a while?

[EDIT] Oh, and try enabling proposed updates [/EDIT]

---

### Post by LK_gandalf_ on 2010-03-25
well it started after some months, probably after a kernel update.
But as I wrote I've just formatted one week ago and the problem was there from the first reboot, with the old kernel too. So it must be some setting in an hidden folder of the home.

---

### Post by ubunterooster on 2010-03-25
If you reformatted, your home folder is clean, right?  Also, before this happened how often did you reboot?

---

### Post by LK_gandalf_ on 2010-03-28
Well not exactly, because I have / and /home on two different partition. So I simply formatted / keeping the home, and the problem was still here. This is why I think that must be something related to an hidden folder.

I tried to backup and remove the whole **.kde** folder, but the problem was still here. So it must be something else.

Is it possibile to read, from a log, what happens when I click on the K menu and then on shutdown? Maybe this will help to find the cause.

---

### Post by ubunterooster on 2010-03-29
Call me stupidly blank, but I forget where the log files for such are. Could you add a custom panel launcher and enter the shutdown order there?

[brainstorm] what if you create a new user, and log in as that one? [/brainstorm]

---

### Post by LK_gandalf_ on 2010-03-29
Uhm I'm sorry but I don't know what a custom panel launcher is :P I use kde, this could be a problem?

Any user on this forum knows how to analyse the log file to find the problem who prevents the shutdown?

---

