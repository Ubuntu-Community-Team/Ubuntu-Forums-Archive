---
title: "Transmission at start up in 11.04?"
date: 2011-05-26
forum: General Help
---

### Post by lockdown1101 on 2011-05-26
Hey guys, I can't seem to get transmission to boot up at start up. I read that I just needed to put "transmission -m" as the command in the start up window, but that doesn't seem to be working and I have no idea where the actual file resides to point to it.

Can anyone help? Thanks!

---

### Post by mikewhatever on 2011-05-26
You probably want 'transmission-gtk' in Ubuntu or 'transmission-qt' in Kubuntu. These are the GUIs, and if you need non-GUI, use 'transmission-daemon' (you'll need to set it up beforehand).
Not sure what 'transmission -m' is supposed to do, there seems to be no such executable in Ubuntu.

---

### Post by fdrake on 2011-05-26
```
man transmission
     -m --minimized
             Start minimized in notification area
```

---

### Post by kerry_s on 2011-05-26
> **lockdown1101 said:**
> Hey guys, I can't seem to get transmission to boot up at start up. I read that I just needed to put "transmission -m" as the command in the start up window, but that doesn't seem to be working and I have no idea where the actual file resides to point to it.

Can anyone help? Thanks!

that should work, you need to turn on the icon in transmission for it to start minimized.

---

### Post by fdrake on 2011-05-26
> **lockdown1101 said:**
> Hey guys, I can't seem to get transmission to boot up at start up. I read that I just needed to put "transmission -m" as the command in the start up window, but that doesn't seem to be working and I have no idea where the actual file resides to point to it.

Can anyone help? Thanks!

do u want transmission to start up when you start up ? that's what u want?

---

### Post by ewanroberts on 2011-06-19
I was having the same problem, I wanted to have Transmission Auto Start when ubuntu starts up. 
thanks to mikewhatever for the solution:

> You probably want 'transmission-gtk' in Ubuntu or 'transmission-qt' in Kubuntu. These are the GUIs

so I added:

```
transmission-gtk -m
```

to the startup applications' preferences dialogue and now transmission opens minimised when ubuntu starts. :KS

---

### Post by lailokenwiz on 2011-07-29
> **lockdown1101 said:**
> Hey guys, I can't seem to get transmission to boot up at start up. I read that I just needed to put "transmission -m" as the command in the start up window, but that doesn't seem to be working and I have no idea where the actual file resides to point to it.

Can anyone help? Thanks!
in applications-internet-... right click transmission and create a launcher
you can then drag it into the start up applications and edit the command (add -m to the command)

good luck

---

