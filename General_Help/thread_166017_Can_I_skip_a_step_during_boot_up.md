---
title: "Can I skip a step during boot up?"
date: 2006-04-25
forum: General Help
---

### Post by johnnymo87 on 2006-04-25
I have a problem during boot up where my computer says:
*/ has been mounted 30 times without being check, check forced.*
And then it freezes. I have a hard drive approaching 6 years old, and I know it has flaws. But I also know that if I skip this step, boot up will continue as normal.

So, with recovery mode, I can enter a command somewhere that modifies how my computer boots up (diagnostic modes etc). Is there any command to skip this step or somehow get around it/

---

### Post by Ramses de Norre on 2006-04-25
You can press ctrl+c to cancel fsck. Or in recovery mode use sudo shutdown -rf now to reboot.
By the way: you should make back ups when you're hard drive is acting like this..

---

### Post by johnnymo87 on 2006-04-25
Thank you for your suggestions. Unfortunately, ...

During graphic (regular) boot up, ctrl+c seems to have no effect. In the text version (recovery), ctrl+c also has no effect. 

You said *in recovery mode use sudo shutdown -rf now to reboot*. I have no command line in regular recovery mode, and the 'command line' recovery mode does not respond to any commands I know, not even *sudo shutdown -rf*.

There is an option to edit a boot up command before it's executed. Does anyone know a way to use this option?

---

### Post by cracker on 2006-04-26
I'd suggest booting to a recovery mode or live CD and running fsck manually on the partition, then it will be marked as checked, and boot should continue normally.

---

### Post by dmizer on 2006-04-26
try this [http://www.ubuntuforums.org/showthread.php?t=163500](http://www.ubuntuforums.org/showthread.php?t=163500)

---

