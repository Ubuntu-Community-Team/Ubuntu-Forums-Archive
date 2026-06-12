---
title: "Upgraded to 10.10 Encrypted Windows Partition now says &quot;Error: Invalid Signature&quot;"
date: 2010-11-14
forum: General Help
---

### Post by tibbyuk on 2010-11-14
Hey guys,

Am in urgent need of help, as I have been an idiot and upgraded my linux boot on my work laptop, and can't get into Windows now, and am starting work in 11 hours!

The issue is,

That my entry for windows XP "That I manually added into etc/grub.d/40_custom" returns an error of "error: invalid signature"

The entry is as so:

```
menuentry "Winows XP" {
set root=(hd0,1)
chainloader +1
```

Now the thing that I've noticed is different, is that during the boot process I am not asked to enter a password to decrypt my windows partition (which I had to previously).

I'm assuming that Grub is somehow bypassing this step, and as such I can't decrypt my drive.

Does anyone have any idea on this one? Any help is greatly appreciated.

---

