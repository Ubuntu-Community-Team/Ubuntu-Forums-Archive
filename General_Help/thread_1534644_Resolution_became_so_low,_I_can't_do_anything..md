---
title: "Resolution became so low, I can't do anything."
date: 2010-07-19
forum: General Help
---

### Post by Tamber on 2010-07-19
I turned off my computer for the night and everything was working fine. But when I turned it on the next morning the resolution was really low, I tried to set the resolution higher (I picked the largest number it would let me), then reset the computer. Now the resolution is so low I can't even get into my programs or use the computer. 

How can I get the use of my computer now? 

I am VERY new to linux, so please either explain things like you would to an idiot or provide reading material along with your explanations. Thank you.

---

### Post by Tamber on 2010-07-19
Please help, I can't even use my computer right now.

---

### Post by Vaphell on 2010-07-20
what graphics chipset do you have in your computer?

---

### Post by eliotv10 on 2010-07-20
Don't put really high resolution.1280x1024 is OK.

1)Go System->Preferences->Monitors
2)Change your resolution at 1280x1024 and refresh rate at something between 50 and 75.
3)Click apply,restart your pc and see if the resolution been kept

---

### Post by rubylaser on 2010-07-20
Well, what you could do is press crtl+alt+f1 (or f2, f3, basically any of the function keys below 7).  That should take to to a command line window.  Just login with your credentials.

Do you have a backup xorg.conf file in /etc/X11/ ?  If not, type this to reset your xorg.conf file
```
sudo dpkg-reconfigure xserver-xorg
```

Then reboot.  That should get you back to where you started, with low resolution, but at least you can use the screen.  Then, we can work on getting your chipset putting out the proper resolution.

Hope that helps.

---

