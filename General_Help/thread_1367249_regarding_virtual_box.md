---
title: "regarding virtual box"
date: 2009-12-29
forum: General Help
---

### Post by arj97 on 2009-12-29
[SIZE=5][COLOR=Green][B]hi  there!
i installed virtualbox on my lappie...also installed-tested various operating systems on it...is there a way to install drivers of an operating system on virtual box????? if no is there any other software??
help!!!!!!!!!
[/B][/COLOR][/SIZE]

---

### Post by MelDJ on 2009-12-29
what os are you using on virtualbox that you want the drivers for?

---

### Post by arj97 on 2009-12-29
[COLOR=Red][SIZE=5]**installed windows 7...........i have the drivers can i install them????????? **[/SIZE][/COLOR]

---

### Post by MelDJ on 2009-12-29
virtualbox does not use the native hardware in your computer. instead it uses virtual hardware. you can install virtual graphic accelaration and the mouse by devices-install guest additions

---

### Post by Cheesemill on 2009-12-29
No you cant.

The guest operating system can't 'see' any of your actual hardware, instead it sees the virtual hardware presented to it by VirtualBox.
Drivers for this virtual hardware can by installed by installing the VirtualBox Guest Additions into your guest OS, just go to Devices > Install guest additions in the VirtualBox menu.

---

### Post by arj97 on 2009-12-29
[color=blue][size=7]thanks!!!!!!![/size][/color]

---

