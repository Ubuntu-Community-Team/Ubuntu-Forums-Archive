---
title: "Window's in VM"
date: 2010-06-08
forum: General Help
---

### Post by jimmers on 2010-06-08
Hi All,
I need to use Window's once or twice a month tops, as I did'nt want to dual boot, so installed XP in a virtual machine (Obtained via Synaptic)

Problem is Windows will recognise my CD/DVD Drive, but not my USB drives, it shows Floppy Drive even though my laptop does not have a floppy drive, I have installed Guest Additions.

What I need guy's is an idiots guide to installing and running XP in a Virtual machine.

As always all help, ideas, suggestions greatly appreciated.

---

### Post by howefield on 2010-06-09
> **jimmers said:**
> Problem is Windows will recognise my CD/DVD Drive, but not my USB drives, it shows Floppy Drive even though my laptop does not have a floppy drive,

There are some good video tutorials on the virtualbox.org website, have a look.

First question would be, have you installed the package from the repository (OSE) or the one from the virtualbox website (PUEL). Reason being that the OSE version doesn't support USB devices.

If you have used the PUEL package, which does support USB devices, have you added the user to the vboxusers group and created a filter for the USB device ?

Work you way through the VM settings to remove the floppy controller if you don't have a floppy disk drive.

---

### Post by pizza-is-good on 2010-06-09
I used virtualbox a lot a while back, but I haven't in a while. If I remember correctly, the window where the OS is open has the traditional File Edit etc.. at the top. On one of them, I think devices, you could go around the devices available to your host machine and 'mount' them to your virtual machine.

---

### Post by dcstar on 2010-06-10
> **jimmers said:**
> Hi All,
I need to use Window's once or twice a month tops, as I did'nt want to dual boot, so installed XP in a virtual machine (Obtained via Synaptic)

Problem is Windows will recognise my CD/DVD Drive, but not my USB drives, it shows Floppy Drive even though my laptop does not have a floppy drive, I have installed Guest Additions.

What I need guy's is an idiots guide to installing and running XP in a Virtual machine.

As always all help, ideas, suggestions greatly appreciated.

VM issues like this are already covered in the Virtualization forum.

---

