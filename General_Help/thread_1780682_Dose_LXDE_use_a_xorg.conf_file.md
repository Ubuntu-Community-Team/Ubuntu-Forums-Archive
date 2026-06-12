---
title: "Dose LXDE use a xorg.conf file?"
date: 2011-06-12
forum: General Help
---

### Post by Jonker on 2011-06-12
Hello All.

Because I had installed Ubuntu 10.10 on a rather old computer, Unity didn't run after updating. So I decided to switch to lubuntu, due to its desktop manager. But when I wanted to configure the xorg.conf file (located at \etc\X11\xorg.conf) I couldn't find any file. I just found the failsafe one.

So, dose LXDE use a xorg.conf file? 

If yes, why is mine missing?
If no, how do you configure it?

Thanks for your help!!!

Jonker

---

### Post by JKyleOKC on 2011-06-12
For more than a year now, all versions of Ubuntu have omitted the xorg.conf file by default. Current versions of the X Windows daemons configure by other means, but will use xorg.conf if the file exists.

That's why you have none in your current installation. You can copy the "failsafe" file to the original name and edit it as necessary, if the automatic detection fails to give you the display resolution you need -- which has happened to many folk since xorg.conf became surplus baggage to the installs.

---

### Post by ajgreeny on 2011-06-12
Presumably you are getting a GUI of the LXDE desktop, so probably do not need the xorg.conf file, as JK says.

However, there are some occasions, depending on your graphic card, when a tweak here and there of that file can make graphics run much better.

What card do you have, and are you noticing any real problems with graphics?  If you're nor sure of the card, run ```
sudo lshw -C display
```and post the output back here.

---

