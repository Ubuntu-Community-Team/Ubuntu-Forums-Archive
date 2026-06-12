---
title: "Terminal"
date: 2009-10-15
forum: General Help
---

### Post by Bismarck0 on 2009-10-15
Hello! I was wondering, what kind of things can one do in the terminal? I use a laptop that runs Ubuntu, and I would like to know if I could so such things as unmount USB drives, shutdown the computer, open documents, and other shortcuts around using the track pad. I'm not a fan of track pads, and I just wanted to see if I could use the terminal to get around using it so much..

And if there are ways to do such things, could anyone tell me how or just give me a link to an imformative site with such info? Thanks :P

---

### Post by jeremyswalker on 2009-10-15
Oh boy. What can't you do in a terminal? There is quite an extensive list of possiblities using the terminal. As far as mounting, "mount" and "umount" are your friends. Shutdown would be "halt" or "shutdown -h now" or other possibilities. Opening documents could be like "soffice thisfile.odt". Etc, etc, etc. There is virtually an endless list to what you can do in the terminal.

EDIT: You could take a look at this guide on Bash: [Bash Guide for Beginners]("http://tldp.org/LDP/Bash-Beginners-Guide/html/").  If you search around you should find much more information too.

---

### Post by akakingess on 2009-10-15
jeremyswalker is 100% correct, there is almost no limit as to what you can do from the terminal, and in some situations, you don't even need a desktop!

---

### Post by garvinrick4 on 2009-10-15
Google Ubuntu Pocket Guide and download to desktop and have it ready for reading at
anytime and soak it in and keep it open on one of your desktops to start.
Google Ubuntu reference and download a one page basic Terminal commands to desktop
keep it open on one of your desktops (you can have quite a few) right click bottom right
over small windows. Keep notes on what you learn and before long you will be using the Terminal as good as you do a fork and knife. Do not be embarassed to copy and paste as
needed. Right now it probably feels like you are using chop sticks but it gets easy quickly.

---

### Post by KeyserSoze93 on 2009-10-15
I do pretty much everything apart from browsing the web (but I use the Vimperator extension, so I get Terminal-like keyboard control) and editing graphics in the terminal.

It's pretty powerful, and a definite bonus when I use my laptop.

There's lots of howtos, on the forums and elsewhere (see google), and if there's a specific issue, like: how do I mount and unmount my USB drive, then this is a good place to ask.

You'll want to modify it for your own needs, but I use this line in /etc/fstab to mount my usb drive.

```
/dev/sdc1  /media/usb1  auto,vfat defaults,user,noauto,utf8,fmask=111  0 0
```

Because my usb first usb drive will appear as /dev/sdc1 (since I have two harddrives already)

That way, I can mount and unmount (when I've run "mkdir /media/usb1) with:

```
mount /media/usb1
```
and
```
umount /media/usb1
```

---

### Post by nothingspecial on 2009-10-15
> **Bismarck0 said:**
>  unmount USB drives
```

sudo umount /media/disk
```

notice it is umount not unmount

> **Bismarck0 said:**
>  shutdown the computer
```
sudo shutdown -h now
```

or to reboot ```
sudo shutdown -r now
```

or to reboot at 11.30 pm ```
sudo shutdown -r 23:30
```


> **Bismarck0 said:**
>   open documents
in the terminal ```
cat document.txt
```

to edit in the terminal ```
nano document.txt
```

to open a document in a gui editor from the terminal ```
gedit document.txt
```

> **Bismarck0 said:**
>  and other shortcuts around using the track pad
Have a look at this list of [URL="http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts"][COLOR="Magenta"]gnome and kde (amongst others) keyboard shortcuts
[/COLOR][/URL]

 > **Bismarck0 said:**
> I'm not a fan of track pads, 


Neither am I ..... Death to the mouse.


Also have a look at [[COLOR="Magenta"]gnome-do[/COLOR]]("http://do.davebsd.com/")

---

### Post by Bismarck0 on 2009-10-15
Wow! That is a lot of advice. Thanks everyone for all the help. I can't wait until I can almost get rid of using this stupid track pad for good xD

---

