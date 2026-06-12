---
title: "command to change action when lid is closed."
date: 2011-11-04
forum: General Help
---

### Post by tuxonapogostick on 2011-11-04
Hi all.

I would like to change the power management action from suspend to blank screen when laptop lid is closed. I am wondering if I can do this from command line. I did some search on ubuntu frums and google but have had no luck yet. Generally speaking my question is about how to do power management from command line.

Any help is appreciated.

Cheers.

---

### Post by duke.tim on 2011-11-04
The default power config file is in

/etc/default/acpi-support

if you are going to be using the terminal you would use

```
vim filename
```
or
vi
pico
emacs

rather than the gui gedit

---

### Post by SteveDee on 2011-11-04
Do you mean this: [http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

---

### Post by tuxonapogostick on 2011-11-04
I couldn't find in this file anything regarding laptop lid. What I am looking for is something like: **command lidclosed action blankscreen**. It would be nice If I knew what option/file gnome-power-pref gui is changing when I change laptop lid closed action from suspend to blank screen.

---

### Post by tuxonapogostick on 2011-11-04
Thans for the link. It is definitely relavent, but it didn't help much.

---

### Post by matt_symes on 2011-11-04
Hi

> **tuxonapogostick said:**
> Hi all.

I would like to change the power management action from suspend to blank screen when laptop lid is closed. I am wondering if I can do this from command line. I did some search on ubuntu frums and google but have had no luck yet. Generally speaking my question is about how to do power management from command line.

Any help is appreciated.

Cheers.

Are you using gnome or Unity with gnome-power-manager ?

If so then
```

gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_ac -s "blank"
gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_battery -s "blank"
```The other options besides blank are suspend, hibernate and shutdown.

Kind regards

---

### Post by tuxonapogostick on 2011-11-04
> **matt_symes said:**
> Hi



Are you using gnome or Unity with gnome-power-manager ?

If so then
```

gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_ac -s "blank"
gconftool-2 -t string /apps/gnome-power-manager/buttons/lid_battery -s "blank"
```The other options besides blank are suspend, hibernate and shutdown.

Kind regards
Yes, I am using gnome-power-manager within unity. When I first tried it, it didn't work. Later, I tried it again and **it worked like a charm**. Thanks a lot for this.

---

