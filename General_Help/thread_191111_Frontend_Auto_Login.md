---
title: "Frontend Auto Login"
date: 2006-06-07
forum: General Help
---

### Post by fopetesl on 2006-06-07
I need to up grade to 6.06 from 5.10 but 1st ..

I found this link regarding auto login which is supposed to bypass login screen:

   [http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login](http://www.mythtv.org/wiki/index.php/Frontend_Auto_Login)

which suggests placing this line in /etc/inittab:

```
c7:12345:respawn:/sbin/mingetty --autologin=UserName tty7
```

though I altered the runlevels to '345'.

Not work unfortunately.

I need this feature since am (re)building a kiosk application and Ubuntu is the only OS (of six) I've tried which is stable.

---

### Post by krye on 2006-06-07
You could try enabling auto-login for GDM in the "Login Window" section of the administration menu with the mythtv user and have mythfrontend run at beginning of session.

Would this work out for you?

---

### Post by fopetesl on 2006-06-07
Boy! You're up late, (or early?).  Thanks for the suggestions - will come back to you later, (or earlier!).8)

---

### Post by krye on 2006-06-07
It's 2:13 am in here, not that late ;)

Good luck!

---

### Post by fopetesl on 2006-06-07
> You could try enabling auto-login for GDM in the "Login Window" section of the administration menu with the mythtv user
I used '[COLOR="Red"]peter[/COLOR]' (me) as User since I am not interested in *mythtv* but didn't see any change.  Still had to log in as normal.

I also tried altering [COLOR="Blue"]/etc/X11/xinit/xinitrc[/COLOR] to not load a window manager but that doesn't work either.  Other OS systems have an .xinitrc file in the User's [COLOR="Blue"]/home[/COLOR] directory but not here!

I could get around the Auto Login if I could over ride wherever the [COLOR="Blue"].xinitrc[/COLOR] file is executed by writing my own.  But where is the equivalent?  Did a search but not found.

---

### Post by fopetesl on 2006-06-08
login as root.
It's called Kiosk mode. In GDM, edit /etc/X11/gdm/gdm.conf and look for the AutomaticLoginEnable and AutomaticLogin settings.
Set [COLOR="Blue"]AutomaticLoginEnable=true[/COLOR]
and [COLOR="Blue"]AutomaticLogin=User_of_your_choice
[/COLOR]
Hope this helps someone else:grin:

---

### Post by usererror on 2006-08-22
> **fopetesl said:**
> login as root.
It's called Kiosk mode. In GDM, edit /etc/X11/gdm/gdm.conf and look for the AutomaticLoginEnable and AutomaticLogin settings.
Set [COLOR="Blue"]AutomaticLoginEnable=true[/COLOR]
and [COLOR="Blue"]AutomaticLogin=User_of_your_choice
[/COLOR]
Hope this helps someone else:grin:

that worked perfectly for me!  on to customizing the menus.  how does it log in the user without needing the password though??

---

