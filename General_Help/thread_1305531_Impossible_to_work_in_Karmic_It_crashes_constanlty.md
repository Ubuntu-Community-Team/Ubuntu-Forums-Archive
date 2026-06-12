---
title: "Impossible to work in Karmic: It crashes constanlty"
date: 2009-10-29
forum: General Help
---

### Post by Jorge M 93 on 2009-10-29
Hello community. As you all, I'm an Ubuntu fan, but in this case I've been very disapointed with an annoying issue.

I just wanted to make a fresh install of the recently released Ubuntu Karmic Koala instead of an update from Jaunty, so I downloaded it. (I have a different partition for personal data so I don't lose any important info)

The problem is that every time I used the CD in Live mode, it crashed totaly once i did just a couple of clics or tried to launch an application. When I mean totaly is because the secreen frezzed completly: Including the mouse. The only solution: The "magic" command of [alt]+[Pr.Scr]+R E S I U B.

I thought this would only happen with the Live CD, but once installed, I launched firefox and the same thing happened.

Clues? of course: I didn't upgrade from jaunty because when I did it, Karmic (BETA) didn't allow me to enable the desktop effects, so I thought a fresh install would solve it. I have an Intel graphics card, so maybe this issue could be related to the famous bug jaunty had with the poor perfomance it gave with this cards, but as I read in the release notes is should have been fixed.

However, I plan to buy a decent graphics card (NVidia 9400 GT) this monday. Would this be a solution?

I would be very pleased with your help. Because if I can't find a solution for this problem I will have to consider installing another distribution.

Thanks.

---

### Post by RJARRRPCGP on 2009-10-29
The bug you're talking about, if you're talking about the MTRR bug, wouldn't cause the desktop effects to fail. 

Just slow in fullscreen videos, in my experience.

And going to Nvidia?--> I dunno, because there's an issue where it seems the Nvidia kernel module causes the boot to be slow.

---

### Post by JorgeM93 on 2009-10-30
no idea?

At least... Is there anyone with a similar problem? Its a pain to be obligated to use vista, but I have to.

I you want more clues... I have an Intel celeron processor, 2.5 GB of RAM, a 500GB partitioned disk.

When I upgradaded to karmic BETA it worked perfectly, execpt for the detail of the deskyop effects: 3D rendering worked because in Jaunty the system crached thanks to a 3D screensaver, which didn't happen in Karmic.

I hope this issue isn't related to the linux kernel because I would have no option to use any recent distro.

---

### Post by girto on 2009-10-30
check out if it is related to bug [https://bugs.launchpad.net/ubuntu/+bug/433333](https://bugs.launchpad.net/ubuntu/+bug/433333)
no resolution yet though :(

---

### Post by JorgeM93 on 2009-10-30
Thanx

I saw your link. That's a similar situation. But it isn't exactly random: It happens when you try to launch an application, just moving the mouse isn`t the problem (at least not yet). Also the report in launchpad said it was related to the UNR's special interface which I don't use (I use a deskyop PC).

I think a provisional solution would be to unable the desktop effects, you know, karmic beta worked good for me without them so, is there a way to do it from a console?.

I would like to report this bug, but it won't be so easy because I'm not using Ubuntu.

Tanks for helping

---

### Post by JorgeM93 on 2009-10-30
Well, I booted from recovery mode, and as I saw that no option was related, I resumed normal boot, and (don't really know how) I coud run my appereance preferences and unable the effects. Hope this solves the problem.

I will be testing for sometime, and if this gets solved, will put the [solved] prefix to the thread.

Thank you all.

---

### Post by JorgeM93 on 2009-10-30
OK, now I can finally write a post from my Ubuntu Karmic machine.

disabling desktop effects was totally necessary: This way my system doesn'y crash and I can even work with Blender (which wasn't possible in Jaunty). I tried to enable them again and I got the same problem, so the problem could be related to the X server.

I think I can live without effects... 

Thank you all for your help.

PS: I can't put [SOLVED] in the title of this post because I can't log in as "Jorge M 93", that's why I created a new account as "JorgeM93".

---

### Post by JorgeM93 on 2009-11-01
Oh Yeah! Just for curiosity, I installed the package kubuntu-desktop in order to use KDE.

For my surprise, KWin worked like a charm, and now I can really use my desktop. So this bug **must** be compiz-related.

Now, is there a way to get a system log from my GNOME desktop so I can report my bug succesfully?

---

### Post by JorgeM93 on 2009-11-19
Hey, did someone else got this problem? It would be useful to report it in Launchpad, but now I have my new nVIDIA 8400 GS working perfectly.

---

### Post by girto on 2009-11-20
Good that your problem is solved.

Logs: Check /var/log folder or System->Administration->Log file viewer

You can report a bug in launchpad, then type in terminal:
```
apport yourbugnumber
```
It will send all your system's pertinent info and logs as additional info to your bug report.

Many have reported that disabling compiz has eliminated the freezing.

---

