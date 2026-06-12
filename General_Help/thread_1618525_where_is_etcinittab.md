---
title: "where is /etc/inittab"
date: 2010-11-10
forum: General Help
---

### Post by kaykav on 2010-11-10
hi
        I have 9.10 ubuntu,and do not have a /etc/inittab file
as suggested by [http://www.debianadmin.com/](http://www.debianadmin.com/). If I wanted to start ubuntu in say run level 1 (which I know is not recommended),how would I do that? Come to think of it; run levels 0,1,4,6 are not applicable,leaving 2-5 (normal usage).So changing default run levels does not make sense.    Your thoughts?....thanks..Rich

---

### Post by sisco311 on 2010-11-10
Ubuntu uses [Upstart]("http://upstart.ubuntu.com/"). 

What exactly are you trying to accomplish?

---

### Post by enthy on 2010-11-16
i have lubuntu 10.10 (ubuntu with lxde)
and i can't find **/etc/inittab** or **/etc/event.d/**

i used **sysv-rc-conf** for edit **runlevel**
but i cannot start in Console environnment.

i don't want to use **upstart**
i just want to edit file.

exemple when you edit inittab
you could make a tty log console
how i could do it with no inittab file ???

---

### Post by sisco311 on 2010-11-16
Edit the file /etc/default/grub and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"**.

You can make the boot process verbose by removing the **quiet** option and you can disable the splash screen by removing **splash** (i.e. **GRUB_CMDLINE_LINUX_DEFAULT="text"**).

Create a new GRUB2 config file:
```
sudo update-grub
```

Reboot. The computer will boot into the CLI.

---

