---
title: "Installed... what now?"
date: 2006-05-16
forum: General Help
---

### Post by NoeticFool on 2006-05-16
Hi,

I'm trying to install Kubuntu 5.10 on my Apple Powerbook (G4, 500 Mhz).  I downloaded the *.iso file for Kubuntu for Macs, made the installation CD, and just went through the install procedure.

The installation goes to 100%, then promts me for my username and password (still in black and white text), which looks like this:

Ubuntu 5.10 "Breezy Badger" Ubuntu ttyl
ubuntu login:
password:

I entered my login and password okay, but then I only get a little bit more text, followed by this prompt:

adam@ubuntu:~$_ 

And that's all.  Is there something I need to type here to take me to the desktop?  Or is something not working right?

The only issue it seemed to have durring installation was a quick failure notice that said:

invalid ROM signature 0 should be [hex code]

If you can help, thanks!

---

### Post by aysiu on 2006-05-16
It looks as if you might have done a server install...? But that's odd that that would happen by accident. You'd have had to have fallen on the keyboard, accidentally hitting the key s e r v e r in that order.

Well, in any case, log in at the terminal prompt and try these commands: ```
sudo /etc/init.d/kdm start
sudo apt-get update && sudo apt-get install kubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
startx
``` If the first command doesn't work, try the second and so on...

---

### Post by tseliot on 2006-05-16
OR the xserver crashed and you didn't notice. (Follow aysiu's suggestion first)


type:
```
sudo nano -w /etc/X11/xorg.conf
```

Scroll down the file with your keyboard and set the driver to "vesa" in the Section Device of the file.

CTRL+X to exit (save the file)

Then restart the xserver:
```
sudo /etc/init.d/kdm restart
```

and you should see the graphical login

---

### Post by Peter76 on 2006-05-16
I had this problem sometime as well on a Mac; sometimes you get to the graphical login, sometimes you get what you get; just press alt+f7 and you'll get the graphical login.

---

