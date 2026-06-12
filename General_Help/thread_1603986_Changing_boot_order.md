---
title: "Changing boot order"
date: 2010-10-23
forum: General Help
---

### Post by MudOilnGears on 2010-10-23
Hello, newbie here in the Linux world. 
Just installed Ubuntu 10.4 on a computer that normally runs XP Pro. I used a separate drive and unplugged the windows drive while installing Ubuntu (error number one right?). Ubuntu installed perfectly, plugged in windows drive, Windows boots perfectly. My only problem is that I don't have the boot list option unless I go into the BIOS and change default boot drive every time I want to switch OS.
   After a bit of research I configured GRUB to allow me to dual boot (Windows did not appear at first), but it boots directly into Ubuntu (fine for me, but my mother uses XP for work) instead of Windows. Unfortunately I have some sort of keyboard issue that makes the arrow keys inoperable until the machine has once booted into an OS. 
  I have found numerous sites that say to change the "default" value after using the command :  "sudo gedit /boot/grub/menu.lst"

but when I use that all I get is this:
title                Windows XP Professional
root                (hd1,0)
savedefault
makeactive
chainloader        +1
map (hd0) (hd1)
map (hd1) (hd0)

with the values changed to my drives of course.

What am I missing, or did I mess up something when I edited this list?

Thanks A million!

---

### Post by Quackers on 2010-10-23
Welcome to Ubuntu Forums.
Boot into Ubuntu and then in a terminal run
sudo update-grub
while the Windows drive is connected. It will ask for your password. As it runs it will configure grub.cfg Watch and see if Windows is picked up.

---

### Post by TeoBigusGeekus on 2010-10-23
```
/boot/grub/menu.lst
```
was the location for grub (legacy) that ubuntu used until a couple of releases ago.
It now uses grub2 - have a look at [this]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by bumanie on 2010-10-23
I am surprised you are getting any output from that code if you are using ubuntu 10.04. As TeoBigusGeekus says, ubuntu now uses grub2 and does not have a /boot/grub/menu.lst any longer. May be boot a live cd and go to terminal and post the output of > sudo fdisk -l so that we can see the partitions/drives on your computer. Also check the version of ubuntu with terminal code > lsb_release -a by booting the hard drive ubuntu installation.

---

### Post by MudOilnGears on 2010-10-23
OK, I'll try this as soon as I can, right now I'm not close to that computer.
Also, I think I forgot to complete my statements, so here's a little more.

Once I got Grub to appear with the boot options I was satisfied with that as it will boot fine, once the keys work...

All I need to change is the default boot order so that I can just power on and boot directly into Windows.

I will run "sudo update-grub" as soon as I get home and see how that goes...

---

### Post by Quackers on 2010-10-23
You can change the default boot system by using Startup Manager (available through Synaptic ) if I understand you corectly.

---

### Post by MudOilnGears on 2010-10-23
Yes, All I need to change is which OS boots automatically. Will try Startup Manager as soon as I get home...

---

### Post by MudOilnGears on 2010-10-23
Ok, installed Startup Manager, and was able to change order easily, I checked the GRUB version tho and it's 1.98 and I'm running Ubuntu 1.04

---

### Post by Quackers on 2010-10-23
Grub version 1.98 is grub2. I think grub1 (legacy) ended at version 0.97

---

