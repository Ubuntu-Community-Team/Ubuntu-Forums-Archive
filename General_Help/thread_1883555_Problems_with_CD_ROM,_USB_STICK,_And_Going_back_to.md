---
title: "Problems with CD ROM, USB STICK, And Going back to 10.04"
date: 2011-11-19
forum: General Help
---

### Post by esg10 on 2011-11-19
Hi I'm currently using 11.10 Oneiric Ocelot. Ever since I upgraded I been having problems with the cd-rom. For some reason every time I inserted a cd it would not do anything. So I went on the internet brought up terminal and all I can remember is changing the cd-rom 'Natty Narwhal' to 'Oneiric Ocelot'.  So for example if we were to go to [System Settings] then [Software Sources] [Ubuntu Software] it would say "CDrom with Ubuntu 10.04 'Natty Narwhal'" and on [Other Software] it would be checked and it would say "Cdrom with Ubuntu 10.04 'Natty Narwhal'". ....  

Ever since I changed Natty Narwhal 10.04 to Oneiric Ocelot 11.10 I have been getting BOOT Problems. Every time I re-start my computer i get "error mounting mount/dev/sda1" press s to continue or m to edit.

I don't know what I did, I'm a complete noob. All I know is how to upgrade and update from terminal $sudo. 

I believe that I upgraded to 11.10 with errors. So yesterday I downloaded 10.04 on a USB stick and re-started my computer to re install 10.04 but it just gives me the "error mounting mount/dev/sda1". I have tried so many things like the boot menu switching it to USB hardrive and all the other ones and enabling... but I still get the same error. Please help. Ty.

---

### Post by WasMeHere on 2011-11-19
Hi esg10,

Please describe your computer including cpu, graphics card, CD/DVD drive (or not), what partitions you have on your hard drive.

And how did you create your USB boot stick? The more we know, the better we can help

Have fun instead of frustration :-)
Olle

---

### Post by esg10 on 2011-11-19
I have a HP pavillion dv6000 it came with windows vista 32 bit + N Vidia Graphics + CD ROM/DVD ROM/ all in one drive. I'm currently on UBUNTU 11.10 and I have multiple desktops from LUbuntu. 

I created the USB stick following the steps in [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)  on the "show me how" for USB STICK...

I first downloaded Ubuntu 10.04 then I used start up Disk Creator and transferred it to my USB Stick.

---

### Post by WasMeHere on 2011-11-19
Since you have a CD/DVD drive I suggest that you make a boot CD from your Ubuntu iso file. Try the same link for instructions, but follow the path for CD instead.

Good luck

---

### Post by esg10 on 2011-11-19
I can't, ... its why I made the USB STICK.

When I put in the blank cd it shows up asking what to do. So I select disk image to write but there is no disk to write to and asks to please replace the disk with a supported cd or dvd.

---

### Post by WasMeHere on 2011-11-19
I'll try to give you some ideas:

Have you ever booted from a USB stick before?
In this computer?

Could you borrow a computer to make a boot CD? I know, it's easy for me to suggest :-/

Try to use Unetbootin instead to make a boot USB stick! Sometimes it works better with your hardware.

---

