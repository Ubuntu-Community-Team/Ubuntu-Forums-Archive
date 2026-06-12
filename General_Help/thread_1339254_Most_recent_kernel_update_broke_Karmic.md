---
title: "Most recent kernel update broke Karmic"
date: 2009-11-27
forum: General Help
---

### Post by BASH-full on 2009-11-27
I searched around the forums but I couldn't find an exact duplication of this problem. I'm running Karmic as a WUBI installation. Everything was working great until this last kernel up date. When I attempt to boot Ubuntu it takes me into a command line screen that lets me do nothing. The screen reads like this: 
 
**GNU GRUB version 1.97~ beta4 **
 
**Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB lists possible device/file completions.**
 
**sh:grub>*** (blinking cursor)*
 
Please help me get into Karmic! How do I keep kernel updates from breaking Karmic in the future?

---

### Post by ncmncm on 2009-11-27
> **BASH-full said:**
> I searched around the forums but I couldn't find an exact duplication of this problem. I'm running Karmic as a WUBI installation. Everything was working great until this last kernel up date. When I attempt to boot Ubuntu it takes me into a command line screen that lets me do nothing. The screen reads like this: 
 
**GNU GRUB version 1.97~ beta4 **
 
**Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB lists possible device/file completions.**
 
**sh:grub>*** (blinking cursor)*
 
Please help me get into Karmic! How do I keep kernel updates from breaking Karmic in the future?


This is  a known issue and there is a bug in launchpad.
Please see here:[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

If you scroll down to post #19 onwards, you could seem some solutions which may or may not work. 

Apparently wubi+grub2+ext4 causes is problematic!

Hope this helps!


[EDIT]
Ok. Info has been  updated since the last time I  checked. 
Click [https://bugs.launchpad.net/ubuntu/+bug/477169](https://bugs.launchpad.net/ubuntu/+bug/477169)  for more details and possible solutions!

---

