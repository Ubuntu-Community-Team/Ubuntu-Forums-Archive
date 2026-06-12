---
title: "Login Fonts Too Small"
date: 2011-08-15
forum: General Help
---

### Post by meharts on 2011-08-15
Hi folks!
OK! This is something that has been a problem since the dawn of time...

So many of us can hardly see what we are writing in the login window....?!

Yep it is nice having the nice backgrounds etc...but what about the font size?

Is there a solution for this problem?

Just want to see the text a bit better.

meharts

---

### Post by LowSky on 2011-08-15
This should so it:


open a terminal:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

then log out

chose your new settings

then once you log back in, then open a terminal and  use this command 

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by meharts on 2011-08-16
Hi LowSky:)

Thanks for coming by

OK! changing font sizes normally I can do in Ubuntu 11.04...

How do I change the settings pertaining to the Login window...i.e. password size etc?


meharts

---

### Post by meharts on 2011-08-16
Hi again!
This is ridiculous...I can increase dpi and everything gets larger but where you actually write the password...that seems smaller and smaller...just a few little dots?

There must be a solution for this?

meharts

---

### Post by meharts on 2011-08-16
Hi again!

No takers?

I find it hard to believe that I am the only one with this problem.......Hasn't anyone found a way to increase the font size for the text in the "text entry field" (login)?



meharts

---

### Post by meharts on 2011-08-17
Hi again!
Trying to look at this logically...put me right if you think I am wrong....

In the older versions of Ubuntu it was GDM responsible for rendering the login window....and now it is X11


I have had Ubuntu installed two times on the same computer....the first was with a Asus Geforce EN210 512mb graphics card and I had the same problem as now..

I now have a new card a Asus HD 6870 and with both I am getting the text in the entry field too small....

I have checked the settings:
```


$ xdpyinfo | grep dimensions  [COLOR="Red"] ( 1280x1024 338x270 millimeters)[/COLOR]
$ xdpyinfo | grep "dots per inch" [COLOR="Red"](96x96 dpi)[/COLOR]

```

This seems to coincide with the screen I am using on this machine

Am I mssing something or is the info right and I should get login rendering so that I can see the dots....LOL

The other thing I noticed is the /usr/share/gdm/gdm-greeter-login-window.ui...I see that this can be edited with glade, but I am not familiar with the terminology used and can't see where I could increase the font size for entering password info et...

Any thoughts on this....


Thanks 

meharts

---

### Post by meharts on 2011-08-18
Hi again!
Like I have said this problem has reared its ugly head many times over the last few years.....

I think it is time the developers find a simple an effective way of solving this whatever your setup...graphics card etc!!

meharts

---

