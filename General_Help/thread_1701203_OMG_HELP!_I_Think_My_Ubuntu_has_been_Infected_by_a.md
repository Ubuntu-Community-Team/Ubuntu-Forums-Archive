---
title: "OMG HELP! I Think My Ubuntu has been Infected by a Windows Virus!"
date: 2011-03-06
forum: General Help
---

### Post by thydeus on 2011-03-06
What happened was I plugged-in and browsed my brothers external harddrive on my Ubuntu OS. It has a lot of movies, games and a bunch of .exe software installers for Windows (he doesn't use Ubuntu).

I couldn't play the games on Ubuntu so I booted up my Windows OS and before I could even open the external harddrive, my antivirus & antispyware went crazy!! 

The harddrive is full of Virus! 

[U][[IMG]http://img827.imageshack.us/img827/5618/omgey.th.png[/IMG]]("http://img827.imageshack.us/i/omgey.png/")
[/U]

I have now unplugged and threw away the external harddrive and I'm running a complete anti-spyware and anti-virus scan on my windows OS.

But now I'm worried that my Ubuntu OS might have gotten infected!

Is it possible that my Ubuntu OS has been infected?

I use a Creditcard and Paypal on my Ubuntu, so I'm really really scared right now. Please help!!!

---

### Post by thydeus on 2011-03-06
I'd like to add that I do not have wine and I did not open any of the infected .exe on my Ubuntu OS.

I'm really new so I hope someone who knows both windows and linux would help. 

btw I'm sorry for my limited vocabulary, English isn't my first language. :(

---

### Post by peculiar penguin on 2011-03-06
I'm not aware of any Windows virus or malware that mounts offline Linux volumes to infect them. Given a lot of effort it would certainly be possible from a technical point of view, but why bother when there must be millions of unpatched Windows boxes just waiting to be taken over?

---

### Post by Joe of loath on 2011-03-06
You may have windows viruses on your Linux partitions, but they won't do anything. If you have WINE, there's a chance that actually running one of the files could lock the PC up, but as WINE is sandboxed it wouldn't do any more damage than that.

More importantly, make sure your windows partition is clean, and tell your brother his hard drive is infected!

---

### Post by AlanR8 on 2011-03-06
Chill

On of the fundamental differences between Doze and Xnix is the fact that you have to give a program permission to run under nix. Not always the case with Doze. In addition, Nix won't recognise a .exe file as something to run natively.

---

### Post by stoneage on 2011-03-06
Install clamav and freshclam, run a virus check. Just for your own reassurance. You might want to run a scan with chkrootkit too, but as people are saying, there is little chance of serious infection.

There is a chance you will find a virus, but as it will be unable to do its work on Ubuntu(because it is coded to run on Windows), it won't have done any harm.

Be wary of false positives though.

:)

---

### Post by kseise on 2011-03-06
Don't worry about it.   I disinfect family drives this way all the time.   Linux doesn't know what to do with exe files.   Even if it did,  the files that the viruses would need to run aren't there.   Like too many windows programs,  they just aren't compatible with linux.   There was a story about 4 years ago of a virus which SHOULD have run but didn't,  so the developers fixed the kernel to run it and issued the patch in the same update.   No worries.   Just run clamav and chkrootkit.    If you are dual booting you should be able to clean up the windows side from your linux side.

---

### Post by thydeus on 2011-03-06
Thank you so much for the advice. :D

I installed ClamAV using Ubuntu software center but unfortunately it won't update. 

I get this error when I try to update it:

[U][[IMG]http://img843.imageshack.us/img843/4295/clamw.th.png[/IMG]]("http://img843.imageshack.us/i/clamw.png/")
[/U]
I've also installed chkrootkit using synaptic, but I can't find it in the applications or the administration tab!! :confused:

---

### Post by stoneage on 2011-03-06
chkrootkit ia a command line application.

> man chkrootkit in a terminal for usage.

---

