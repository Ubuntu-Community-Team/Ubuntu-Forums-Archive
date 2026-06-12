---
title: "nvidia-settings wouldn't save to empty xorg.conf file"
date: 2009-11-27
forum: General Help
---

### Post by manuleka on 2009-11-27
i am trying to run twin view on my nvidia graphics card with ubuntu 9.10

in terminal i ran these commands

```

$ sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo touch /etc/X11/xorg.conf 
$ sudo nvidia-settings

```

when trying to save configuration file i get the bottom error:

```

$ sudo nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.

Segmentation fault

$ _

```

---

### Post by NoaHall on 2009-11-27
Hm. Well, it should be ```
gkusdo nvidia-settings
```.
See what happens when you do that, and post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by sisco311 on 2009-11-27
create a minimal xorg.conf file. 
```
gksu gedit /etc/X11/xorg.conf
```
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by manuleka on 2009-11-27
fixed it... :)

ran:```

$ sudo nvidia-xonfig
```

which prints out:```

$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

then ran:
```
$ sudo nvidia-settings
```

then save and kaboom :)

---

### Post by sisco311 on 2009-11-27
> **manuleka said:**
> fixed it... :)

ran```

sudo nvidia-xonfig
```

d'oh! of course.

EDIT: Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

