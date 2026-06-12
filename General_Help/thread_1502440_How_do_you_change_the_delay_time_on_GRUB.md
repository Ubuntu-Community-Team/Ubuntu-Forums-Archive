---
title: "How do you change the delay time on GRUB?"
date: 2010-06-05
forum: General Help
---

### Post by pking123 on 2010-06-05
I have GRUB "1.98-1ubuntu6", and while I have been using GRUB, I have always wondered how to change the delay time prior to GRUB booting into the default operating system. I would even like to switch it off, if possible. Thanks for any help you may have, as I can't seem to find mention of it anywhere, and I think a 10-second wait is silly, having been accustomed to adjusting LILO to any delay time I liked.

Paul King

---

### Post by philinux on 2010-06-05
> **pking123 said:**
> I have GRUB "1.98-1ubuntu6", and while I have been using GRUB, I have always wondered how to change the delay time prior to GRUB booting into the default operating system. I would even like to switch it off, if possible. Thanks for any help you may have, as I can't seem to find mention of it anywhere, and I think a 10-second wait is silly, having been accustomed to adjusting LILO to any delay time I liked.

Paul King

Easy way, install startupmanager then run it from system>admin

[apt:startupmanager]("apt:startupmanager")

---

### Post by karthick87 on 2010-06-05
If you want to do it manually,type "[COLOR=Red]sudo gedit  /boot/grub/grub.cfg[COLOR=Black]"[/COLOR][/COLOR] on terminal and find the line which says "set timeout=[COLOR=Red]10"[/COLOR] and change the value you want..

---

### Post by yetiman64 on 2010-06-05
> **getyourkarthick said:**
> If you want to do it manually,type "[COLOR=Red]sudo gedit  /boot/grub/grub.cfg[COLOR=Black]"[/COLOR][/COLOR] on terminal and find the line which says "set timeout=[COLOR=Red]10"[/COLOR] and change the value you want..

Not a good idea as this file is dynamic and is influenced by /etc/default/grub and the 6 scripts in /etc/grub.d.  If you want to do it manually.

The setting is changed in /etc/default/grub with 
```
gksudo gedit /etc/default/grub
```and change the "GRUB_TIMEOUT=" setting to your desired time. Then run
```
sudo update-grub
``` to make the setting stick.

Check section 5 out here - [LINK]("http://ubuntuforums.org/showthread.php?t=1195275")  for more info on grub 2 settings and files.

Edit: Setting the "GRUB_TIMEOUT=" value to -1 turns automatic booting off altogether, and grub just sits on its menu until a choice is made by the user. Also startupmanager is the easiest choice as per philinux's post.

---

