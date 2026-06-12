---
title: "Keyboard and mouse stop working after sleep"
date: 2011-03-15
forum: General Help
---

### Post by LetsMugSanta on 2011-03-15
Yeah so whenever I try to hibernate/sleep my computer and I come out of the sleep, the keyboard is not recognized and stops working altogether and requires a reboot. Changing the USB port does nothing either.

Any ideas?

---

### Post by LowSky on 2011-03-15
Found this [http://ubuntuforums.org/showpost.php?p=9171282&postcount=11](http://ubuntuforums.org/showpost.php?p=9171282&postcount=11)

follow these steps

open a terminal and type

```
gksu gedit /etc/default/grub
```

now look for

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

addd this after splash

```
atkbd.reset
```

it will look like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"
```
then save the file

go back to the terminal and type

```
sudo update-grub
```

try suspending to see if it works

---

### Post by LetsMugSanta on 2011-03-15
Yeah no go. After customizing the login screen from one of my earlier threads the network for some reason will disable itself upon reboot. No big deal but I have to re-enable it every time. Also I now get no background on my login screen. And when returning from sleep mode I got random gray boxes, (about 2 or 3), and the rest of the screen was black and I had to reboot.

---

### Post by Krytarik on 2011-03-15
> **LetsMugSanta said:**
> Yeah no go. After customizing the login screen from one of my earlier threads the network for some reason will disable itself upon reboot. No big deal but I have to re-enable it every time. Also I now get no background on my login screen. And when returning from sleep mode I got random gray boxes, (about 2 or 3), and the rest of the screen was black and I had to reboot.
Do those issue occur when you try the previously stated suggestion or even without it?

Do you have the package "hibernate" installed!?

---

### Post by LetsMugSanta on 2011-03-16
The network issue happens randomly and I guess it just stopped doing it. The purple background for the login screen happened when I just did the above. 

You have to have a package installed to have the computer hibernate? Are you serious?

---

### Post by Krytarik on 2011-03-16
> **LetsMugSanta said:**
> 
You have to have a package installed to have the computer hibernate? Are you serious?
Yeah, I'm sure. Strangely it is not installed by default.

---

