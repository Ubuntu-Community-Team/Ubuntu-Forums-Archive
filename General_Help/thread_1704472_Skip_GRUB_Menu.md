---
title: "Skip GRUB Menu?"
date: 2011-03-10
forum: General Help
---

### Post by a.kleiner on 2011-03-10
On my laptop, I have a dual-boot setup between Ubuntu 10.10 and Windows 7. Is there a way to "hide" Windows (for lack of a better word) without removing it and skip straight to Ubuntu by default (instead of going to the GRUB screen)? If so:

[LIST]
[*]How would I set this up?
[*]Say I need to boot to Windows on occasion (which I will). What would I do differently on startup?
[/LIST]
Thanks in advance!

---

### Post by kyphi on 2011-03-10
Install Startup Manager.  You will find it in Synaptic or you can open a terminal and type in ```
sudo apt-get install startupmanager
```

Now you can shorten the boot display sequence (3 seconds is sufficient) and specify which system to boot into.  You will still be able to choose your operating system when you need to do so.

---

### Post by Krytarik on 2011-03-10
Add the option "GRUB_HIDDEN_TIMEOUT=0" to your "/etc/default/grub":
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20(file)]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")

And follow tweak #11, method 2 of this guide:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

**EDIT:** I just yet noticed, that the mentioned option is already present in the default "grub" config file.

---

### Post by Animal X on 2011-03-10
i use to just comment the thing out that i dont want showing

---

### Post by Krytarik on 2011-03-10
> **Animal X said:**
> i use to just comment the thing out that i dont want showing
1.) That doesn't hide the menu completely, like the OP would like to have.

2.) This gets reverted when "update-grub" is run the next time, wether because of a kernel upgrade or whatever else...

---

### Post by tg3793 on 2011-03-10
Just watch what part you set to "0". Many have gotten stuck with a problem getting back into GRUB later when they need to.

---

### Post by Krytarik on 2011-03-10
Ah, I forgot to say: After doing this you have to press SHIFT to make the boot menu show up if you need to.

---

### Post by garvinrick4 on 2011-03-10
###Use Krytarik's suggestion /etc/default/grub 
Change to # in menu entry line you want to boot.
Uncomment the graphical terminal:
```
gksudo gedit /etc/default/grub
```change and save:

```
sudo update-grub
```Krytarik gave you link to instructions:

---

