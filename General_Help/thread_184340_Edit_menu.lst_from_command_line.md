---
title: "Edit menu.lst from command line?"
date: 2006-05-29
forum: General Help
---

### Post by edwina on 2006-05-29
I have just done a clean install of Kubuntu RC1, having deleted my old Ubuntu Breezy install.

Everything is working fine (not that I've done much with it yet), but I don't seem to be able to get into my /boot/grub/menu.lst file from the terminal. If I stick in```
sudo kwrite menu.lst
``` or ```
sudo kate menu.lst
``` then I just get a few pages of blurb starting with ```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
```

I can edit the file through Konqueror, but it would be nice to know what's up with the terminal route. Any ideas?

I'm no Linux pro, so go easy on me!

---

### Post by Jucato on 2006-05-29
Have you tried using kdesu instead of sudo, as it's supposed to be the command to use when launching graphical apps with root privileges?

---

### Post by aysiu on 2006-05-29
Try ```
kdesu kate /boot/grub/menu.lst
``` or ```
kdesu kwrite /boot/grub/menu.lst
``` You might get "errors" in the terminal, but that's because you're launching a graphical application from the terminal. It should work fine.

If not, try ```
sudo nano /boot/grub/menu.lst
```

You can also just press Alt-F2 and type ```
kdesu konqueror
``` and go from there to /boot/grub

---

### Post by edwina on 2006-05-30
Excellent, thank-you. kdesu was the key (just moved over from Gnome, where this doesn't seem to be necessary), but I appreciate you giving me some alternatives too.

---

### Post by aysiu on 2006-05-30
[QUOTE=edwina]Excellent, thank-you. kdesu was the key (just moved over from Gnome, where this doesn't seem to be necessary), but I appreciate you giving me some alternatives too.[/QUOTE] It's the exact equivalent of Gnome's ```
gksudo gedit
```

Both ```
sudo gedit
``` and ```
sudo kwrite
``` will work, but for graphical applications it's a good idea to use ```
gksudo gedit
``` or ```
kdesu kwrite
```

---

### Post by edwina on 2006-06-02
Thanks Aysiu. Can you tell me why "kdesu" is a better way of launching graphics apps from the command line? I have no problem with it, but would be intrigued to know the basis for using "kdesu".

I found that on Gnome (Breezy) there was no apparent issue with ```
sudo gedit menu.lst
```. With KDE (Dapper) It wouldn't launch at all with ```
sudo kwrite menu.lst
``` and, in fact, even with ```
kdesu kwrite menu.lst
``` I still get about 10 lines of text (can't remember what they say, off hand) which makes me think that all is not quite right with my set up.

Thanks again for your help. It is much appreciated.

---

### Post by NoWhereMan on 2006-06-02
graphical apps may do some output on the console. this is not a problem, that output is useful for debugging, it won't affect the functionality of the program :)
if you really don't like that you can put an & at the end of the line
```
sudo gedit /boot/grub/menu.lst &
```
or you can use VIM :D:D:D:D

---

### Post by abloylas on 2006-06-02
Hi,
I got exactly the same error message when running Automatix on Kubuntu as described in [http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930).
Would this be because I installed Automatix using sudo in the first place or is it because Automatix uses sudo when it should be using kdesu?

Cheers

abloylas

---

### Post by aysiu on 2006-06-02
[QUOTE=edwina]Thanks Aysiu. Can you tell me why "kdesu" is a better way of launching graphics apps from the command line? I have no problem with it, but would be intrigued to know the basis for using "kdesu".[/QUOTE] There are particular commands that could go either way (like *sudo gedit*), but it's generally a good idea to get in the habit of using *gksudo* and *kdesu* for graphical applications because using *sudo* with them can mess up the permissions of certain files, sometimes (for example, don't do *sudo firefox*--you'll regret it). Other times, the command simply won't work: *sudo kate*, for example.

---

