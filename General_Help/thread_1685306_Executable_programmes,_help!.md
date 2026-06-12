---
title: "Executable programmes, help!"
date: 2011-02-10
forum: General Help
---

### Post by jordanC on 2011-02-10
hi, i have installed ubuntu desktop edition onto my laptop and want to reinstall windows 7 from a USB. The usb had the windows setup as an .exe file. I try to make the programme executable (right click, properties, permissions, allow programme to be executable) but when i try to tick the box, it just flashes with a tick for a quick second and it wont stayed ticked. i have wine installed, any ideas?

---

### Post by 3Miro on 2011-02-10
If the windows 7 executable is a .exe then it is probably intended as an upgrade from windows XP (or Vista). You will not be able to run it from within Ubuntu. You have to find a UBS/DVD that lets you boot from it and then install Windows. 

You might also want to read about reinstalling the Grub boot-loader. Windows will not let you boot into Ubuntu. so unless you want to remove Ubuntu, you will have to "restore" the ability to boot into it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by lukeiamyourfather on 2011-02-10
Generally speaking you can't run *.exe files in Linux. Wine can run some but not a Windows installer. You'll have to boot from the installer rather than run it through Ubuntu.

---

### Post by jordanC on 2011-02-10
it wouldnt show up in the grub and i tried using unetbootin to set it up, said i need to make it fat32, can anyone tell me how to do this? also will i be able to run an .exe file as a boot from usb?

---

### Post by 3Miro on 2011-02-10
> **jordanC said:**
> it wouldnt show up in the grub and i tried using unetbootin to set it up, said i need to make it fat32, can anyone tell me how to do this? also will i be able to run an .exe file as a boot from usb?

Your USB drive will not show in Grub. You have to check with your BIOS for a bootup screen, usually it is F12 (hit that while rebooting before you see the Grub menu).

You can install Gparted from the Software Center that will let you format your USB into fat32 (old DOS and windows), NTFS (windows), ext3 (older Linux), ext4 (Linux) or many other.

---

### Post by jordanC on 2011-02-10
ive got the usb at the top of the list on my BIOS, just having trouble formatting the USB, cant seem to find that programme on the sofwarre centre either

---

### Post by 3Miro on 2011-02-10
The program is called Gnome Partition Editor, in short gparted. Check the screenshot.

---

### Post by jordanC on 2011-02-10
ok thanks, any ideas if i still cant boot using my usb?

---

### Post by 3Miro on 2011-02-10
> **jordanC said:**
> ok thanks, any ideas if i still cant boot using my usb?

You have to make the USB boot-able, which takes more than just copy/paste an .exe file over it. You have to check on a windows forum/manual on how make a bootable windows USB, I only know the program that does that under Ubuntu (for Ubuntu boostable USB).

---

### Post by jordanC on 2011-02-10
ok ive made the usb bootable and ive got the windows7 disc image onto my usb, whats the next step to boot it from the usb?

---

### Post by Mark Phelps on 2011-02-11
You have to go into your BIOS settings and configure them to boot from the USB first.  If your BIOS does not support booting from USB, then you won't be able to do this.

---

### Post by jordanC on 2011-02-12
yeah i did that first....

---

