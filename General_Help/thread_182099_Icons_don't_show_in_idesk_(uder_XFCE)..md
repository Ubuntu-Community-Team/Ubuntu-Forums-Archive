---
title: "Icons don't show in idesk (uder XFCE)."
date: 2006-05-25
forum: General Help
---

### Post by DoktorNo on 2006-05-25
I have installed Ubuntu 5.10 server, and then I installed via apt-get xubuntu-desktop. After working for a while with my new xubuntu, I desired to have some icons on desktop, so I installed idesk. After configuring, and adding one sample icon and starting idesk from terminal the icon did't show. :( But when I am logging out, the icon is flashing on desktop for very short time. So idesk is properly configured, but something is obscuring icons. :???: 

Turning off the background does not work!

---

### Post by DarthMandeep on 2006-05-25
I'm not very familiar with idesk, so I can't help you with that.

What I can do is suggest Rox-filer. It's a file manager that can also be used to manage your desktop wallpaper and desktop icons.  It's fast and easy to use. A big favorite of mine.

I found it much easier and nicer than idesk, but then I tried idesk a long time ago so maybe it's improved.

---

### Post by IYY on 2006-05-25
I'd also suggest Rox. iDesk is quite outdated, and very difficult to make changes to (edit config files just to add a shortcut?).

---

### Post by DoktorNo on 2006-05-26
Thanks for concern . :) Rox is already installed, so there is no problem. But when I start rox, I still cannot drag icons to the desktop. Is there any tutorial about configuring Rox properly?

---

### Post by IYY on 2006-05-26
No need for a tutorial, just one command. When you start rox:

rox --pinboard=MyPinboard

---

### Post by DoktorNo on 2006-05-26
Oh yea, I tryed this, and Rox literally RoXX! :D I'm not a total newbie, but when I logged out with session saving, the next time Rox didn't automatically started. :S Any ideas to solve this?

---

### Post by DarthMandeep on 2006-05-26
I start X directly from the console, so to start rox automatically I added the pinboard line to the end of my .xinitrc file in my home directory.

If you're using a *dm, I think you can edit its config file and add that line.

---

### Post by DoktorNo on 2006-05-26
Thanks! I will try this! :)

BTW: it would be interesting to see Fluxbox and Rox together, but I am not sure, if FluxBox has it own desktop menager&#8230;

And one simple question: can Rox support automouted devices, like USB-drives and CD's, just to pop up their icons on the desktop, like in GNOME?

---

### Post by hudanet2005 on 2006-07-26
i dont have .xinitrc in my home directory
even though i have chosen to view hidden files

rox does not automatically load
the problen is unsolved

---

