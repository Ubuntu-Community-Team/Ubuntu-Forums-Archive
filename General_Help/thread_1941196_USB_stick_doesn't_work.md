---
title: "USB stick doesn't work"
date: 2012-03-15
forum: General Help
---

### Post by bero1616 on 2012-03-15
Hy. I made a ubuntu liveusb, managed to install the os but now the stick is not working. The pc doesn't recognise the usb. What happend, can i repair it?

---

### Post by ajgreeny on 2012-03-15
What do you mean by "the stick is not working"?

Not working for what purpose, and what are you trying to do with it?

If you don't need it as a live USB any more you can just re-format it, by installing gparted to your installed system and using that.  Just make sure you point to the correct partition/disk when you format and don't delete anything else.

---

### Post by bero1616 on 2012-03-15
I want to format it
ubuntu and win don't recognize like it's not plugged in ( lspci doesn't list it)
now it wont even boot
I think it's not broken because i've mate two live usb's and both don't work any more

---

### Post by ajgreeny on 2012-03-15
> **bero1616 said:**
> I want to format it
ubuntu and win don't recognize like it's not plugged in ( lspci doesn't list it)
now it wont even boot
I think it's not broken because i've mate two live usb's and both don't work any more
**lspci** will not list a USB device; for that you need **lsusb**.  Is it seen in **gparted** or if you run ```
sudo fdisk -l
```

It looks as if a re-format might be needed, but before you do that can you check it on another machine, just in case it is your computer hardware (usb port/socket) that is at fault in some manner.

---

### Post by bero1616 on 2012-03-15
Thanks for your replays. I've meant lsusb.
I've tried fdisk and gparted, non of them recognizes my usb, both of my machines don't recognize them

---

### Post by jerome1232 on 2012-03-15
Either the usb port your plugging it into is busted, or the stick is busted (and by busted I mean physically broken)

Try plugging it into a usb port in the back of the computer

---

