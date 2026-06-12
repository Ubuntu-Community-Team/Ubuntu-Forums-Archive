---
title: "Ubuntu Plymouth logo"
date: 2012-05-18
forum: General Help
---

### Post by Welly Wu on 2012-05-18
I installed GNOME Desktop 3.4 and KDE 4.8 and my splash screen during boot-up and shut down now looks like the KDE icon. I want the original purple Ubuntu logo screen during boot-up and shut down restored.

How do I do this in the terminal?

How do I do this using a GUI?

I know that this must be simple to solve, but I admit that I am too lazy to do a search right now. Please help me solve this little problem. Thank you.

---

### Post by josephmills on 2012-05-18
open terminal 
```
 sudo update-alternatives --config default.plymouth 
```
pick your fancy then 
 
```
sudo update-alternatives --config text.plymouth 
```
pick the the same one as before then 
```
 sudo update-initramfs -u 
```
then (optional )
```
sudo reboot 
```
let us know how it goes 
Joseph

---

