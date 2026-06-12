---
title: "WINE and Steam crash my desktop"
date: 2010-04-26
forum: General Help
---

### Post by nerdcore on 2010-04-26
OK so I have a 64 bit Ubuntu OS running. I have installed WINE 1.1.4X and have steam installed. My problem is every time I go and initilize the Steam.exe the whole screen goes blank and the computer reverts back to the Ubuntu login. I am so confused. I have tried installing different things with winetricks and changing the registry and nothing seems to work.

---

### Post by djrobthaman on 2010-04-27
Wow. I just posted with the same problem except I'm using office. You wouldn't happen to have figured this one out yet have you? I'm thinking maybe a wine downgrade would do the trick (at least it could be a short term fix). Have you tried that yet?

---

### Post by djrobthaman on 2010-04-27
Okay.  I tried downgrading to 1.01 and that didn't work for me.  Same error.

---

### Post by nerdcore on 2010-04-27
I also tried to downgrade to 1.0.1 and was successful but now steam loads but I can't see it.

---

### Post by paraplegicpanda on 2010-04-27
I'm assuming we still haven't figured this out? I just tried to start Steam and started having this same issue. Any suggestions?

---

### Post by djrobthaman on 2010-04-27
I think I have it figured out though this is only a short-term fix. If you downgrade wine1.2 to 1.1.31 and uninstall wine (it seems wine is only a dummy package so i suppose wine 1.2 does all the heavy lifting) it might work.  At least, it seems to have worked for me.

---

### Post by Hit in the Head on 2010-04-27
Greetings!

n00b here, but I've been trouble-shooting this from a VM.  I was able to replicate the failure.  I ended up being able to use Steam with Wine1.2 as long as the Screen resolution was a standard 1024x768 .  I know that it is kind of a weird long-shot, but could the issue reside there?

Again, please take what I say with a grain of n00b-covered salt. :)

---

### Post by paraplegicpanda on 2010-04-27
I don't know about the problem with Office, but the problem with Steam seems to be the new Steam update clashing with Wine v1.1.43. I downgraded to Wine v1.1.31 via Synaptic and I can now get Steam running, unfortunately L4D2 doesn't want to work anymore, I 'm now getting the incomplete installation error. I'm about to update to Wine v1.1.42 and see how it works after that.

---

### Post by nerdcore on 2010-04-27
OK, doing a bit of poking I have ended up getting it working. I know now that 1.1.43 WINE is just too unstable to run Steam. I downgraded to 1.0.1 than upgraded to 1.1.27. I also used Vista as the Windows version in the wine. Once done, I rebooted and everything works like a charm.

---

