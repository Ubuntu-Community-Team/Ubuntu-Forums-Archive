---
title: "Clamshell mode in Ubuntu?"
date: 2011-07-24
forum: General Help
---

### Post by cptrohn on 2011-07-24
Hey all out there in Ubuntu land!

Well here is what I am trying to do today...  I am wanting to take the laptop that I use for my job and be able to hook it up to a 23" external monitor, fullsize keyboard and mouse to be able to use as a desktop workstation as well I would like to be able to close the lid while I am doing this but I don't see an option in the power management settings to be able to do it?  I do keep a small Win7 partition on this machine because I need it for work for a few proprietary apps that I have to be able to run, but can't seem to be able to get this figured out in ubuntu...

---

### Post by frankbooth on 2011-07-24
Launch a terminal and type the following command:
```

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"

```

---

### Post by cptrohn on 2011-08-27
This worked like a charm for me Frankbooth!  Thanks for the help!

---

