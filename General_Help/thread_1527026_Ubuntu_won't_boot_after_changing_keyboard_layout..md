---
title: "Ubuntu won't boot after changing keyboard layout."
date: 2010-07-08
forum: General Help
---

### Post by guzz20 on 2010-07-08
Please somebody help me, this is giving me a headache.

When I installed Ubuntu on my laptop I selected English US (dead keys) as my keyboard layout, but a couple of days ago I decided to change it to English US (dead keys ALTGR) so I just went to the keyboard settings and added the layout, then deleted the old one "English US (dead keys)", logged out and selected the new one "English US (dead keys ALTGR)", logged back in and then restarted, and now I can't boot into Ubuntu, all I get is Grub but when I enter to Ubuntu I get a black screen and the Caps Lock light blinking.

Thanks.

---

### Post by BurningSludge on 2010-07-08
[FONT=Comic Sans MS][SIZE=3]Do you have a live DVD or a system rescue disk?[/SIZE][/FONT]

---

### Post by guzz20 on 2010-07-08
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]Do you have a live DVD or a system rescue disk?[/SIZE][/FONT]

I have the live CD of Ubuntu 10.04 Desktop Edition.

---

### Post by guzz20 on 2010-07-09
Somebody? 

Maybe someone can give me a link to where are the files that are used to configure the keyboard layout in 10.04? so I can edit them and add the "dead keys" layout, I found /etc/default/console-setup file, I changed it but it didn't worked so I guess it may need to be updated with a command like update-grub (not that one obviously) for example?

---

### Post by simosx on 2010-07-10
> **guzz20 said:**
> Please somebody help me, this is giving me a headache.

When I installed Ubuntu on my laptop I selected English US (dead keys) as my keyboard layout, but a couple of days ago I decided to change it to English US (dead keys ALTGR) so I just went to the keyboard settings and added the layout, then deleted the old one "English US (dead keys)", logged out and selected the new one "English US (dead keys ALTGR)", logged back in and then restarted, and now I can't boot into Ubuntu, all I get is Grub but when I enter to Ubuntu I get a black screen and the Caps Lock light blinking.

Thanks.

This is not a keyboard layout issue; you mention that the problem appears when grub is running (or failing to run properly). At that stage no keyboard layout has been enabled. In fact at that point  not even the Linux kernel managed to start. What grub does is it tries to find the partition with your installation and a /boot subdirectory, identify the kernel image and run it.

The keyboard layout settings come into work when you get to the GUI interface.

What you can do is find the documentation on how to change the parameters that grub uses when it boots Linux. There is a 'quiet' parameter that you can remove and then see all the details of the booting process. Where it fails would be the point of failure.

---

### Post by guzz20 on 2010-07-10
> **simosx said:**
> This is not a keyboard layout issue; you mention that the problem appears when grub is running (or failing to run properly). At that stage no keyboard layout has been enabled. In fact at that point  not even the Linux kernel managed to start. What grub does is it tries to find the partition with your installation and a /boot subdirectory, identify the kernel image and run it.

The keyboard layout settings come into work when you get to the GUI interface.

What you can do is find the documentation on how to change the parameters that grub uses when it boots Linux. There is a 'quiet' parameter that you can remove and then see all the details of the booting process. Where it fails would be the point of failure.


Oh, I see, So it's probably an Ubuntu or Gub problem I'll try that "quiet" parameter. That's a very weird problem if I can't find the problem soon I'll have to re-install Ubuntu. :cry:

I'm still covinced the keyboard layout somehow triggered this problem.

---

