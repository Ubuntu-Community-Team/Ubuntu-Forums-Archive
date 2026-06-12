---
title: "Audio pops &amp; clicks in karmic koala"
date: 2009-11-03
forum: General Help
---

### Post by the real omni on 2009-11-03
I just installed a clean copy of Ubuntu 9.10 i386 on my HP Pavilion dv6000 laptop and pretty much everything works but the speakers randomly pop & click every few seconds, which is obviously unacceptable. Can anyone tell me how to fix this?

Same results whether I use desktop speakers or the built-in laptop speakers.

---

### Post by wildweathel on 2009-11-03
Please search before you post.  

[http://ubuntuforums.org/showthread.php?t=1312690](http://ubuntuforums.org/showthread.php?t=1312690)

---

### Post by the real omni on 2009-11-03
> **wildweathel said:**
> Please search before you post.  


Please read posts carefully before you condescend.

I did a search and found nothing resembling my symptoms. The pops and clicks don't happen when audio playback starts, they happen *constantly* from the time it boots up until the time I shut down and boot to my 8.04 partition.

---

### Post by Dark_Stang on 2009-11-04
I had the same problems on my dv6000. After removing the packages alsa-base, alsa-utils, and linux-sound-base everything was fine.

---

### Post by wildweathel on 2009-11-04
Alright, my apologies.  I was a little tired of answering what looked like the same question for the two-dozenth time since I installed the beta, so I got sloppy.  I certainly don't mean to come across as rude.

(It's okay to mention what you've searched for and found lacking.  It'll help keep people from dismissing your question.)

Okay, now let's be sure that you've got a new problem, though.  The power-save-pop isn't always noticeable at the *start* of audio playback.  In my case, it pops 10-20 seconds after audio stops, and then intermittently for a few minutes after that.  The gold standard is that either 

a) you don't have an HDA-style card (that problem only affects the hda-intel driver)
b) disabling HDA powersaving doesn't fix the problem. (obviously, it's something else then)

Could you post the contents of /proc/asound/cards ?

---

### Post by the real omni on 2009-11-09
> **Dark_Stang said:**
> I had the same problems on my dv6000. After removing the packages alsa-base, alsa-utils, and linux-sound-base everything was fine.

Tried that, the pops and clicks are a bit quieter now but still present.

---

### Post by the real omni on 2009-11-09
> **wildweathel said:**
> Alright, my apologies.  I was a little tired of answering what looked like the same question for the two-dozenth time since I installed the beta, so I got sloppy.  I certainly don't mean to come across as rude.

No worries mang, happy to get any help I can :)

> ... power-save-pop isn't always noticeable at the *start* of audio playback.  In my case, it pops 10-20 seconds after audio stops, and then intermittently for a few minutes after that.

Has nothing to do with power-save as far as I know.. As soon as Ubuntu loads I start getting the pops and clicks and they continue until I shut down, regardless of what I'm doing.

> Could you post the contents of /proc/asound/cards ?

omni@nomad:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6480000 irq 21

---

### Post by Kupfer on 2009-11-09
Hi, I had the same problem. I googled it, but found nothing useful. Then I came across this post by coincidence. I followed the instructions and no popping or clicking sound since.

[http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html](http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html)

---

### Post by CanGooner on 2010-01-30
Thanks for the tip Kupfer! 

The solution in that link has worked for me as well.

---

### Post by the real omni on 2010-01-31
> **Kupfer said:**
> Hi, I had the same problem. I googled it, but found nothing useful. Then I came across this post by coincidence. I followed the instructions and no popping or clicking sound since.

[http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html](http://www.webupd8.org/2009/10/fixing-popping-sound-in-ubuntu-karmic.html)

Thanks a bunch Kupfer, I tried this and the pops & clicks seem to have gone away.

---

### Post by the real omni on 2010-02-05
Well it took me a few days before I actually had a reason to play any audio but now that I have, it seems the problem is only half fixed.

The pops & clicks have gone away so I am now happily using Koala, but all the other audio has been suppressed as well.

---

### Post by the real omni on 2010-02-06
I'm pretty sure the reason audio isn't working is because I uninstalled alsa-base, alsa-utils, and linux-sound-base as per an earlier suggestion.

I've since re-installed the 3 packages but I'm wondering if there's any configuration I'll need to re-do or what.. cause audio is gone

---

