---
title: "Ubuntu 10.10 Doesn't Recognize Display"
date: 2010-10-04
forum: General Help
---

### Post by alligoodw on 2010-10-04
System Stats:

Acer Aspire 7741Z-5731
Intel Pentium Processor
Windows 7/64-bit OS
Intel HD Graphics
---------------------------------------

Experience:
Load OS from live CD ..... no problems
Install to HD ..... problems . . . OS boots into command line and not gnome.  The OS will boot into gnome using the LOW-GRAPHICS method.  

Question:  How do I correct this problem? How do I get Ubuntu to recognize the Intel HD Graphics board installed in this laptop?

---

### Post by dyous87 on 2010-10-04
Did you check if there are any restricted drivers for your graphics card?

Go to System>Administration>Hardware Drivers

David

---

### Post by luc.d on 2010-10-11
Hi,
I just fixed a similar problem on my Acer 5741.

While booting, the screen turned completely black (like it was unplugged from power). It was kind of frustrating, but I was lucky to resolve it with an update to BIOS (I had v1.02 and upgraded it to 1.13).

I took the files from the Acer website, than flashed the bios from an USB key, and, by surprise, it worked :) .

Anyway, hope this helps,

Luc

---

### Post by crh0831 on 2010-10-18
I just bought an Acer Aspire 7741Z-5731 today and am having the same problem.  The live CD works fine (well, no sound - but I figured I'd iron that out later)  After the install the reboot drops me at a command prompt.  I tried to restart gdm but the screen just went blank.  

Pressing the power button brought up the shutdown text and I saw something about "timed out waiting for intel_agp" before the machine powered off.

I'm in the process of installing 10.04 for now to see if I can solve the video problem.  Anyone have any other suggestions?

---

### Post by SciFiCheetos on 2010-11-08
Were you ever able to get Ubuntu working on this notebook.  I recently purchased the same model and am having this problem.

---

