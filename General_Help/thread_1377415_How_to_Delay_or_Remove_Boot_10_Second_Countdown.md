---
title: "How to Delay or Remove Boot 10 Second Countdown"
date: 2010-01-10
forum: General Help
---

### Post by Ataraxian on 2010-01-10
I am Dual-Booting Windows 7 and Ubuntu 9.10. At start-up I am presented with the available operating systems and then given 10 seconds to choose one or it will automatically start Ubuntu.

Can I remove this timer, lengthen it, or have it automatically go to Windows? 

Any help would be appreciated,

Thank You!

---

### Post by drs305 on 2010-01-10
The solution is here: [Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

You edit the /etc/default/grub file and change the GRUB_TIMEOUT="10" line, then run "sudo update-grub" to update the grub.cfg file.

---

### Post by Ataraxian on 2010-01-10
Thanks for the quick reply!

I'll try it now.

---

### Post by Ataraxian on 2010-01-10
There are no command lines to edit in the grub (/etc/default) - gedit

---

### Post by drs305 on 2010-01-10
> **Ataraxian said:**
> There are no command lines to edit in the grub (/etc/default) - gedit

```

gksu gedit /etc/default/grub

```

If you try to open a file with gedit or another text editor and get a blank file it's normally because the address is incorrect. If the text editor doesn't find the file at that location, it creates a new (blank) one.

These instructions assume you are using Grub 2 with Karmic. If you updated from Jaunty and are still using Grub Legacy, look for "timeout" in /boot/grub/menu.lst

---

