---
title: "Start up in shell"
date: 2010-04-18
forum: General Help
---

### Post by Josh K on 2010-04-18
I'd like to change the startup to just present me with a shell asking for a login if that's possible. Is it? :confused:

---

### Post by dominiquec on 2010-04-18
Shell as in command-line shell?

If you disable gdm, you'll end up with a command line login.

```
sudo update-rc.d gdm remove
```

Restore it with:

```
sudo update-rc.d gdm defaults
```

---

### Post by Josh K on 2010-04-18
> **dominiquec said:**
> Shell as in command-line shell?

If you disable gdm, you'll end up with a command line login.

```
sudo update-rc.d gdm remove
```

Restore it with:

```
sudo update-rc.d gdm defaults
```

And I can restore it without an internet connection available?

---

### Post by oldos2er on 2010-04-18
If you're using grub2, edit /etc/default/grub and change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
Then run **sudo update-grub**

---

### Post by Josh K on 2010-04-18
> **oldos2er said:**
> If you're using grub2, edit /etc/default/grub and change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
Then run **sudo update-grub**

I love Linux. 

```
reboot -f
reboot: Need to be root
sudo reboot -f
System Shutting Down NOW!
```

:D 

Okay, now that worked out better then the other solutions (disable gdm, run funny commands on oddly named files). Now if I want to go from that, logout, and startup the GUI how do I do that?

---

### Post by oldos2er on 2010-04-23
If you want to start the GUI, run **startx**. No need to logout.

---

