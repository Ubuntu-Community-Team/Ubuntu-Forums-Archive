---
title: "accedently installed x86 instead of x64"
date: 2010-01-27
forum: General Help
---

### Post by Crevatsch on 2010-01-27
hi all!

I had a cd laying around with ubuntu on it, and i wanted to play around with it some more. So i installed Ubuntu, and couldn't believe how slow it was! you've guessed it: i've installed x86 on a x64 computer. now i want to go from x86 to x64, what steps to take?

---

### Post by howefield on 2010-01-27
You would need a complete reinstall with a 64 bit version.

But do not expect huge differences in speed. If your computer is capable of running, then I'd run it. The speed gains will depend on what you are using the computer for.

---

### Post by SuperSonic4 on 2010-01-27
Reinstall although the speed difference is often negligible for day to day use unless you want the system to recognise more than 4gb ram

---

### Post by audiomick on 2010-01-27
If your machine is slow, it might have other reasons than 32 - 64 bit.
What are the specs of the machine?
Which Ubuntu version have you installed?

---

### Post by Crevatsch on 2010-01-27
i have a AMD 4800+ (2.5 ghz) processor and 4 gig of ram, but the whole OS seems laggy to me, the loudness control on my keyboard lags, new screens that come pupping up lag for at least one second before showing something, the same when i want to move screens, and 'unlock' them from their place, and so on. Ive installed the same (x86) software on my parents computer, (which is slightly faster) and there it ran like i was supposed to: without any lag, so i know that it isn't how it's supposed to be(not that its that bad, but i can compare it to something)

if you say i wont notice the gain in speed when i install x64, the Ubuntu experiment will me canceled for me, it's doing exactly the opposite from what i installed if for: being slower than windows 7  :(

the ubuntu version a have installed is probably the latest one: 9.10, from the ubuntu.com website

---

### Post by Zorael on 2010-01-27
That could be a video driver thing. Do you have an ATI or Nvidia card for which you haven't yet installed the proprietary driver?

---

### Post by Crevatsch on 2010-01-27
that could be it... i've installed the ATI drivers for my old HD3650 card that the update manager suggested

the other computer where i have installed it is running on the onboard videocard...

---

### Post by Crevatsch on 2010-01-27
well, that didn't make any difference, has anyone else got some ideas? i really like everything about Ubuntu, but when it's slower then windows it spoils all the fun

---

### Post by jorj82 on 2010-01-27
I don't know if this will help, but you could try an older version of Ubuntu.  Your pc is WAY better than mine, but 8.04 is pretty fast on my machine.

---

### Post by jaezcurra on 2010-01-27
Hi, installing x64 over x86 is not that hard and you are not forced to format the disk.  Just begin the installation and, once at the disk partition stage, choose manual editing and put the "/" onto your former Ubuntu partition and DO NOT format it.  The installation will overwrite your x86 stuff with fresh x64 one without touching the rest.  I did it myself 2 weeks ago and all went flawlessly.

---

### Post by llawwehttam on 2010-01-27
I use 64 bit and it works great for me. It was a big leap in performance. Have a look at the 64 bit link in my signature.

---

### Post by J V on 2010-01-27
open the system monitor and check what is using your ram/cpu...

---

