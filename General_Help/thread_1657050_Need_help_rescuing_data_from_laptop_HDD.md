---
title: "Need help rescuing data from laptop HDD"
date: 2010-12-31
forum: General Help
---

### Post by fedu on 2010-12-31
My girlfriend's laptop fried the other day and I'm trying to put her hard drive into my functioning laptop to save her pictures. I downloaded the universal usb installer and am going to try and make a virtual drive from one of my flash drives. I need to know what a good iso would be for network support that is pre-loaded so I don't have to mess around with getting the usb set up before transferring the files. Is it even possible to pull data off of the drive this way?

Thanks for the help in advance... I hope someone out there has done this already.

---

### Post by ram2500 on 2010-12-31
I have had someone summon me for help when their Vista laptop became ridden with viruses to the point that it would not boot, and before reinstalling, I removed the drive from the laptop and temporarily installed it in my desktop machine. I accessed the drive and copied important files over to my hard drive before reinstalling Windows. Several people have said to never install a laptop (2.5") drive in a desktop (allegedly of the SATA  power being different between the platforms), but after research, it was OK to place a 2.5" drive in a desktop with no modifications. As far as I know, the laptop's hard drive has had no issues. This would be a simpler option, but you need a desktop (although some HP laptops, such as my Pavilion dv9000, have a dual-hard drive bay with one of them empty). 

Otherwise, an Ubuntu ISO should work, but this will be slow. Better to take out the HDD, copy the files to a desktop PC temporarily, and replace the files once your friend's machine is either repaired or replaced.

---

### Post by Habeouscorpus on 2010-12-31
Here's a good one: [http://www.sysresccd.org/](http://www.sysresccd.org/)

It's created for what you're about to do. (I think. If I understand you right, anyway.)

---

### Post by fedu on 2010-12-31
Unfortunately, I don't have sata on my desktop, so I can't transfer the pictures that way. I'm pretty sure her mobo is fried, so I need a way to transfer files (if I can access the data at all) using linux. I took my hard drive out of my laptop and put hers in, but it won't run because it isn't set up for my computer.
*I should mention that her laptop is/was running vista. At the POST test, there is no beep and nothing shows uo on her computer- hence me believing her mobo is toast.

---

### Post by dcstar on 2010-12-31
> **fedu said:**
> Unfortunately, **I don't have sata on my desktop**, so I can't transfer the pictures that way. I'm pretty sure her mobo is fried, so I need a way to transfer files (if I can access the data at all) using linux. I took my hard drive out of my laptop and put hers in, but it won't run because it isn't set up for my computer.
.........

Put the hard drive in an external SATA dock, that is what these things were invented for.

---

### Post by Schrute Farms on 2011-01-01
You can access the windows files you need if you do a live boot via USB/CD.  The Ubuntu live cd works fine.  You won't have to do anything to make the USB work.  Just go into places on the menu after it boots & mount the internal drive, and any other drive you choose.  Then copy what you need.  
I saved some files for my cousin, booting Ubuntu 10.04 with my flash drive.  I plugged her flash drive into the computer & copied her stuff right on to it no problem.

---

