---
title: "Two Ubuntu Option in GRUB"
date: 2009-12-03
forum: General Help
---

### Post by ChappyHappy on 2009-12-03
I believe the ss says it all. I gained two extra options. An extra Ubuntu and its safe mode.
I dont recall when it started cause I usually just hit restart/power and walk away then come back.

I dont believe it's causing the system any problems. I also dont believe there is two 9.10 on it. I believe it's probably some error on GRUB's part, which I believe can be fixed easily.
Am I correct in assuming those points? I'm still quite newb with Ubuntu and GRUB.
What's the process to fix this? And how to avoid this again in the future?

Thanks!

_[[IMG]http://img682.imageshack.us/img682/4531/pc010020.th.jpg[/IMG]]("http://img682.imageshack.us/i/pc010020.jpg/")_

---

### Post by DeMus on 2009-12-03
> **ChappyHappy said:**
> I believe the ss says it all. I gained two extra options. An extra Ubuntu and its safe mode.
I dont recall when it started cause I usually just hit restart/power and walk away then come back.

I dont believe it's causing the system any problems. I also dont believe there is two 9.10 on it. I believe it's probably some error on GRUB's part, which I believe can be fixed easily.
Am I correct in assuming those points? I'm still quite newb with Ubuntu and GRUB.
What's the process to fix this? And how to avoid this again in the future?

Thanks!

_[[IMG]http://img682.imageshack.us/img682/4531/pc010020.th.jpg[/IMG]]("http://img682.imageshack.us/i/pc010020.jpg/")_

You installed a new kernel. That's it. Just leave it like it is and when you get problems with the new kernel you can always log into the old one. Nothing to worry about.

---

### Post by ST3ALTHPSYCH0 on 2009-12-03
The most recent round of updates included a new kernel, 2.6.31-15. As long as you experience no problems, use that kernel.. if you notice new problems that you didn't have before, continue using -14. You can edit the grub menu to remove the items you don't want to see to alleviate confusion if you like. Search for "edit grub 2 menu". 
So, a direct answer is "no", it's not an error on grub's part, but "yes" it can be "fixed".

---

### Post by ChappyHappy on 2009-12-03
Ah ok, that clears up a few things. Thanks!

Btw, 9.10 is suppose to come with GRUB2. But from what I can see, I have GRUB 1.94 beta installed.
Do I need to upgrade something or is this just a typo?

---

### Post by ST3ALTHPSYCH0 on 2009-12-03
> **ChappyHappy said:**
> Ah ok, that clears up a few things. Thanks!

Btw, 9.10 is suppose to come with GRUB2. But from what I can see, I have GRUB 1.94 beta installed.
Do I need to upgrade something or is this just a typo?

That is Grub 2. Legacy grub or grub 1 ended at ver. .97 or something like that.

---

