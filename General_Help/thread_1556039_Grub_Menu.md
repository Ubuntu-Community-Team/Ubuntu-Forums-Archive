---
title: "Grub Menu"
date: 2010-08-18
forum: General Help
---

### Post by Jonny87 on 2010-08-18
I want to remove the grub boot menu that shows up on start up so that it just goes straight to Ubuntu.

Is there a simple way to do that?

---

### Post by hudsonl on 2010-08-18
> **Jonny87 said:**
> I want to remove the grub boot menu that shows up on start up so that it just goes straight to Ubuntu.

Is there a simple way to do that?


You could just change the timeout to 0 in the menu.lst file

> vi /boot/grub/menu.lst

---

### Post by rollin on 2010-08-18
Hopefully you can get your answer here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2). I think it should be hidden by default unless you have two OS installed. If so I think you need to uncomment the line GRUB_HIDDEN_TIMEOUT line in /etc/default/grub.
The link should help you determine what you need to change.

---

### Post by Jonny87 on 2010-08-18
Ubuntu is the only OS but for some reason its coming up tough thats why I want to stop it.
Thanks guys I'll try those suggestions.

---

### Post by wilee-nilee on 2010-08-18
> **Jonny87 said:**
> I want to remove the grub boot menu that shows up on start up so that it just goes straight to Ubuntu.

Is there a simple way to do that?

0 is not good at least 1 second should be kept for ease of other system access.

Change it with in the terminal
```
gksudo gedit  /etc/default/grub
```
Look for this line
GRUB_TIMEOUT=3 
and change the time then run ,
```
sudo update-grub
```

You might consider burg if you want a more graphic looking bootup choice. Here is what mine looks like, the resolution in this shot is wrong the icons and panel are much smaller in the actual gui.
[ATTACH]166847[/ATTACH]

---

