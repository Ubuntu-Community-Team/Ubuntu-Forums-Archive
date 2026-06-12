---
title: "Where is the power button and System Admin in Ubuntu Oneiric Ocelot?"
date: 2011-11-12
forum: General Help
---

### Post by sprogmeister on 2011-11-12
I upgraded to 11.10 and can no longer find the power button, or where I can do system admin. I am having real problems with mt wireless on this system and one work around lists goig through System > Admin, but I cannot find it. Also, I cannot find a power button and thus need to log off before I power off. Please help.

---

### Post by sprogmeister on 2011-11-15
I still cannot find a quicker way to turn the system off, other then to log off first. I have tried to use windows wireless to install drivers to make  the wireless work (I have the disk). The disk contains a Linux:gurivers file but I cannot get it to install. I see the .exe file and .ini but am unable to get the file to install. Can anyone advise please?

---

### Post by BillyBoa on 2011-11-15
Let's see if I understand. Normally the power off is on the up right corner. You push on the corner and scroll down you go to Shut Down and that's it.

if you like to use terminal CTRL+ALT+T and

```
sudo halt
``` or

```
sudo shutdown -h now
```

To find the apps, go to the upper left corner and push the Dash. From there in the search box right the name of the application you are asking or just find the option applications and they are scrolled down all.

To install the wireless drivers right "jockey" to the dash search and choose Additional Drivers.

---

### Post by sprogmeister on 2011-11-15
Thanks,  have no on/off button top right. I will try the drivers idea.

---

### Post by BillyBoa on 2011-11-15
If something is missing there is a solution

from a terminal try this commands one by one

- to reset the Unity launcher icons:

```
unity --reset-icons
```

- to reset Unity:

```
unity --reset
```

- to reset Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by sprogmeister on 2011-11-16
Tried and the later 2 commands bring up a warning that compiz is unable to bind with the framebuffer. I am sorry, I do not understand this

---

### Post by BillyBoa on 2011-11-16
Let's see if we can do something, write to a terminal:

```
sudo apt-get install --reinstall ubuntu-desktop
```

With this you reinstall Unity

---

### Post by sprogmeister on 2011-11-16
I have followed your instruction but terminal just scrolls the same fault. I have attached a screen shot for clarity. Many thanks for your patience and help.

---

### Post by sprogmeister on 2011-11-17
I thought I had had the wireless issue resolved but Windows Wirelss doesn't recognise the .ini file. Any suggestions?

---

