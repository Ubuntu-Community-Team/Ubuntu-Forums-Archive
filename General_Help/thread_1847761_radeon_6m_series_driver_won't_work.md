---
title: "radeon 6***m series driver won't work"
date: 2011-09-21
forum: General Help
---

### Post by scalydragon on 2011-09-21
hi i'm new to ubuntu and this forum, i have a radeon 6***m series graphics card (i think its 6660m or 6880m) and i've tried the default recommended ati driver which doesn't enable any 3d graphics, and i've tried to install the ati 11-8-x84-x84. which never seems to be able to install.  my question is is there a way for me to get the 3d graphics like in compiz or is there no support for my graphics card

---

### Post by pme 72 on 2011-09-21
What version of Ubuntu did you load?

---

### Post by scalydragon on 2011-09-21
it was 11.04

---

### Post by scalydragon on 2011-09-21
it is 11.04, when i first installed it it was unity, but after installing it went back to classic and it said that i don't have the hardware to run unity, but my 6***m graphics card is one of the newest.  and after installing the recommended driver i installed compiz config but none of the changes i made were applied.

---

### Post by pme 72 on 2011-09-21
Welcome to the Ubuntu forums. I only have experience loading the ATI driver from the AMD website for a windows machine. The default Radeon driver works for me with 10.04 so I can offer you no advice that is backed by experience on loading their fglrx driver. You might want to take my advice with a grain of salt and wait for a response from someone more knowledgeable. 

You could also post a question with Ask Ubuntu:

[http://askubuntu.com/questions/ask](http://askubuntu.com/questions/ask)

Did you uninstall the one from AMD and try the one from System>Administration>Additional Drivers? 

You said that the driver from the AMD site did not load properly. Did you follow the directions from the Natty Installation Guide for manually installing the drivers?

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by scalydragon on 2011-09-22
do you also have the 6***m series card?  
i have tried to unistall the one from from system>administration>additional drivers but none of the processes seemed to work.  
would my graphics work if i tried Ubuntu 10.04?  or another linux system?

---

### Post by pme 72 on 2011-09-22
I still think your issue is that your card is so new that the available drivers may not fully support your card yet with linux.    

Look at Unsupported Adapters on this page:

[http://wiki.cchtml.com/index.php/Ubuntu#Installation](http://wiki.cchtml.com/index.php/Ubuntu#Installation)

To find the name of your video adapter run this code in a terminal:

```
lshw -c display
```

I ran into a similar issue when I got a new Radeon HD 4550 several years ago.

---

### Post by scalydragon on 2011-10-02
okay, so i finally got the right propitiary driver installed from the amd website, i installed the 11.08.84x84 one, but still there doesnt seem to be any 3d, and when i use compiz config nothing happens when i check the different effects.

---

### Post by Dangertux on 2011-10-02
I have this chipset and am using the same driver.  Do you have radeon.modeset=1 in your kernel line in grub. That is what I had to do to enable compositing. 

Hope this helps

---

### Post by scalydragon on 2011-10-02
how do i get radeon.modeset=1 in my kernel line?

---

### Post by Dangertux on 2011-10-02
Ok be careful with this because if you do it wrong, you can severely hose your boot loader, and have to reinstall grub from a livecd, in fact before you do this make sure you have your LiveCD handy.

Once you do, do the following

```

sudo nano /boot/grub/grub.cfg

```Look for the line that looks something like this (it might be a little different)

```
 
linux   /boot/vmlinuz-2.6.38 root=UUID=3ea56657-ac63-41a2-8c3b-31b1ec12f3a4 ro   quiet splash

```change it to look like this

```

linux   /boot/vmlinuz-2.6.38-8-genericroot=UUID=3ea56657-ac63-41a2-8c3b-31b1ec12f3a4 ro   quiet splash radeon.modeset=1

```press ctrl+o to save your file then ctrl+x to exit. Reboot.

**IMPORTANT :** DO NOT COPY AND PASTE THIS, CHANGE ONLY THE radeon.modeset=1 if you copy paste, it will break your bootloader.

---

