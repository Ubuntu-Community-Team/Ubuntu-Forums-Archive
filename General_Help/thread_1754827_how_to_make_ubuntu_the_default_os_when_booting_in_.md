---
title: "how to make ubuntu the default os when booting in dualboot machine ?"
date: 2011-05-10
forum: General Help
---

### Post by doron387 on 2011-05-10
hi guys,
i have ubuntu 10.10 installed in dualboot with win7 on a asus 1201n netbook.
the first os in the first black screen boot menu is win7, which means that it is the default os to boot if i don't use the arrow down to ubuntu.
well, i had enough experience with ubuntu to decide that i want to defaultly boot into ubuntu.
does anybody know how i change it ?
[there is no menu.lst file in 10.10, so i didn't find the way to do it]

waiting for your reply, 
thanks ahead,
doron387

---

### Post by philinux on 2011-05-10
> **doron387 said:**
> hi guys,
i have ubuntu 10.10 installed in dualboot with win7 on a asus 1201n netbook.
the first os in the first black screen boot menu is win7, which means that it is the default os to boot if i don't use the arrow down to ubuntu.
well, i had enough experience with ubuntu to decide that i want to defaultly boot into ubuntu.
does anybody know how i change it ?
[there is no menu.lst file in 10.10, so i didn't find the way to do it]

waiting for your reply, 
thanks ahead,
doron387

I this a wubi install or a regular dual boot?

---

### Post by grahammechanical on 2011-05-10
You can installed something called Grub Customizer. Search for grub-customizer in the Ubuntu Software Centre. That will let you set the boot order among other things. Or Startup Manager.

Regards.

---

### Post by wilee-nilee on 2011-05-10
> **philinux said:**
> I this a wubi install or a regular dual boot?
+1 or easybcd,

---

### Post by doron387 on 2011-05-10
well thanks to you both.
i have rebooted to my win7 os, because i thought that i remembered a software called EasyBCD 2.0 that i once used for this purpose.
i wasn't wrong.
in EasyBCD 2.0 in win7 i changed it within 2 seconds.
so thanks a lot for your replies.
consider it as SOLVED

---

### Post by wilee-nilee on 2011-05-10
> **doron387 said:**
> well thanks to you both.
i have rebooted to my win7 os, because i thought that i remembered a software called EasyBCD 2.0 that i once used for this purpose.
i wasn't wrong.
in EasyBCD 2.0 in win7 i changed it within 2 seconds.
so thanks a lot for your replies.
consider it as SOLVED

Excellent that is the best choice for changing the MS boot menu, if you don't want to do it manually.

You might want to be aware that the wubi, I think you have can be moved to a partition at some point if you so desire.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

