---
title: "verbose boot in 11.04?"
date: 2011-09-08
forum: General Help
---

### Post by jerguy1928 on 2011-09-08
hey i have ubuntu 11.04 am i am wondering is there any way to have verbose boot?

---

### Post by dcstar on 2011-09-09
> **jerguy1928 said:**
> hey i have ubuntu 11.04 am i am wondering is there any way to have **verbose boot**?

Which means?

---

### Post by oldos2er on 2011-09-09
> **jerguy1928 said:**
> hey i have ubuntu 11.04 am i am wondering is there any way to have verbose boot?

If I'm understanding you correctly, make a backup copy of /etc/default/grub ```
sudo cp /etc/default/grub /etc/default/grub.original
```

Edit the file ```
gksu gedit /etc/default/grub
``` Change the line 
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to GRUB_CMDLINE_LINUX_DEFAULT="text"
Close gedit and run ```
sudo update-grub
``` Reboot.

---

### Post by jerguy1928 on 2011-09-11
this isn't quite what i was thinking of. when i do this, it does a text based bootup like i wanted, but on its done with booting i want it to go to gdm and not just command line.

---

### Post by oldos2er on 2011-09-12
That's what it should do (start gdm), and I don't really understand why it isn't working for you. If you run **startx** after logging in, does your desktop come up?

---

### Post by jerguy1928 on 2011-09-17
yes but i switched from wubi to a partition, and changing that line of grub will have the screen be purple, then have the already booted code, and then give the login option (but not gdm, the command line login like before).

---

### Post by oldos2er on 2011-09-18
Is the package gdm installed? If so, try **sudo dpkg-reconfigure gdm**

---

### Post by jerguy1928 on 2011-09-18
> **oldos2er said:**
> Is the package gdm installed? If so, try **sudo dpkg-reconfigure gdm**

gdm is installed (checked with synaptic), tried it, nothing changed.

---

### Post by bcbc on 2011-09-18
Removing 'quiet splash' should do what you want? You can experiment by hitting 'e' on the grub menu entry and manually editing it (remove quiet splash, or in your case also 'text') and then Ctrl+X to boot. If it works make it permanent.

If the grub menu doesn't show automatically hold SHIFT down to see it when you boot (although if you have a dual boot it always shows).

But why do you want to see the 'verbose boot' every time?

---

### Post by jerguy1928 on 2011-09-18
it does do it, but what happens is it flashes the code for like one second and then goes to gdm, in another words if possible i would like to see it in real time. By the way, thanks for you help so far people.

---

### Post by bcbc on 2011-09-18
> **jerguy1928 said:**
> it does do it, but what happens is it flashes the code for like one second and then goes to gdm, in another words if possible i would like to see it in real time. By the way, thanks for you help so far people.

Why don't you just browse your /var/log/syslog and other log files? I don't know how you can read anything useful as it flashes by so quickly - it's helpful when it's freezing at some point, but that's about it.

---

### Post by jerguy1928 on 2011-09-18
alrite thanks.

---

