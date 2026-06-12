---
title: "turn current Windows partition into image for a VM in Ubuntu?"
date: 2010-05-27
forum: General Help
---

### Post by derande on 2010-05-27
I have a dual boot machine (Win XP and Lucid).

I only need to boot into Win XP on the rare occasion when I need to access one program that I cannot run in Wine and do not have the .exe to install it my current Windows VM in Virtualbox.

Is it possible to save my current Win XP partition as an image, then install that image as a virtual machine in Virtualbox running in Lucid? And if possible, would this allow me to run previously installed programs in the Win XP VM?

I've used Clonezilla some. Would it be able to clone the Win XP partition into and ISO to run as a VM?

Thanks!

---

### Post by labinnsw on 2010-05-29
I had a similar problem when I decided to port my Qemu Image to Virtualbox. The tutorials did not work. The virtualbox image created did not work. In the end, I backed up Windows using the Windows back up tool. I then installed Windows on Virtual box and restored the back up using Windows system restore.

The result was exactly what I had before (Programs, settings, and files) except that now it is on virtual box.

---

### Post by dcstar on 2010-05-30
> **derande said:**
> 
.........
Is it possible to save my current Win XP partition as an image, then install that image as a virtual machine in Virtualbox running in Lucid? And if possible, would this allow me to run previously installed programs in the Win XP VM?


This issue is covered in the Virtualzation forum.

VMware have a free tool for converting existing Windows systems to VMs.

---

