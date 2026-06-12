---
title: "Bad Motherboard?"
date: 2009-10-15
forum: General Help
---

### Post by rhpot1991 on 2009-10-15
So running Karmic (though the same issues seem to exist on Jaunty as well) I have lost the ability to use my Hauppauge pvr-xxx cards and firewire.  In dmesg I see the following:

john@ultramagnus:~$ dmesg |grep error
[    0.439356] pci 0000:01:09.0: BAR 0: error updating (0xec000008 != 0xfc000008)
[    6.106842] amd64_edac: probe of 0000:00:18.2 failed with error -22

It seems like motherboard is having issues.  I'd love to hear anyone else's opinions before I order a replacement.

---

### Post by akakingess on 2009-10-15
Just to clarify, they were working and then just one day, poof, no more firewire? Or have they never worked within Ubuntu?

---

### Post by P4man on 2009-10-15
hmm.. did you try loading an older kernel?
Looks like there is a problem with the northbridge, but it could be a kernel issue just as well as a hardware issue /me guesses.

---

### Post by Giblet5 on 2009-10-15
> **P4man said:**
> hmm.. did you try loading an older kernel?
Looks like there is a problem with the northbridge, but it could be a kernel issue just as well as a hardware issue /me guesses.

+1 on the Northbridge diagnosis, though it'd likely be the Southbridge handling firewire. Same result.

Maybe it's time for that Nehalem... :/

---

### Post by rhpot1991 on 2009-10-15
Yep, they were working earlier yesterday afternoon.  Then I did some updates, moved some hardware around, and poof things stopped working.  Currently running  2.6.31-14-generic, I booted to 2.6.31-13-generic and that didn't help at all.  Then I took my old HD with Jaunty on it, threw that in (where they were all working before upgrade) and they are not working in there either, got the same error message in dmesg.

Planning on calling up ABIT for a RMA later this morning, then I'll go home for lunch to reseat everything and flash the bios.

---

### Post by akakingess on 2009-10-15
I think you are on the right track, it most definitely sounds hardware related to me, I don't even know if flashing the BIOS would help, but as long as you're in there, right?

---

### Post by P4man on 2009-10-15
> **rhpot1991 said:**
> 

Planning on calling up ABIT for a RMA later this morning, then I'll go home for lunch to reseat everything and flash the bios.

I was about to suggest trying a BIOS reset (and/or upgrade). Another thing to try, though perhaps far fetched, but is running a memory diagnostics. Am I right in guessing you have ECC ram ?

---

### Post by rhpot1991 on 2009-10-15
> **P4man said:**
> I was about to suggest trying a BIOS reset (and/or upgrade). Another thing to try, though perhaps far fetched, but is running a memory diagnostics. Am I right in guessing you have ECC ram ?

Non ECC, I'll give the memory a check too.

---

