---
title: "How to fix bootloader using Live CD"
date: 2010-03-20
forum: General Help
---

### Post by lsk3993 on 2010-03-20
I managed to mess up my bootloader using EasyBCD in Windows. Now neither Ubuntu nor Windows will boot up on startup.
I have an Ubuntu Live CD (which I'm currently using) and was looking for a way to fix the bootloader using it.
I found [this thread]("http://ubuntuforums.org/showthread.php?t=224351") which describes how to install Grub with a Live CD but get stuck on the first command...
When I try do "sudo grub" I get "sudo: grub: command not found".

Is there anything I can do?

Thanks

---

### Post by Helkaluin on 2010-03-20
The catch is that the thread you read is for grub-legacy. Now with Grub2 you'll need this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to section 13, four simple terminal commands and you're done.

Good luck!

---

### Post by lsk3993 on 2010-03-20
> **Helkaluin said:**
> The catch is that the thread you read is for grub-legacy. Now with Grub2 you'll need this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to section 13, four simple terminal commands and you're done.

Good luck!
Thank You! Problem solved :D
Naturally being a completely new user I had no idea that I was using the wrong Grub version guide...

---

