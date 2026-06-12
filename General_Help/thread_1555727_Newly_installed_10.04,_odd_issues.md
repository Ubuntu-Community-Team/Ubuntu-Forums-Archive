---
title: "Newly installed 10.04, odd issues"
date: 2010-08-18
forum: General Help
---

### Post by muffhuff on 2010-08-18
I just installed Ubuntu on my fathers Pavillion laptop and I am having some weird issues. At first everything worked fine "out of the box" but after 3 or 4 reboots I am having some issues. I am quite sure there is something wrong with authentication. But don't know how to rectify it.

First of all I could mount the windows partition in Linux without problems, after the problems arose I can't, it throws me back with a permission denied error. Secondly I can't reboot or shutdown the system, It just keeps throwing me back to GDM.

Opening the terminal and typing 'sudo shutdown -r' and typing the root password it restarts.

The same username and password (which where created at install) was used before the problems arose and the same user are used after the problems I haven't created any additional usernames. The only changes I have made to the system is creating a keychain for the wireless network and made it remember the keychain password.

Any suggestions to how I can fix this?

---

### Post by arpanaut on 2010-08-18
The -r option requests that the system reboot...

In terminal:

```
man shutdown
```

---

### Post by muffhuff on 2010-08-19
> **arpanaut said:**
> The -r option requests that the system reboot...

In terminal:

```
man shutdown
```

Thanks for the help that solves all of my problems

Seriously read the post before you reply

---

