---
title: "Change keyboard layout w/o sudo and X"
date: 2011-12-15
forum: General Help
---

### Post by zoff_ita on 2011-12-15
Hi all,

I have access to a Ubuntu Server (no X-server) 11.10 32bit machine as normal user (no root, no sudo) and I need to chande the keyboard layout.

Of course, I can't run the common solution
```
sudo dpkg-reconfigure console-setup
```
cause I can't use sudo.

How can I change the keyboard layout with this configuration?

Is it possible?

Thanks,
- Zoff -

---

### Post by seawolf167 on 2011-12-15
The command 

```
sudo dpkg-reconfigure console-setup
```

will make a system-wide change, for which (as you've noticed) you need admin privileges. You can, however, change your keyboard layout on a per-session basis by using

```
setxkbmap *layout_name*
```

a change back to the  "normal" US layout is

```
setxkbmap us
```

or dvorak

```
setxkbmap dvorak
```

etc.

---

### Post by zoff_ita on 2011-12-15
setxkbmap is a X-server utility.

X is not installed.

Thanks anyway.

---

### Post by seawolf167 on 2011-12-15
Ahh sorry, guess I filtered that part out!

---

