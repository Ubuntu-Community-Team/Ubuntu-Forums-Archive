---
title: "Xubuntu 11.04 Won´t boot"
date: 2011-09-30
forum: General Help
---

### Post by moustii on 2011-09-30
The last time i wanted to boot my pc running Xubuntu I encounterd some problems. First it gives me the choice wich os I would like to boot in(which is normal). When I chose Xubuntu (11.04) a black screen appeared.

It looked like this:

[http://shakthydoss.files.wordpress.com/2011/09/grub.jpg?w=282&h=179](http://shakthydoss.files.wordpress.com/2011/09/grub.jpg?w=282&h=179)

How do I get rid of this?

I tried running "boot" but it said that no kernel was selected or something like that.

---

### Post by TeoBigusGeekus on 2011-09-30
Your bootloader (grub) seems broken.
You could try reinstalling it using [this]("https://help.ubuntu.com/community/Grub2#ChRoot") method.

---

### Post by 2F4U on 2011-09-30
What are your hardware specs, in particular, what graphics card do you have? Some do not play well with Ubuntu. You may try to add "nomodeset" (without the quotes) as boot parameter and see if that works.

---

### Post by Blasphemist on 2011-09-30
The grub> prompt means grub didn't find grub.cfg, for one reason or another. This page shows how to troubleshoot it. [https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)

You could bypass the troubleshooting and fix it with boot-repair but you probably should troubleshoot it if you can. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

