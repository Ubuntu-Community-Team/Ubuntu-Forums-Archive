---
title: "&quot;Secret&quot; ubuntu."
date: 2011-11-15
forum: General Help
---

### Post by samvkampen on 2011-11-15
Ohai!

I've got a question (that is probably not entirely ubuntu related). If I install Ubuntu, can I make it so that it automatically starts Windows, but starts Ubuntu when you press a key? I'm familiar with the "Press any key to display the menu" thing, but i'd like to have it that you dont see that (or see a different message). Could that be possible? I'm just curious. My mom doesnt really approve any Linux because in the past I crashed the computer because of some stupid things (Oh, you're young, you like to try stuff :P), but without free, customizable software i'd go nuts (especially the customizable part ;), so thats why :'

Thanks in advance,

Sam van Kampen

---

### Post by Megaptera on 2011-11-15
You could dual boot with the default o/s being Windows with you needing to select Ubuntu instead at boot time. 

Or you could run Ubuntu within Windows using VMWarePlayer (or other virtualisation software). So you could have Windows running and then VM in to Ubuntu.

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Or run Ubuntu from a flash drive (pen drive) and set the PC to boot from USB when your Ubuntu pen drive is inserted at boot.

Hope these ideas are of help?

---

### Post by snowpine on 2011-11-15
Run Ubuntu from a USB pen drive or in a Virtual Machine. You get Ubuntu, your mom gets to keep her Windows, everybody is happy. :)

---

### Post by haqking on 2011-11-15
choose windows as default in grub, set grub timeout to 0 and press the shift key when you want to access the grub menu to choose Ubuntu

---

### Post by ofnuts on 2011-11-15
> **samvkampen said:**
> Ohai!

I've got a question (that is probably not entirely ubuntu related). If I install Ubuntu, can I make it so that it automatically starts Windows, but starts Ubuntu when you press a key? I'm familiar with the "Press any key to display the menu" thing, but i'd like to have it that you dont see that (or see a different message). Could that be possible? I'm just curious. My mom doesnt really approve any Linux because in the past I crashed the computer because of some stupid things (Oh, you're young, you like to try stuff :P), but without free, customizable software i'd go nuts (especially the customizable part ;), so thats why :'

Thanks in advance,

Sam van KampenIf you use dual boot, you can default to Windows. That's how my family PC works. 2 seconds to strike a cursor keys before it starts Windows is plenty of time.

if you don't even want the Linux to show up in a dual boot choice, I think you can have most of it on disk, but bootable only of the appropriate USB key is there at power up (likely faster than running it completely from the key).

---

