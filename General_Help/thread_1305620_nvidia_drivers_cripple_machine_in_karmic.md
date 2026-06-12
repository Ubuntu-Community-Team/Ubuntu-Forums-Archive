---
title: "nvidia drivers cripple machine in karmic?"
date: 2009-10-30
forum: General Help
---

### Post by TrevorBradley on 2009-10-30
Hey there.. I've just done an upgrade from jaunty to karmic and am having some serious video problems that appear to be holding me back.

My machine has an onboard nVidia 6150 that works amazingly well with a 1900x1200 monitor.  Compiz worked quite well with snappy performance, when things were working.

I had some issues back in the jaunty days.  Long ago I installed a beta nvidia 180 driver and it's been a bit kooky since.. saying I have an outdated nvidia driver many times during kernel updates.  Before my update, the server's graphics would be a bit sluggish, but I would log out, log right back in again, and things would be OK.  Not a great solution, but since the machine was rarely rebooted it seemed to be OK.

Now that I've upgraded though, I can't seem to get this working at all.  Firstly I had a horrible problem where the screen would flicker and xorg would complain that it had no screens... turning off UseFBDev in xorg.conf fixed that.  The system does indeed load with nvidia drivers, though windows take forever to open, frame rate appears atrocious, and certain apps (like terminal) don't seem to open at all).

I *can* use the nv video driver and all is fine (except performance and screen resolution) and I might live with (less) crappy graphics for a few days.  But I would like to get this fixed.

Can anyone provide me some clues as to what might be going on?
What log files should I provide to attempt to track down a whacky nvidia driver problem?

Thanks in advance!
Trevor in Canada

---

### Post by TrevorBradley on 2009-10-30
OK, as suggested by others elsewhere on the forum, I tried installing the latest 190 nVidia drivers from their website.. I have acceleration now.

Compiz still makes it run really slow, but I think that's another (related?) matter...

---

### Post by NRDNick on 2009-10-30
Have a look here [http://ubuntuforums.org/showthread.php?p=8171854#post8171854]("http://ubuntuforums.org/showthread.php?p=8171854#post8171854") and try forcing your powermizer option to performance mode, either with the method described or simply by selecting the performance mode in the Nvidia-settings app. It has fixed my issues here, hopefully it'll help a few others as well.

---

### Post by michwill on 2010-02-27
I'm still having the issue, even after following the instructions.  Are there any updates we're missing?  I'm running Ubuntu 9.10 and the NVidia 190.53 driver.

FYI, I tried posting to the linked thread, but it's not open to additions.

Best.

---

