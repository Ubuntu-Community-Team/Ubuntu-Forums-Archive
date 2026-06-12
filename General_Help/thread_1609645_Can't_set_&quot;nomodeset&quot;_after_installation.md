---
title: "Can't set &quot;nomodeset&quot; after installation"
date: 2010-10-30
forum: General Help
---

### Post by cwanime123 on 2010-10-30
I'm a newb to Linux and I just installed Kubuntu 10.10 to find out I cannot access the grub menu. I tried alt+f2 but that didn't work. What the real problem is is that I am trying to get the display to turn on at boot since it automatically goes to sleep at boot and cannot be woken up. I could set "nomodeset" for the live cd and it would work fine but I can't find a way to do so when Kubuntu is already installed. Does anybody know how to access the grub menu or how to stop the display from sleeping? Any help is greatly appreciated.

---

### Post by yabbadabbadont on 2010-10-30
You probably just need to edit the /etc/default/grub file and change the "GRUB_CMDLINE_LINUX_DEFAULT" option.  Then you'll have to run "sudo update-grub" afterwards to update the grub configuration file.

---

### Post by drs305 on 2010-10-30
With Grub 2:
To access the menu during boot, hold down the SHIFT key.
Highlight the menu item you want to boot.
Press "e" to edit the item.
Cursor to the end of the "linux" line and add **nomodeset**. Then CTRL-x to boot.

Once booted:
Open a text editor as root, and open */etc/default/grub*
Add **nomodeset** to the *GRUB_CMDLINE_LINUX=""* line.
Update grub with:
```
sudo update-grub
```

---

