---
title: "Flash video stutters &amp; wifi issues after waking from suspend"
date: 2011-06-08
forum: General Help
---

### Post by nerdpecks on 2011-06-08
Hi everyone,

First off, I'll come clean and admit that I am still relatively green to Linux, but I'm not afraid to tackle the complex.

I have a few stroke-inducing issues that I haven't been able to resolve as a  usually do by eye-grepping Google and the various forums. Of course, I'm  running Ubuntu 11.04 with Unity - which is fairly new and undiscovered  country.

I've got this no-name brand, sample laptop from a manufacturing partner  of ours out of Shenzhen China. It's rocking a Core i3 M350 with an  nVidia GT 330M (discreet-ish?)& apparently some flavor of Intel  integrated graphics. 

Now, there are so many variables at play, I'm not quite sure where to  begin - so please bear with this post a bit longer as I unravel the  details.

Loading the nVidia drivers (both proprietary and the experimental open  varieties) results in Unity no longer working and dumping me back to the  classic Ubuntu desktop. I believe it has something to do with the fact  that I have no ability to disable the integrated graphics through the  BIOS and Ubuntu has set its hopes and dreams upon using Intel graphics for the  rest of all time.

That said, running without the nVidia graphics drivers, I am able to use  Unity and it runs pretty well. The only caveat being that on occasion  (read: intermittently), when the laptop wakes up from suspend/hibernate  mode, playing Flash video in full screen gets choppy (stutters).  Restarting Ubuntu resolves the issue. I suppose I should verify that I am using Firefox 4.

In addition, there are times that the WiFi adapter will not wake, and  using the keyboard function key to power cycle it ceases to function. A  complete shutdown is required to address this one. i.e. Restarting and warm-booting does  not fix it.

Did I mention Skype is a terd? I don't actually expect a fix for this pile of hot mess - just thought it might make someone laugh.

If there is anyone here that could lend me a hand with any or all of  these issues, not only will you have the satisfaction of knowing that  you are one bad Mambajamba (TM), but I'll buy you a drink or something via  Dwolla or bitcoin.

Thanks for reading through this -- sometimes it's just nice to get these annoyances off of one's chest.

---

### Post by linuxinstalledfromhdd on 2011-06-08
I would suggest you try using Flash Aid plugin to fix your flash issues:

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

And then if that still doesn't fix it, I would switch to 10.10, and use a complete walk-though and see if your problems still remain:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by cottfcfan on 2011-06-09
The stuttering video after waking from suspend problem is a known bug.
To fix it, go to your repositories in synaptic packkage manager, and tick the proposed updates and backports boxes.
Reload and upgrade all the updates it offers you. Reboot & your video problem should now be resolved.

ps. you might find some of your other issues resolved as well, I did.

---

