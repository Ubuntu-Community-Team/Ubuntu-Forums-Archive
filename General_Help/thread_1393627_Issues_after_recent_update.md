---
title: "Issues after recent update"
date: 2010-01-29
forum: General Help
---

### Post by Dante311 on 2010-01-29
I recently updated through update manager today and it didn't go so smoothly.  It said something about an error updating samba and now Youtube videos do not work (although I have latest flash installed).  It is also not dependent on the browser I use.  Even ads on webpages show up weird:

[ATTACH]145350[/ATTACH]

I know this is very general help question but I'm stuck on how to fix this issue.  I don't even know where to begin.  Any help would be great.  Thanks so much!
[IMG]file:///home/quentin/Desktop/error.png[/IMG]

I use Ubuntu 9.04.

---

### Post by warfacegod on 2010-01-29
Have you tried reinstalling Flash? Or even your browser?

---

### Post by Dante311 on 2010-01-29
Just uninstalled and reinstalled Flash 10 to no avail.

---

### Post by warfacegod on 2010-01-29
Does using an older kernel give you the same problem?

---

### Post by Dante311 on 2010-01-29
Do you mean older version of Flash?  If so, how would I install an older version?  Also, before the update that I performed today, Flash 10 was working fine.  Apologies upfront, I am still learning ins and outs of flash.  Appreciate the replies!

---

### Post by warfacegod on 2010-01-29
> **Dante311 said:**
> Do you mean older version of Flash?  If so, how would I install an older version?  Also, before the update that I performed today, Flash 10 was working fine.  Apologies upfront, I am still learning ins and outs of flash.  Appreciate the replies!

When GRUB loads there should be a list of Linux kernels. 2.6.31-16 / 2.6.31-17 etc. Try the second highest #. If you don't see GRUB then hold esc. while rebooting.

---

### Post by Dante311 on 2010-01-29
I just restarted and am running from the second kernal in the list.  The issue remains.

---

### Post by Jefferythewind on 2010-01-29
Thats too bad.  I had a problem come up after an update one time, I ended up reinstalling the OS.  Good luck.  I think I heard something about some kind of system roll-back to an earlier time., but have never done it.  good luck.

---

### Post by Jerriy on 2010-01-29
> **Dante311 said:**
> I recently updated through update manager today and it didn't go so smoothly.  It said something about an error updating samba and now Youtube videos do not work (although I have latest flash installed).  It is also not dependent on the browser I use.  Even ads on webpages show up weird:

[ATTACH]145350[/ATTACH]

I know this is very general help question but I'm stuck on how to fix this issue.  I don't even know where to begin.  Any help would be great.  Thanks so much!
[IMG]file:///home/quentin/Desktop/error.png[/IMG]

I use Ubuntu 9.04.Believe me [you are not alone]("http://ubuntuforums.org/showthread.php?t=1392606"). Something happened with the recent round of updates as I'm also stuck with a similar problem. 

Oh and by the way, here is a prediction: sooner or later you'll get an advise to simply do a "fresh install" of the flash or the browser or the whole ubuntu or whatever. And unless you're lucky enough to be a Linux programmer or something, you WILL end up following that advice (something that may improve but also potentially worsen the problem since you are essentially tinkering with a flawedly updated system)

---

### Post by kostkon on 2010-01-29
For some reason you removed Adobe Flash and installed Gnash...

---

### Post by warfacegod on 2010-01-29
> **Jerriy said:**
> Believe me [you are not alone]("http://ubuntuforums.org/showthread.php?t=1392606"). Something happened with the recent round of updates as I'm also stuck with a similar problem. 

Oh and by the way, here is a prediction: sooner or later you'll get an advise to simply do a "fresh install" of the flash or the browser or the whole ubuntu or whatever. And unless you're lucky enough to be a Linux programmer or something, you WILL end up following that advice (something that may improve but also potentially worsen the problem since you are essentially tinkering with a flawedly updated system)

Predicting after the fact proves nothing. The update system isn't flawed any more than another OS's. You seem to think that your pessimism can help the OP out better than I or someone else with experience. I leave you to it then because I am bowing out gracefully.

---

### Post by Dante311 on 2010-01-29
I have not installed Gnash....and Flash is installed.

---

### Post by Jerriy on 2010-01-29
> **warfacegod said:**
> Predicting after the fact proves nothing. The update system isn't flawed any more than another OS's. You seem to think that your pessimism can help the OP out better than I or someone else with experience. I leave you to it then because I am bowing out gracefully.Your experience has not helped me so why should I believe otherwise? I have (not only because of advice but also out of my own concern) decided to delete flash and even wipe firefox out of synaptic and installed the whole thing all over again... but to NO AVAIL. Every step I take seems to make the pc slower if anything.

---

### Post by Dante311 on 2010-01-29
I have resolved this issue.  I removed all programs that dealt with Flash and only installed Macromedia Flash plugin.  My videos now work and I browser seems to be performing well again.  Hopefully, this will help others with the same problem.

---

### Post by Jerriy on 2010-01-29
> **Dante311 said:**
> I have resolved this issue.  I removed all programs that dealt with Flash and only installed **[COLOR="Red"]Macromedia[/COLOR] Flash plugin**.  My videos now work and I browser seems to be performing well again.  Hopefully, this will help others with the same problem.And exactly how did you do that?

---

