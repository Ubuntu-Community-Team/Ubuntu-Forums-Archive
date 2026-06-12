---
title: "How to stop automounting"
date: 2012-05-01
forum: General Help
---

### Post by layers on 2012-05-01
I need to plug in a usb hard drive, but I don't want the system to do anything to it; I have to mount it by myself, and so stuff to it.

Is there a way to do this, which is easily reversible? I like automount in my everyday life, it's just that only now, it mustn't automount.

---

### Post by JRV on 2012-05-01
Install ubuntu-tweak with these commands:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
Run the program
Select Tweaks=>File Manager
Toggle Automatically Mount Media to off.

---

