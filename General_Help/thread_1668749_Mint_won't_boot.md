---
title: "Mint won't boot"
date: 2011-01-16
forum: General Help
---

### Post by pvtryan on 2011-01-16
Yes, I'm using Mint. It's practically the same as Ubuntu, but the Mint forums have much less people. Hear me out.

I'm dualbooting Win7 and Mint 10, each on their own disk. Mint will not boot. It was working fine a couple days ago, but now only Windows is working. 

When I tried to boot Mint recovery mode some of the last lines were:
> Gave up waiting for root device. Common problems: 
[here it listed four things]
-
-
-
-
ALERT! /dev/disk/[long, seemingly random stream of numbers and letters] does not exist. Dropping to a shell!

I think that it could be a GRUB (GRUB 2) problem because when I booted up this morning GRUB did not have the 5-second timeout it was supposed to have. Minor things like this have happened to me in the past — once, by itself, it changed the default boot to memtest, and I had to change it back with the StartUp-Manager.

I would try using the StartUp-Manager or running sudo grub-mkconfig with my live CD, except that my live CD will not boot. The drive seems to be fine, because I just tested it with The Fellowship of the Ring.

The only thing I have changed recently (to my knowledge) is my CMOS battery, yesterday. Windows is working fine, and it can see the drive that Mint is on (meaning the drive IS connected and does exist!).

Thanks for the help. :(

---

### Post by pvtryan on 2011-01-17
I was able to boot a live CD in compatibility mode just now. It gave me a command line. I ran "sudo fdisk -l" and it showed me that somehow my linux partition changed from sda1 to sdf1. I guess all I have to do is change GRUB.

I tried installing GRUB in the command line and running "sudo grub-mkconfig," but no dice.

How can I fix this via command line and why isn't the live CD working normally?

---

### Post by khamil8686 on 2011-01-17
maybe try running sudo update-grub2 (or sudo update-grub)? depending on what version of grub youre running, if your partition changed somehow, grub would want to be updated on where it is now and when i run sudo update-grub2 it searches my hard drive and finds all OS (whats the plural abbreviation of multiple operating systems? :P) installed and automatically updates the grub config file telling where the OS are on the hard drive, hopefully this helps :)

---

### Post by coffeecat on 2011-01-17
> **pvtryan said:**
> I ran "sudo fdisk -l" and it showed me that somehow my linux partition changed from sda1 to sdf1.

Which means that was what drive 1 is now drive 6 - which sounds like a BIOS issue.

> **pvtryan said:**
> The only thing I have changed recently (to my knowledge) is my CMOS battery, yesterday.

Which could very well have reset the BIOS. Before doing anything with grub you need to look at the device boot order in your BIOS.

---

### Post by pvtryan on 2011-01-17
The boot order in the BIOS is the first thing I changed after I replaced the disk.

It goes:

CD/DVD
SATA Drive with GRUB on it
USB

---

### Post by pvtryan on 2011-01-17
The boot order in the BIOS is the first thing I changed after I replaced the disk.

It goes:

CD/DVD
SATA Drive with GRUB on it
USB

---

### Post by coffeecat on 2011-01-17
Boot up with a live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script and post your RESULTS.txt file within code tags for legibility. From this we can see what is what and take it from there.

I'll be logging off soon, but someone should be able to help you. I'll pick this thread up in the morning anyway.

---

### Post by pvtryan on 2011-01-17
> **pvtryan said:**
> 
I would try using the StartUp-Manager or running sudo grub-mkconfig with my live CD, except that my live CD will not boot. The drive seems to be fine, because I just tested it with The Fellowship of the Ring.
[QUOTE=pvtryan]
I was able to boot a live CD in compatibility mode just now. It gave me a command line.
[/QUOTE]

Unless there is a command line browser built in to the live CD that I'm not aware of, I don't think that's going to happen.

Sorry about the double post, stupid browser froze.

---

### Post by pvtryan on 2011-01-19
I got both my live CD and my installation by adding 
```

irqpoll acpi=off noapic

```
to the kernel line.
 
Can someone please explain to me why I would need this now, when I did not need it before?
 
Also, I read somewhere that irqpoll takes a performance hit. Is there any way to fix this?
 
Thanks.

---

