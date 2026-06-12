---
title: "What part of ubuntu is responsible for the laptops Fn+F1-12 shortcuts"
date: 2010-07-04
forum: General Help
---

### Post by cherva on 2010-07-04
What part of ubuntu is responsible for the laptops Fn+F1-12 shortcuts,and for the special keys like the Lock the touchpad key on Asus EeePC ?

---

### Post by sgosnell on 2010-07-04
X-Windows, AFAIK.  If you want to change them, System/Preferences/Keyboard Shortcuts will do that.  You need to install additional software to get the dedicated keys on an eee-pc to work.  Do a search in Synaptic for eee and you'll find what you need.

---

### Post by cherva on 2010-07-05
On Ubuntu 10.04 they worked out of the box and I'm trying to customize a distro based on ubuntu to make them work ... but I don't know what part to change :confused:

---

### Post by sgosnell on 2010-07-05
If they work out of the box, why change anything?  If they work in one version but not in another, it's most likely the kernel that is changing.  You can include a later kernel if you want.  I'm using 2.6.34 in Lucid, and it works well for me.

---

### Post by philinux on 2010-07-05
> **cherva said:**
> On Ubuntu 10.04 they worked out of the box and I'm trying to customize a distro based on ubuntu to make them work ... but I don't know what part to change :confused:

Which distro?

---

### Post by Bachstelze on 2010-07-05
Probably a kernel module. In Ubuntu, type lsmod in a terminal, it will give you a list of all loaded modules. Find the relevant one, Google it to get the source code, build it for your new distro.

---

