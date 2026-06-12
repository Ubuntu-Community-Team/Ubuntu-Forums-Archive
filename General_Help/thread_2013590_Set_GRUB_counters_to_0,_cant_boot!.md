---
title: "Set GRUB counters to 0, cant boot!"
date: 2012-07-01
forum: General Help
---

### Post by aryzing on 2012-07-01
Hi All,

After reading [Ubuntu's GRUB 2 help page]("https://help.ubuntu.com/community/Grub2") and the [Configuration page]("https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2"), I set both counters to zero
```
GRUB_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT=0
```
I did so because I want my laptop to boot straight into the OS, except if I maintain SHIFT key depressed (which is supposed to trigger the GRUB2 menu to appear, acording to the help).
When I try this, the "booting straight into the OS" part works perfectly, but when I hold the shift key depressed, I get a message saying that grub is starting, but again the default OS boots without prompt, i.e. i dont get to see the grub selection menu.
So now I can only boot into one OS :(

If possible, I am looking for two answers:
1. Why is this not working as I expected it to?
2. How can I edit the grub file from a live CD (because my default OS is Win7)

Any other solutions and suggestions to tackle the problem are very much appreciated too!

Sorry if this was a n00b error, I hope the solution is not to hard. Thanks for any help!

---

