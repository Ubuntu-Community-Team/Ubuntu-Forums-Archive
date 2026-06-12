---
title: "boot failure maverick"
date: 2010-11-07
forum: General Help
---

### Post by cthom on 2010-11-07
selecting either generic or recovery leads to a string of [2.xxxxxx] messages including [2.5492403] CODE: then a string of numbers.

varius MOUNTs fail ( /dev, /sys, /proc)

message No init found. Try passing init=bootarg

it then finishes with a (initramfs) prompt


this only happened yesterday after days of problem free use. help? :(

---

### Post by cthom on 2010-11-07
*bump*

---

### Post by dino99 on 2010-11-07
what kind of installation are you using ? which distro (32/64/pae) ?

---

### Post by drs305 on 2010-11-07
If it's a failure of the boot files that is not allowing the system to fully load we can probably figure it out if you run the boot info script from the following link. It will generate a file called RESULTS.txt. Post the contents of that file here.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by cthom on 2010-11-07
i guessed i might have to use that bootinfoscript. but how do i run it from the prompt? i copied it to a usb card (on my mobile dongle). and atm it's the only extra device on my laptop.

---

### Post by drs305 on 2010-11-07
> **cthom said:**
> i guessed i might have to use that bootinfoscript. but how do i run it from the prompt? i copied it to a usb card (on my mobile dongle). and atm it's the only extra device on my laptop.

Change to the directory/folder in which the script is located (probably either Desktop or Downloads). Run it as:
```

cd ~/Desktop  # or cd ~/Downloads
sudo bash ./boot_info_script055.sh
gedit RESULTS.txt
```

---

### Post by cthom on 2010-11-07
i entered cd ~/Desktop, got this: 

cd can't cd to //Desktop

---

