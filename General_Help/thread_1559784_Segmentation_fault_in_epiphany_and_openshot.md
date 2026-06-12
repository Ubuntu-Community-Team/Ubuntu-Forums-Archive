---
title: "Segmentation fault in epiphany and openshot"
date: 2010-08-24
forum: General Help
---

### Post by TheWeakSleep on 2010-08-24
When I open up epiphany, it prompts me to either recover or don't recover my session.
No matter what the decision, it outputs a segmentation fault.

I can load it with a -p switch, as well as loading it as sudo (just to test) so I'm kind of thinking if i can re set the session to default, then I will be able to get around it?

I havent been able to test this though because i cant find where the config files for epiphany are! 

It doesn't output anything useful other than segmentation fault.

As for openshot, I JUST installed it, and it installed with no errors, but when I try and run it, this is the output

```
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 27456.  Creating new pid lock file.
A new frmMain has been created
Segmentation fault

```Any idea? I literally just installed it, wanted to see if it was any good :p

---

### Post by TheWeakSleep on 2010-08-24
bump

any ideas? I really miss epiphany :(

---

### Post by Irony on 2010-08-24
Uninstall openshot, use pitivi - openshot maybe in the repos but it is unstable at best.

---

### Post by TheWeakSleep on 2010-08-24
So the solution is to use a different program?

I was reading a different thread that suggested it might have dependency issues with libcairo2 the version of which I have is 1.9.6-6~mrw4. I assume that I installed it via ppa, though I have no clue which one at the moment :D

anyone know anything about epiphany? I tried removing it completely and reinstalling, but nothing helped.

---

### Post by Irony on 2010-08-26
> **TheWeakSleep said:**
> So the solution is to use a different program?
After openshot shot nautilus to pieces on my desktop that would be my general recommendation.

---

### Post by TheWeakSleep on 2010-08-26
Does anyone have any idea what is causing segmentation fault in epiphany?

---

### Post by Ahz The Cat on 2010-10-14
No idea why its happening, but its happening to me too.  I can sudo epiphany and get a working session, but as user, I get a message that Epiphany shut down unexpectedly and am given the option to recover the previous session or start a new session.  Whichever option I pick, I get a segmentation fault.  Now I'm stuck using firefox for the things that Midori can't handle, and Midori for everything else.  I'm running lucid 64 on a Lenovo lappy, and getting frustrated.  Googling the problem pulls up lots of bug reports and similar problems from Debian users...but no solutions.

---

### Post by Ahz The Cat on 2010-10-15
Just spent a fruitless  hour searching for epiphany config files. :(  No joy yet.  Can anyone suggest good places to look for user settings and config files?

---

### Post by Ahz The Cat on 2010-10-16
Completely uninstalled all epiphany packages via Synaptic, then reinstalled.  Same message...the saved state info must not be in any of the Epiphany data files, rather in a user log or file.  Will have a look... would love some input tho!

---

### Post by Ahz The Cat on 2010-10-16
Or it could be a Flash/PulseAudio giant bundle of pain.  Logs!

[PHP]Oct 16 18:13:14 lenobot kernel: [39105.996317] npviewer.bin[3744]: segfault at f348f04c ip 00000000f61a5757 sp 00000000ff8c8420 error 4 in libflashplayer.so[f5e06000+b2c000]
Oct 16 18:13:21 lenobot pulseaudio[1439]: ratelimit.c: 427 events suppressed
Oct 16 18:13:55 lenobot kernel: [39146.932009] npviewer.bin[7040]: segfault at f58cf054 ip 00000000f6249733 sp 00000000ffc46300 error 4 in libflashplayer.so[f5eaa000+b2c000]
Oct 16 18:14:02 lenobot pulseaudio[1439]: ratelimit.c: 446 events suppressed
Oct 16 18:15:58 lenobot pulseaudio[1439]: ratelimit.c: 444 events suppressed
Oct 16 18:21:50 lenobot pulseaudio[1439]: ratelimit.c: 441 events suppressed
Oct 16 18:27:28 lenobot pulseaudio[1439]: ratelimit.c: 435 events suppressed
Oct 16 18:31:51 lenobot kernel: [40222.928671] npviewer.bin[7072]: segfault at f204804c ip 00000000f620d757 sp 00000000ffb96d90 error 4 in libflashplayer.so[f5e6e000+b2c000]
Oct 16 18:32:01 lenobot pulseaudio[1439]: ratelimit.c: 218 events suppressed
Oct 16 18:35:55 lenobot pulseaudio[1439]: ratelimit.c: 223 events suppressed
Oct 16 18:37:56 lenobot kernel: [40587.329313] npviewer.bin[7449]: segfault at f580f054 ip 00000000f6189733 sp 00000000ff9d3490 error 4 in libflashplayer.so[f5dea000+b2c000]
Oct 16 18:38:29 lenobot pulseaudio[1439]: ratelimit.c: 421 events suppressed
Oct 16 18:40:27 lenobot kernel: [40738.863434] npviewer.bin[7501]: segfault at f57ec04c ip 00000000f6166757 sp 00000000ffdc4870 error 4 in libflashplayer.so[f5dc7000+b2c000]
Oct 16 18:43:26 lenobot pulseaudio[1439]: ratelimit.c: 440 events suppressed
Oct 16 18:45:11 lenobot kernel: [41022.351350] npviewer.bin[7542]: segfault at f38dfade ip 00000000f5eb2fe3 sp 00000000ffb84be0 error 4 in libflashplayer.so[f5e5a000+b2c000]
Oct 16 18:45:45 lenobot pulseaudio[1439]: ratelimit.c: 442 events suppressed
Oct 16 19:08:09 lenobot kernel: [42400.610126] npviewer.bin[7591]: segfault at f30fe04c ip 00000000f61e5757 sp 00000000ffac0fe0 error 4 in libflashplayer.so[f5e46000+b2c000]
Oct 16 19:09:22 lenobot pulseaudio[1439]: ratelimit.c: 440 events suppressed
Oct 16 19:18:23 lenobot pulseaudio[1439]: ratelimit.c: 428 events suppressed
Oct 16 19:21:18 lenobot kernel: [43189.466961] npviewer.bin[7774]: segfault at 8 ip 00000000f60139ea sp 00000000fffad580 error 4 in libflashplayer.so[f5dc4000+b2c000]
Oct 16 19:21:37 lenobot pulseaudio[1439]: ratelimit.c: 425 events suppressed
Oct 16 19:34:47 lenobot pulseaudio[1439]: ratelimit.c: 447 events suppressed
Oct 16 19:39:03 lenobot kernel: [44255.081521] npviewer.bin[7902]: segfault at 8 ip 00000000f60729ea sp 00000000ff845a50 error 4 in libflashplayer.so[f5e23000+b2c000]
Oct 16 20:01:21 lenobot kernel: [45592.443826] npviewer.bin[8041]: segfault at f58a804c ip 00000000f6222757 sp 00000000ffde5870 error 4 in libflashplayer.so[f5e83000+b2c000]
Oct 16 20:26:12 lenobot kernel: [47083.261229] epiphany-browse[8265]: segfault at 0 ip 00000000004428c6 sp 00007fff8fc25f70 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:29:30 lenobot kernel: [47281.691665] epiphany-browse[8298]: segfault at 0 ip 00000000004428c6 sp 00007fffb9fa0f60 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:32:41 lenobot kernel: [47472.726657] epiphany-browse[8318]: segfault at 0 ip 00000000004428c6 sp 00007fff4c274490 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:33:05 lenobot kernel: [47497.011038] epiphany-browse[8349]: segfault at 0 ip 00000000004428c6 sp 00007fffbbfcc920 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:33:16 lenobot kernel: [47507.282512] epiphany-browse[8353]: segfault at 0 ip 00000000004428c6 sp 00007fff8b607070 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:34:41 lenobot kernel: [47592.436194] epiphany-browse[8364]: segfault at 0 ip 00000000004428c6 sp 00007fffe530c980 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:37:46 lenobot kernel: [47777.941580] epiphany-browse[8630]: segfault at 0 ip 00000000004428c6 sp 00007ffff78f1d50 error 4 in epiphany-browser[400000+d5000]
Oct 16 20:56:38 lenobot pulseaudio[1439]: ratelimit.c: 80 events suppressed
Oct 16 21:13:39 lenobot kernel: [49930.472169] epiphany-browse[8902]: segfault at 0 ip 00000000004428c6 sp 00007fffe1924670 error 4 in epiphany-browser[400000+d5000]
Oct 16 21:26:50 lenobot kernel: [50722.050374] epiphany-browse[9034]: segfault at 0 ip 00000000004428c6 sp 00007fff7c259110 error 4 in epiphany-browser[400000+d5000][/PHP]Oct 16 21:26:50 lenobot kernel: [50722.050374] epiphany-browse[9034]:  segfault at 0 ip 00000000004428c6 sp 00007fff7c259110 error 4 in  epiphany-browser[400000+d5000
This little guy seems to be the culprit, or at least the main indication.  Any Epiphany experts out there got any ideas as to what we are seeing here?
:confused:

---

