---
title: "Grub won't let me hide the menu with Windows installed."
date: 2009-12-27
forum: General Help
---

### Post by Mike_IronFist on 2009-12-27
I have a dual boot of Ubuntu and Windows Vista. Now I've edited my Grub config file (/etc/default/grub) tons of times, with GRUB_HIDDEN_TIMEOUT=0 not commented out. For some reason, this does not hide the menu for me, and the only way that grub will hide the menu is if I set GRUB_TIMEOUT=0 . The issue with this is, I can't get to the menu if I ever want to boot into Windows, because the menu will display for 0 seconds (not at all)!

However, that's the only way I can hide the menu - it won't hide it otherwise.

I was originally booting pure Ubuntu, and I could get the menu to display, as usual, by holding the Shift key. How come, even with the GRUB_HIDDEN_TIMEOUT and other stuff factored in, I can't get grub to hide the menu?

Please help.

EDIT: And yes, I do know to use
```
sudo update grub
```
after each modification.

---

### Post by meierfra. on 2009-12-27
This has worked for me:

[http://ubuntuforums.org/showthread.php?t=1362642#4]("http://ubuntuforums.org/showthread.php?t=1362642#4")

---

### Post by Mike_IronFist on 2009-12-27
> **meierfra. said:**
> This has worked for me:

[http://ubuntuforums.org/showthread.php?t=1362642#4]("http://ubuntuforums.org/showthread.php?t=1362642#4")

Actually I found another solution thanks to a link from the bug page on Launchpad. I'll post it in this topic later for future reference once I find it again.

Thanks for your help though!

---

