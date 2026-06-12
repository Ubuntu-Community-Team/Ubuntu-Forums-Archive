---
title: "changes to grub's menu.lst not taking effect"
date: 2010-03-06
forum: General Help
---

### Post by graymalkn on 2010-03-06
I'm running 9.10 and recently edited my /boot/grub/menu.lst file to change the default kernel and timeout. I've done this plenty of times before but this time the changes didn't take effect. I can reopen menu.lst and the changes are there but when i reboot it acts as though nothing has changed. Any thoughts on what could cause this?

---

### Post by Intrepid Ibex on 2010-03-06
Karmic uses grub.cfg (grub2) by default (instead of grub-legacy, which uses menu.lst).

You should try startupmanager (get it with synaptic or straightly with apt, with "sudo apt-get install startupmanager") and tweak the settings with it.

Here's everything and more you need to know about grub2 (using the search feature is allowed): [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by wojox on 2010-03-06
Did you run:

```
sudo update-grub
```

---

### Post by graymalkn on 2010-03-06
Ah hah! It seems I was just being an old fart about things. /boot/grub/grub.cfg had a warning not to edit the file directly but pointed to /etc/default/grub for making changes. I changed there then ran update-grub and now all is well. Thanks for pointing me in the right direction!

---

### Post by gleble on 2010-04-11
This is exactly my problem. If I edit menu.lst it has no effect. I have tried running sudo grub-update. I've read piles of forum entries to no avail. I am running Jaunty.

---

