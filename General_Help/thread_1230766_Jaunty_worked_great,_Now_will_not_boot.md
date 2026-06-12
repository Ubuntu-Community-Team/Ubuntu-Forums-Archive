---
title: "Jaunty worked great, Now will not boot"
date: 2009-08-03
forum: General Help
---

### Post by Squid Tamer on 2009-08-03
I normally don't ask for help if I can't avoid it. (And please exuse my spelling, I am terrible at it and I am on a Windows computer with no spell check.)

Jaqunty has been working great for a few days, and I have been enjoying it. I had very few problems. A few days ago it started failing to boot every so often. Now it doesn't doesn't boot at all.

Grub loads, but after it goes through that weird garbage appears and dissapears on the screen, until it stops at a black screen with some different colored garbage at the top. I attached a picture of it just in case someone has seen this before. 
Recovery mode doesn't work either.
I think that the problem was caused by some hard-resets, where the computer froze due to graphics issues. I try to do it when there is no Drive activity, but it is quite possible that something cot corrupted during one of those.
I have done the fsck in the recovery mode, but it doesn't help.

Does anyone know how to fix it before I re-install?

Edit: I now believe that it does boot, but it is a Graphics issue. I ahve an ATI graphics card. It always/usually (Can't remember) shows some "boot-up-text" before it goes to the garbage screen. Ctrl-alt-f1 or f2 doesn't do anything.

Edit: Resolved. I removed ATI catalyst control.

---

### Post by clonne4crw on 2009-08-08
I had a ATI Radeon HD 2600, and was using the ATI Catalyst drivers. Every time I launched MythTV, the screen got all screwed up, (pretty much like your own screenshots) and the only thing I could do to fix it was reset X and disable the Catalyst drivers.

I blame the Catalyst drivers. I wish there was an alternative to them...

---

