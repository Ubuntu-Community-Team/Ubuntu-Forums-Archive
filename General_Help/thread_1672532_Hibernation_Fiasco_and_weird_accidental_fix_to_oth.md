---
title: "Hibernation Fiasco and weird accidental fix to other problem"
date: 2011-01-21
forum: General Help
---

### Post by Chirality on 2011-01-21
So, I know people have had issues with hibernation in 10.10 Maverick, I being one such person.

I recently tried a proposed fix from this thread:

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

The problem is that when I started the computer again after the hibernation, which seemed promising, since the computer actually turned off rather than displaying a black screen while everything was powered on and requiring a hard reset. Unfortunately when I powered back on, I got a forever loading Ubuntu screen. I tapped the delete key and the system went a black screen displaying an error:

```
libcrypt version: 1.4.5
Could not stat the resume device file /dev/dm-0
Please type in the full path name to try again or press enter to boot the system

```

So I hit enter... nada. I tried using various combinations of system keys to see if I could get to a shell or something and still no luck. I hit and held enter repeatedly, but no joy.

So I restart and get taken to GRUB. After attempting recovery mode with no further luck, I tried a different Linux version, downgraded from 2.6.35-24 generic to 2.6.35-22

Boom! Everything works as if nothing happened. Nothing is resumed from hibernation, but the GUI is fine, all my settings are in tact, let's break out some cake. First order of business, go to synaptic and remove uswsusp. Done.

Here's the weird thing though. The laptop battery meter was an issue I hadn't gotten around to yet. It always looked like it was charging, and never displayed capacity correctly and was completely unreliable. For the first time since installing Ubuntu, the meter actually gives accurate time left, and no longer shows the computer as charging when unplugged. Apparently I benefited by using this slightly older version of Linux.

This is what I really need help with: Is it enough that I deleted uspwsusp? Is there something else I should do to make sure Ubuntu loads properly the next time I start it? Do I have to continue using this version of Linux otherwise? Any clues as to what happened to the battery meter? Also, I'd still like to get this thing to hibernate if I can.

Thanks!

---

### Post by Chirality on 2011-01-21
Okay further news to report. The battery meter is no longer "fixed", and I have left the computer on continuously since successfully accessing it.

---

