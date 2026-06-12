---
title: "deleted ubuntu partition, how to reinstall without losing information."
date: 2011-01-16
forum: General Help
---

### Post by timmins on 2011-01-16
hey, I really shouldn't be so intrepid when it comes to messing with my operating system.

My gateway netbook was dual booted with windows 7 and ubuntu netwbook.

anywho, I was attempting free up some space on my netbook and decided that the ubuntu partition was expendable. 

I deleted it and sufficient to say I now can't boot boot up, I just get an error message, can't remember exactly what it is.

I am getting a new computer and would kind of like to be able to recover the files on the computer.

I have a USB netbook boot drive and am wondering how I would be able to install ubuntu without loosing the files.

I have the usb key plugged in am now at the partition stage of the installation, does anyone have any recommendations?

Thanks

---

### Post by grahammechanical on 2011-01-16
Windows boots from something called a Master Boot Record which is located in the very first part of the hard disc. A Linux installation will disconnect the MBR and put in a boot loader  such as GRUB. By deleting the Ubuntu partition you have removed the boot reference to the Windows installation. You need to restore the MBR there is a simple command that will do it.

Google for MBR and check out the Wikipedia entry for Master Boot Record. Look for the entry Editing/replacing MBR contents. See if you can work out what to do for your Windows installation.

Regards.

---

### Post by timmins on 2011-01-16
hey, I went to wiki and tried many of the commands none had any effect. the exact error is 

error: unknown filesystem.
grub rescue>

I typed in commands like bootrec /Fix mbr , fixmbr , mbr etc. any recommendations?

Thanks

---

### Post by timmins on 2011-01-16
I found a couple of comparable situations, but none where the partition had been deleted, I don't really care whether I get to the files through ubuntu or windows. 

Is there anything I can do using the live usb?

---

### Post by maizuddin35 on 2011-01-16
I don't quite get it . Do you have a ubuntu live usb? if you have that , you can get access to that live usb , and get your files back to another usb or external hard disk or any free disk.

---

### Post by timmins on 2011-01-16
yeah, I'll try it, I'm sure it'll work

---

### Post by timmins on 2011-01-16
hey guys, I just re-installed ubuntu, it worked. thanks

---

### Post by maizuddin35 on 2011-01-16
Nice :D. Have you recover your files?

---

### Post by Primefalcon on 2011-01-16
if you want to recover a deleted partition look into a program called testdisk, saved my behind once

---

### Post by maizuddin35 on 2011-01-16
@Primefalcon, what do you meant by "saved my behind once"? :D

---

