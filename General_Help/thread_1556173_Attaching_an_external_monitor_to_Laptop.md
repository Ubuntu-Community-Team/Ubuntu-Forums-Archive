---
title: "Attaching an external monitor to Laptop"
date: 2010-08-19
forum: General Help
---

### Post by TheNessus on 2010-08-19
Hi all,

So I bought an external monitor for my laptop. In charge of monitor settings in Gnome is my Nvidia-settings, because of my Nvidia GPU.

If I close my laptop lid, both monitors do either of the following: hibernate, sleep, or turn off display. I don't have a "nothing" option, and I would need one of these three anyway when mobilizing with the lappy. 

How do I close the lid and have the external one operating?

Thank you :)

---

### Post by TheNessus on 2010-08-19
solved it

"/apps/gnome-power-manager/buttons/lid_ac

to the value 'nothing' without single quotes."

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236)

---

