---
title: "Time selection"
date: 2010-06-28
forum: General Help
---

### Post by thefallofroy on 2010-06-28
I'm running Ubuntu using wubi, how do I change the time selection at the bootup when I choose between Windows or Ubuntu?
Also is it possible to make it infinite?

---

### Post by cariboo on 2010-06-28
It depends on what version of Ubuntu you are using. If you are using grub-legacy (Jaunty and earlier, you set the time out in /boot/grub/menu.lst. look for a line that says:

```
timeout	 10
```

set the timeout to whatever you want, then reboot.

In Karmic and newer you need to edit /etc/default/grub. To open the file as root press Alt-F2 and type:

```
gksu gedit /etc/default/grub
```

Once the file is open, look for a line that looks like this:

```
GRUB_HIDDEN_TIMEOUT=0
```

Change the value to whatever you want. After you have saved and closed the file, open a terminal and type:

```
sudo upgrade-grub
```

This will up date the changes you have made. You can now reboot, and wait as long as you set the timeout to.

---

### Post by bcbc on 2010-06-29
if you're referring to the windows boot menu, then it depends on whether you're running xp or vista/7. former uses the 
\boot.ini file and the latter easybcd.

I searched online and it seems you can make it infinte in boot.ini by setting the timeout to -1
Or just set it to 999 (the max).

---

