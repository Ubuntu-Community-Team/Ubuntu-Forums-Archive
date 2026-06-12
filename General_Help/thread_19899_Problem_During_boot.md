---
title: "Problem During boot"
date: 2005-03-14
forum: General Help
---

### Post by afroman on 2005-03-14
After battling with the installation, i eventually got it installed and when booting up it says all the necessary eg. booting kernel                                 [ ok ]
etc. etc. etc. then an error message appears - something to the likes of this
                        *res temporary name resolution failure                                  [fail]
then when the login screen is supposed to appear there is just a black screen!
Some one please help!!!!!!

---

### Post by kamstrup on 2005-03-14
The name resolution thing is because the network isn't working...  Try waiting a minute or so and see if the login screen doesn't appear.

What exact version of Ubuntu have you installed? Hoary or Warty? Did it say 5.04 or 4.10?

Also which graphics card do you have (be as specific as you can)?

---

### Post by Buffalo Soldier on 2005-03-14
afroman,

Glad that you manage to solve cd burning problem and start installing. 

Yes, I agree with kamstrup. The more specific the description of your problem and the more detail of your computer spec... the easier is is for people to help you.

---

### Post by afroman on 2005-03-14
Ya thanks buffalo soldier for the help in getting the installation going as soon as i copied at a slower speed it works, your help is really appreciated!
My machine is a laptech laptop, Pentium 233mhz, 64megs ram, i dont know exactly what my graphics card is, it may be onboard - it runs at 128bit
I think the actual problem is - i tried installing again and when the first boot screen tried to load it said - 
Loading Gnome display Manager
Gnome display manager failed 
then it comes to a black screen
I have tried reinstalling many times!

PLEASE HELP!!!!!!

---

### Post by alastair on 2005-03-14
GDM is not starting.

You can probably switch to a text VT using something like CTRL+ALT+F1(F2 etc.).

Then, look in the logs i.e.

/var/log/syslog

/var/log/X*.0.log

and see if there are errors.

If this is a graphics problem then - what graphics card? And what's in the X config?

/etc/X11/XF86Config or
/etc/X11/xorg.conf

---

### Post by kamstrup on 2005-03-15
Yes. Do a CTRL+ALT+F1 as alastair point out. Use "sudo nano -w /etc/X11/xorg.conf" or XF86Config depending on whether you are running Hoary or Warty.

Find the "Device" section, and make sure that it says "vesa" in the entry 

Driver "something"

-- ie. "something" should be "vesa", if that still doesn't work (or if it's vesa already), try "fbdev". Save, and reboot (maybe pray a little)...

The problem is that it sounds like a rather old laptop you have there. It might have really strange harware :-S You might also experience poor performance. Normally I'd say 500MHz and 128 MB RAM, as a minimum, but give it a spin anyway. I've never actually tried Ubuntu on smaller machines.

PS: What do you mean by 128 bit?

---

### Post by afroman on 2005-03-15
Hey please help me a bit more with the sudo commands as a am new to linux!
Thanx

---

### Post by alastair on 2005-03-15
All you need to do is have a look at the files :

/var/log/syslog
/var/log/X*.0.log
/etc/X11/XF86Config or
/etc/X11/xorg.conf

and perhaps post them here for folks to have a look at. See if you can see any "errors" reported.

Perhaps you can copy them to a USB disk, other partition or a network machine and then look at them?

Explain where you are having trouble.

---

### Post by kamstrup on 2005-03-15
Hitting ctrl-alt-f1 will send you to a text-based log in prompt. Log in. We need to know whether you run Hoary or Warty. To find out this type "uname -r" and hit return. If it prints back something with 2.6.8.1 you are using Warty, if it prints out something with 2.6.10 it is Hoary.

If Hoary: Type "sudo nano -w /etc/X11/xorg.conf" hit return
If Warty: Type "sudo nano -w /etc/X11/XF86Config" hit return

and follow the instructions above.

Good luck.

---

