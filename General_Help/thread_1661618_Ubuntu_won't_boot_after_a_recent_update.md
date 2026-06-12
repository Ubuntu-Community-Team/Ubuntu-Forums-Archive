---
title: "Ubuntu won't boot after a recent update"
date: 2011-01-06
forum: General Help
---

### Post by dettadeus on 2011-01-06
I've been running ubuntu on multiple computers for about 8 months now, installed on one computer as it's only OS (XP ran too slowly), and as a side OS for two others, one running XP and one running 7.
The problem is, Ubuntu recently stopped booting on my Windows 7 computer. The option shows at start-up, but when I select it, the computer restarts back to the boot menu. I had recently installed an update from Update Manager that required a Restart, so when I restarted it to finish installing I left it to have dinner and it restarted into windows.
About a day later, I wanted to boot ubuntu again, but my computer simply restarted, and has been doing this since (it's been about 3 days).

I'm not sure if this has anything to do with it, but the last thing I installed before the update was a 1st person shooter game, I can't remember the name, but the icon was a "ka" symbol in katakana (looks like this: &#12459; )

I'm not sure how to fix this, since I'm still relatively new to ubuntu, and can't reach my ubuntu partition from windows. I'm sure it's also a problem that I can't get into terminal either.
Am I going to have to reinstall?

---

### Post by Rubi1200 on 2011-01-07
Hi and welcome to the forums :-)

From your description, I would surmise this is a Wubi install. If so, please confirm this and that you are able to boot Windows normally.

For Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, let us know.

---

### Post by dettadeus on 2011-01-08
Yes, i'm able to boot windows normally (i'm typing this on the computer with the issue).
I suppose I'll just re-install it, since I'm not that good with computer-jargon and such. Didn't really have anything to lose on the partition anyways, I'll just have to reinstall a few programs.
Thanks anyways!

---

### Post by bcbc on 2011-01-08
When you reinstall you'll be prompted by Update Manager. Go through the list and uncheck grub-pc and grub-common. If you look at the wubi megathread Rubi1200 linked to, it describes how you can lock these packages using Synaptic. These updates are what is breaking Wubi installs.

---

