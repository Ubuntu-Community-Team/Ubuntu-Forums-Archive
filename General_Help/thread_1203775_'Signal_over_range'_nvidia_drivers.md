---
title: "'Signal over range' nvidia drivers"
date: 2009-07-03
forum: General Help
---

### Post by Langy on 2009-07-03
Hey, I've searched these forums and google for related problems, but none seemed to match my circumstances. Small background:

Relevant (I think) system specs:
AMD Athlon 64 3800+ 2.4ghz
Nvidia geforce 6100 nforce 405 integrated graphics
Ubuntu 9.04 kernel 2.6.28-11 and -13 (tried both)
1024x768 monitor, '50-60 Hz' (from back of monitor)

Ubuntu had worked perfectly for 2 weeks or so after intalling the reccomended Nvidia 180.44 drivers via System>Administration>Hardware Drivers. However after booting up yesterday morning i was met with 'Signal over range' on my monitor after the Ubuntu loading bar had finished, at the login screen. I tried using 'xfix' from the recovery menu which brings me to a 800x600 display and I reinstalled the drivers, but i still kept getting 'signal over range' at the logon screen.

After several hours of research, changes and reboots I came across one option in the xorg.conf that *appeared *to solve the problem, which was to add:

```
Option "useEdid" "FALSE"
```to the 'Monitor' section. This let me login as normal in the proper 1024x768 resolution, and i thought the problem was over.

But now i have another mysterious problem that relates to pretty much any graphical media; for example I tried playing a file using VLC media player, which was stuttering, both the sound and video. this was the same for several formats, and streaming. I ran 'glxgears' from terminal, and noticed that every 10 seconds or so it would lock up for about 5 seconds at a time, during which the mouse was unmovable, any sound that was playing would loop, and after the pause, streaming media I was playing through VLC stopped. I also tried loading up an online game through Wine, but this also shows the same symptoms as 'glxgears', only more pronounced with longer and more regular pauses. In the online game after the first 5-10 second pause, it was apparent that it's connection to the internet had also been interrupted.

I then tried starting over completely, and reinstalled Ubuntu 9.04 from Live CD, installing the nvidia drivers, reboot, but once again I get 'signal over range' at the logon screen, and using 'Option "useEdid" "FALSE"' ' just brings about the stuttering/pausing/locking up.

I am at a loss on what to try next. As i said, the normal nvidia drivers, default xorg.conf, and all media/games were working perfect after installing Ubuntu for the first time 2 weeks ago, up until yesterday; I have made no hardware/software changes to bring this about.

Any help would be deeply appreciated, i am unable to get Ubuntu working properly with any nvidia drivers I have tried.

Thanks in advance, sorry for the mass of info, i thought i had better describe everything I had tried, and the symptoms.

---

