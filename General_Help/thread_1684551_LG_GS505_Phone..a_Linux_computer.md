---
title: "LG GS505 Phone..a Linux computer?"
date: 2011-02-09
forum: General Help
---

### Post by 4042966262 on 2011-02-09
I have a LG GS505 
[http://www.phonescoop.com/phones/phone.php?p=2546](http://www.phonescoop.com/phones/phone.php?p=2546)
and i love it to pieces.. but its not Linux.
would there be any way to somehow make it a teensy tiny computer??
is thia even possible?

---

### Post by 4042966262 on 2011-02-09
i found something called ubuntu mobile... hows this work? i should mention i have a 1GB card in phone ill delete EVRYTHINNG on it if i can get ubuntu on my phone!!

---

### Post by Joe of loath on 2011-02-09
No way in hell you'll get Ubuntu on it :lol:

At a push you might manage android, but only if someone else has done it already, or you know a lot about assembler + C programming.

---

### Post by 4042966262 on 2011-02-09
i downloaded (and have sitting on phone as is not as a iso or mounted or anything Moblin-2.1-fin)
how would i work this?

---

### Post by 4042966262 on 2011-02-09
if i can get Linux to store on a Card (i have a 1gig SD card in phone)
and i can get the phone to boot from card. this could possibly work.

---

### Post by iponeverything on 2011-02-09
> **4042966262 said:**
> if i can get Linux to store on a Card (i have a 1gig SD card in phone)
and i can get the phone to boot from card. this could possibly work.

you seem to be under the impression that there is some kind of hidden low level compatibility feature built into mobile processors that has not been discovered yet.. I have nice stash of hydrogen-3 on the moon that I'll let you have for a song.

---

### Post by 4042966262 on 2011-02-09
ok. point taken. you think im loony/ and i agree i very well could be. 
i did find this link though.. 
[http://forums.techarena.in/hardware-peripherals/1039093.htm](http://forums.techarena.in/hardware-peripherals/1039093.htm)
this is someone who got Windows XP Operating System on SD card
it includes downloads for USB boot
[http://www.usboot.org/tiki-index.php?page=Download](http://www.usboot.org/tiki-index.php?page=Download)
last but not least 
[http://forums.techarena.in/operating-systems/1239218.htm](http://forums.techarena.in/operating-systems/1239218.htm)
i know it can boot from a 1 gig flash drive. i have done that, wouldnt it be possible to make the phone boot from a SD?
as for your moon gas. what song would you like?):P

---

### Post by dino99 on 2011-02-09
dont stop working i'm waiting for the solution :)

---

### Post by 4042966262 on 2011-02-09
worst case?
ill buy this type of phone!
[http://www.youtube.com/watch?v=vMwlchuqsXo](http://www.youtube.com/watch?v=vMwlchuqsXo)

---

### Post by 4042966262 on 2011-02-09
the search goes on...
[www.linuxfordevices.com/c/a/News/Ubuntu-MID-Edition-ships/](www.linuxfordevices.com/c/a/News/Ubuntu-MID-Edition-ships/)

---

### Post by iponeverything on 2011-02-09
my samsung I5503 was cheap and came with andriod 2.1.

I was able put 2.2 on it both samsung and custom rom -- it is small linux box. It has sshd and busybox installed - so that I ssh into it. Pretty cool.

not to mention 2.2 itself is very cool - usb and wifi tethering and it takes voice command pretty well.

fun little phone.

---

### Post by 4042966262 on 2011-02-09
WOW...thank you iponeverything!! you have given me hope!
atm i am mounting the .img on my SD
oh it just finished!
now how the heck do i boot from it?

---

### Post by 4042966262 on 2011-02-09
on my phone i now see in other files
LDLinux.sys
bootfs.img
install.cfg
install.sh
rootfs.img
moot.msg
syslinux.cfg
vmlinuz
intrid0.img
whats going on??
i have about 15 files with same name..then next in list and so on

---

### Post by iponeverything on 2011-02-09
you are missing the point. 

If you want you want that hardware boot a linux kernel -- the linux kernel has to be ported and compiled for that hardware. 

Every processor is different. 

> 
Ubuntu MID Edition is also a modified version of the new Ubuntu Desktop Edition 8.04, optimized for handheld MID devices. The initial developer release is available for both Intel Centrino Atom ("Menlow") and Intel's A100/110 ("McCaslin") platform (targeting the Samsung Q1U ultra-mobile PC). Additionally, a handy KVM image and launcher shell script let users easily try out the stack on desktop PCs running Linux. It runs fairly quickly on systems with hardware virtualization support and Linux's the KVM (kernel virtual machine) loadable kernel module. 


unless your phone runs Intel Centrino Atom or Intel's A100/110 (which it does not) -- you are out of luck.

---

### Post by 4042966262 on 2011-02-10
> **iponeverything said:**
> If you want you want that hardware boot a linux kernel -- the linux kernel has to be ported and compiled for that hardware..

how would it be compiled/ported?

---

### Post by Joe of loath on 2011-02-10
You will need the source code for all your programs, and a toolchain written for that hardware.

---

### Post by 4042966262 on 2011-02-10
Source code.. i should be able to get that from Ubuntu source. where though?
and a toolchain.. what is that? 
im looking into what the phone has for processors and such.

---

### Post by Joe of loath on 2011-02-10
Source code is the easy part.

If you don't know what a toolchain is, you're not likely to be able to get Linux on your phone. Find someone who's an expert in embedded systems, see if they'll help you.

---

### Post by 4042966262 on 2011-02-10
i would love to do that..where and how?

---

### Post by Joe of loath on 2011-02-11
...

Find someone and ask them?

---

