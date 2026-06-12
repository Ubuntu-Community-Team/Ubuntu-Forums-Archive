---
title: "Wiping out and starting over"
date: 2009-09-11
forum: General Help
---

### Post by Nate Shoffner on 2009-09-11
I currently have Ubuntu Jaunty installed and in an attempt to upgrade the kernel to the latest version, it messed up my machine.  Whenever a new program is installed, it comes up with an error about the kernel.  With Ubuntu 9.10 getting ready to come out, I am wondering, is it just better for me to back up all of my data, wipe out the Ubuntu partition and restart with 9.10 using the LiveCD (when it becomes available).  Thank you.

---

### Post by P4man on 2009-09-11
You should be able to roll back to the previous kernel by selecting it in the grub menu. Sure is easier than a reinstall :)

As for 9.10, you can already download the alpha5 if you're curious. Its hardly complete or bug free, but if you don't mind experimenting, its certainly usable:

[http://cdimage.ubuntu.com/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/releases/karmic/alpha-5/)

---

### Post by nothingspecial on 2009-09-11
```
sudo nano /boot/grub/menu.lst
```

Put a # infront of the lines refering to the kernel that doesn`t work and grub will ignore it when you restart.

---

### Post by Nate Shoffner on 2009-09-11
If I make GRUB ignore it, will it cause any problems while updating to 9.10?  Speaking of, is it easy to upgrade using the LiveCD?  Do I just have to put it in and it has the ability to update my 9.04 to 9.10 without any problems (I would back up my data of course)?

---

### Post by P4man on 2009-09-11
> **Nate Shoffner said:**
> If I make GRUB ignore it, will it cause any problems while updating to 9.10?

None whatssoever.

>   Speaking of, is it easy to upgrade using the LiveCD?  Do I just have to put it in and it has the ability to update my 9.04 to 9.10 without any problems (I would back up my data of course)?

No, you cant upgrade from a live cd. You can upgrade by running a command from within jaunty (id have to look it up) but I dont recommend that. Its better to do a clean install, especially when dealing with alpha versions (and even for released versions its usually better to reinstall rather than upgrade).

---

### Post by Nate Shoffner on 2009-09-11
So I would, in the end, be better off wiping out my partition and doing a fresh install of 9.10 when it is replaced?  If that is the case I will back up all of my important data, make a list of my currently installed programs and go from there.  I have broken this system several times so I would feel better doing a fresh install that way if I have any problems, I can be sure that my screw ups weren't at fault. :P.  I used to know the command to list all of the currently installed programs, anybody happen to know it?  Thank you.

---

### Post by P4man on 2009-09-11
Someone asked the same question not 10 minutes ago :)
[http://ubuntuforums.org/showthread.php?t=1263500](http://ubuntuforums.org/showthread.php?t=1263500)

Im not 100% sure if its a good plan to do that across different releases, but I guess it should work.

---

### Post by nothingspecial on 2009-09-11
Personally, I use a seperate /home partition.

That way all your data and settings are preserved, but Ubuntu itself is brand shiny new.

See [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") for details.

---

