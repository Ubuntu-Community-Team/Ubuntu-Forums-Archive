---
title: "How to access camera as root?"
date: 2010-12-02
forum: General Help
---

### Post by doomslang on 2010-12-02
I'm having some problems getting photos off of my camera that I am thinking I can work with if I can access the photos on the camera as superuser.  However I don't understand how Ubuntu (gnome) mounts cameras now, they don't show up as a mounted drive and I can't access (or find it at all) with 'sudo nautilus.'  This has been driving me crazy.  Thanks for any help.

[edit] Oh, also, the camera shows up if using nautilus not as a superuser.

---

### Post by doomslang on 2010-12-02
Also, for example..I can't use image recovery programs because the camera doesn't have a device name/mount point it has some sort of weird "gphoto2://[usb:004,002]/store_00010001/" that I, and apparently many programs, don't understand.  I logged in as root (I know, I know) and the camera showed up in Nautilus under 'Computer' and it actually worked and I was able to get a picture off of it.  But then when I tried to move more it quit working and won't work again even on restart and doing the exact same thing.  Ugh.

---

### Post by Jerubaal on 2010-12-06
I'm having a similar problem - it used to work ok, but I have since done updates and installed Picassa, so I have no idea which change has caused the problem. 
WHen I 'open' the Digital Camera icon on the desktop, it just shouw the comtents of my /mnt/MyPhotos partition and not the actual camera contents, even though it says it is located at gphoto2:[usb1,005]. 
Picassa says it is transferring and the camera led flashes every second, so perhaps it is doing something. Alas, I fear the battery will run out before Picassa finishes anything...

---

