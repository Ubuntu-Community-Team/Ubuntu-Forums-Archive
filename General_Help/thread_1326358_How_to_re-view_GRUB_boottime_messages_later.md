---
title: "How to re-view GRUB boottime messages later?"
date: 2009-11-14
forum: General Help
---

### Post by mahy on 2009-11-14
Hello everybody,

after the recent GRUB upgrade, I get a warning at boottime. As I press enter for "Ubuntu 9.10", I see a message about some graphical settings being deprecated, and that I should use something else. But this warning only appears for a split second, and then hides under the Ubuntu splash image. I'd like to review this warning once the boot process is finished, just like I can view "dmesg" messages. Is it possible?

Moreover, I'm afraid the most recent GRUB upgrade didn't work out really well. A dialog screen popped onto me from Synaptic, but I didn't pay much attention and only clicked "next". How do I re-initiate the whole upgrade process so that I can change anything if necessary? The command "update-grub" or package reinstallation don't seem to do the trick...

Any help much appreciated.

---

### Post by falconindy on 2009-11-14
You can use scroll lock to pause the messages as they scroll by. You may also want to temporarily edit out 'splash' from the entry you're booting off of.

Btw, chances are high that if you're seeing a message about deprecation, the fix is going to be coming from upstream. I wouldn't worry about it.

---

