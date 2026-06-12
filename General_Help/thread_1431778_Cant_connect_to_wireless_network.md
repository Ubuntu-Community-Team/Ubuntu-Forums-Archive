---
title: "Cant connect to wireless network"
date: 2010-03-17
forum: General Help
---

### Post by killing kittens on 2010-03-17
Ok i hope someone can help me i have an hp laptop and im running hardy heron and dont know how to connect to my 2wire plz help

---

### Post by eNiNjA on 2010-03-17
sure...but what kind of card do you have?

open a shell and type lspci

then maybe we can help you

---

### Post by killing kittens on 2010-03-17
how do i open a shell?????

---

### Post by windfix on 2010-03-17
Have you tried:
Reboot while connected via ethernet cable (should initiate configuration of proprietary drivers)
and/or Look under System | Administration | Hardware Drivers

to make sure you've got a driver installed for the wireless card?  In my limited experience, the wireless cards have all required proprietary drivers.

---

### Post by windfix on 2010-03-17
For a shell (terminal), go to Applications, Accessories, Terminal

---

### Post by prodigy_ on 2010-03-17
Press Alt+F2. In a window that will appear, type ```
gnome-terminal
``` and press Enter. Another window will appear - a command-line shell. Type ```
lspci
``` in it and press Enter. Post output here. (Note that Ctrl+C works differently in shell window, so you need to use Ctrl+Insert to copy the selected text.)

---

### Post by eNiNjA on 2010-03-17
alt + f2 isnt good for a new user lol

it's under:

applications -> accessories -> terminal

paste the output of:

lspci

---

### Post by eNiNjA on 2010-03-17
> **windfix said:**
> 

to make sure you've got a driver installed for the wireless card?  In my limited experience, the wireless cards have all required proprietary drivers.

that's not always the case..hp has always had good linux support in my endeavors, and i always recommend them to my customers

---

### Post by 3rdalbum on 2010-03-17
If you don't have any wireless networks listed in the Network Manager applet on your top panel, then probably the first thing I'd do is try a newer version of Ubuntu. Hardy's driver support is ancient, in Linux-years.

New users should start with the latest Ubuntu, because you get the latest refinements and drivers, and the best community support and documentation.

---

### Post by eNiNjA on 2010-03-17
my first guess is that the wireless isn't even turned on.....

---

### Post by 3rdalbum on 2010-03-17
> **eNiNjA said:**
> my first guess is that the wireless isn't even turned on.....

That's a possibility as well. One that I didn't think of, because I never turn mine off.

---

### Post by ani84 on 2010-03-17
Since you are saying that you dont know how to connect to a wireless, i'm assuming you didn't try connecting. If you did, then what exactly happened when you tried to connect? If not then look in the top right of your desktop, you have a wireless network icon. click on it, select a network and try connecting to it. Hope this helps.

---

### Post by eNiNjA on 2010-03-17
> **3rdalbum said:**
> That's a possibility as well. One that I didn't think of, because I never turn mine off.

on my hp dv9300, the wireless turns off on a boot/reboot

---

