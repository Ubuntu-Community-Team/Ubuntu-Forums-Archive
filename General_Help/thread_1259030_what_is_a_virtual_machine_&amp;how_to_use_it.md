---
title: "what is a virtual machine &amp;how to use it"
date: 2009-09-05
forum: General Help
---

### Post by hairchin67 on 2009-09-05
can someone tell me how and if i can put windows on ubuntu with a virtual machine? what r the requirements for this?

---

### Post by NoaHall on 2009-09-05
A virtual Machine is a way of running a operating system inside another. You will need a VM application(I recommend downloading VirtualBox 3.0 from the site) and either a .iso file or a CD. You will need enough RAM to run your Host and your Guest ( I would recommend about 3 GB for each) Although you could use around 500 MB for ubuntu and the rest for the Virtual machine

---

### Post by Ms_Angel_D on 2009-09-05
Here's a few links

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://klikit.pbworks.com/How-to-install-Windows-in-VirtualBox](http://klikit.pbworks.com/How-to-install-Windows-in-VirtualBox)


Hope they help.

---

### Post by hairchin67 on 2009-09-05
i have a dell with these specs do i have enough ram to use windows in this virtual machine. im only going to use it for a math lab college class

500.6 MiB for memory

intel(r) pentium(r) 4 cpu 2.40 ghz

---

### Post by NoaHall on 2009-09-05
I would say no - you wouldn't be able to happily run a virtual machine. Try getting your memory up to at least 1GB

---

### Post by JKyleOKC on 2009-09-05
> **hairchin67 said:**
> i have a dell with these specs do i have enough ram to use windows in this virtual machine. im only going to use it for a math lab college class

500.6 MiB for memoryI have VirtualBox installed on two Xubuntu systems, one running Hardy and one running Jaunty. The Hardy box has only 256 MiB in it, and the Jaunty one has 512 MiB. On the Hardy box I'm able to run Windows 2000, and on the Jaunty one WinXP. Neither is very fast, but both run well enough to let me use them -- and I've even done a small amount of software development on the Windows 2000 VM, since I didn't want to install Visual Basic anywhere else on my LAN.

They would run better with more RAM, but if all you need is to run a math program for a class you should be okay...

---

### Post by XCan on 2009-09-06
Math programs, limited ram, that sounds like a bad combination, unless you're just going to play around with tiny matrices. :p Which program worth a damn is there anyway that isn't multiplatform?

---

