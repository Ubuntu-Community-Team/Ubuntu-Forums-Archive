---
title: "how tun run ubuntu live from usb"
date: 2011-06-17
forum: General Help
---

### Post by NoBody0420 on 2011-06-17
i have just started learning linux and i have a live dvd
but i want to run it from my usb because the dvd is pretty much scratched and sometimes i am not able to run it
and there are also some linux drivers and other stuff in my ubuntu live dvd

so i was wondering if there is any way i can run linux from my usb
i copied the file from my dvd to my usb but it didnt work

help plz

---

### Post by PenguinMan2907 on 2011-06-17
You want to boot from usb by changing the bios boot order to the following:

1.USB
2.CD-ROM
3.Hard Disk

Each computer's bios is very different so ask online for help if needed.

---

### Post by nzjethro on 2011-06-17
Use [ this programme (unetbootin)]("http://unetbootin.sourceforge.net/") to create your Live USB. If you just copy the files to your USB stick, the BIOS can't boot from it. Once you have created a Live USB, it doesn't boot, do as PenguinMan said, and change your boot order, or else each time you boot go to your BIOS menu and select USB as your boot media.

EDIT: to change your boot order, press F1, F2, F12, or esc when you start up your computer (it will likely say something along the lines of "For startup menu pres <><>"). In the start-up menu there should be a tab for changing your boot order, and it will give you full instructions from there.

---

### Post by wildmanne39 on 2011-06-17
> **NoBody0420 said:**
> i have just started learning linux and i have a live dvd
but i want to run it from my usb because the dvd is pretty much scratched and sometimes i am not able to run it
and there are also some linux drivers and other stuff in my ubuntu live dvd

so i was wondering if there is any way i can run linux from my usb
i copied the file from my dvd to my usb but it didnt work

help plz
Hi, you can just use start up disk creator, I think it is already installed in natty, if not you can install it and it is easy to use, but I think you have to make it persistent so it will save your installs when you reboot.

---

### Post by NoBody0420 on 2011-06-18
i downloaded unetbootin and have copied all the files from my live ubuntu dvd to my usb
but when i boot it from my usb i get the unetbootin screen that doesn't boot ubuntu
it says press to tab and when i do that i get kind of a prompt
am i supposed to enter a command in order to run it

---

### Post by wildmanne39 on 2011-06-18
> **NoBody0420 said:**
> i downloaded unetbootin and have copied all the files from my live ubuntu dvd to my usb
but when i boot it from my usb i get the unetbootin screen that doesn't boot ubuntu
it says press to tab and when i do that i get kind of a prompt
am i supposed to enter a command in order to run itHi look at post #4 and you can use ubuntu's own startup disk creator. It is very simple.

---

