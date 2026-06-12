---
title: "Resolution is stuck low after switching drives to AHCI in BIOS"
date: 2012-06-25
forum: General Help
---

### Post by j03l5k1 on 2012-06-25
I'm trying to set up a raid 5 on my Ubuntu HTPC.

I realised that in bios my drives were set to IDE mode.

I changed this to AHCI and now the resolution is extremely low (800 x600)

Switching thing back to IDE makes everything normal again.

Does anyone have any ideas, what could be wrong?

---

### Post by irv on 2012-06-25
Did you check to see if there was a bug reported on this, and if not maybe file one if someone can't help.
Questions:
Are you using an onboard video? And with is your video card?
What kind of computer are you using? And the spec?

This is just the starting point to try to get to the bottom of your problem. Many times someone will have the same configuration or close to it as you do.

---

### Post by j03l5k1 on 2012-06-25
Hi irv, thanks for your reply,

I had done some searches using googlubuntu.com, didn't have that much luck.

The PC is being used as an HTPC

its running
9800GT
core 2 quad 9650
4 1TB hard drives (2 stuck in raid that i was trying to fix that caused this)
2GB ddr 3 ram

---

### Post by irv on 2012-06-25
What about the video? Is it on board? or a separate card?

---

### Post by j03l5k1 on 2012-06-25
Sorry, the 9800GT is a pcie card

---

### Post by irv on 2012-06-25
This is strange that changing your BIOS from IDE mode to raid 5 would have anything to do with a video using PCI. 
One more thing. Your BIOS is it up to the latest version? You may want to check to see if it is up to date. That would be a good place to start. I remember having some different issues once and flashing my BIOS fixed it. It is worth a check.

---

### Post by j03l5k1 on 2012-06-25
Im thinking I may just format the OS and install with the bios set to AHCI.

Would be a quick solution.

Also, I haven't actually configures the drives into raid mode yet. Just the controller to to AHCI from IDE.

Its also worth noting that the OS is not actually installed on the drives I intend on raiding.

---

### Post by irv on 2012-06-25
> **j03l5k1 said:**
> Im thinking I may just format the OS and install with the bios set to AHCI.

Would be a quick solution.

Also, I haven't actually configures the drives into raid mode yet. Just the controller to to AHCI from IDE.

Its also worth noting that the OS is not actually installed on the drives I intend on raiding.
Hope things go well with this. Yes, maybe you are on the right track. Set everything the way you want and then install. With a clean start hopefully things will go well.

---

### Post by j03l5k1 on 2012-06-25
The format has done the trick, everything is fine now, thanks for all your input irv.

Now, on to figure out how to unraid these two windows drives........

---

