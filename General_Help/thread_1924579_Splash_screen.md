---
title: "Splash screen"
date: 2012-02-13
forum: General Help
---

### Post by Mazate on 2012-02-13
Hola... I actually have two questions...

1)  I while back I did a terminal command to make the gnome shell the default desktop regardless of whatever desktop I was on before I shut down.  I would now like to make it so that whatever desktop I was on previously is the one that will load the next time I turn on my computer.  Can anyone tell me how to do that?

2)  Since I installed KDE, I automatically get the Kubuntu splash page whenever I'm shutting down or restarting.  Is there a way to get the regular Ubuntu splash page to come up?

Thanks in advance.

---

### Post by josephmills on 2012-02-13
> **Mazate said:**
> Hola... I actually have two questions...

1)  I while back I did a terminal command to make the gnome shell the default desktop regardless of whatever desktop I was on before I shut down.  I would now like to make it so that whatever desktop I was on previously is the one that will load the next time I turn on my computer.  Can anyone tell me how to do that?


sorry can help with that 

> 
2)  Since I installed KDE, I automatically get the Kubuntu splash page whenever I'm shutting down or restarting.  Is there a way to get the regular Ubuntu splash page to come up?

Thanks in advance.


this one I might be able to help on. 

open your terminal and type in 
```
sudo update-alternatives --config plymouth
``` 

pick the one you like then run 
```
sudo update-initramfs -u
```


You can also look at the plymouth configuration file located in 
/lib/plymouth/
but you do not need to do this. 
I am sure that there are other ways to do this but this is the only way I know how. :D

---

### Post by Mazate on 2012-02-18
Yeah, no luck on this.  I remember there was just a short little command to do it.  I just don't recall what it was.

---

### Post by Krytarik on 2012-02-19
> **Mazate said:**
> 1)  I while back I did a terminal command to make the gnome shell the default desktop regardless of whatever desktop I was on before I shut down.  I would now like to make it so that whatever desktop I was on previously is the one that will load the next time I turn on my computer.
Back then, you did this; pulled it from your post history ;-) :

[http://ubuntuforums.org/showthread.php?p=11413719#post11413719](http://ubuntuforums.org/showthread.php?p=11413719#post11413719)

I presume you are auto-logging in; right? For auto-login, the session is fix, and doesn't take into account to which session you logged in the last time. To change it, just replace "gnome-shell" in the command you've run earlier with the value corresponding to your desired session; you'll find a list in this guide (sorry, copy & paste sucks in this case :P):

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

EDIT: Upon testing this now with an Oneiric 11.10 Live ISO, with an updated LightDM, I've just noticed that this isn't true anymore; any setting for both "user-session" and "autologin-session" in the "/etc/lightdm/lightdm.conf" will be overridden by the last used session, stored in the user's "~/.dmrc" - which is great, of course. :D However, in your case, this doesn't seem to apply; is your system updated!?

> **Mazate said:**
> 2)  Since I installed KDE, I automatically get the Kubuntu splash page whenever I'm shutting down or restarting.  Is there a way to get the regular Ubuntu splash page to come up?
There is an error in *josephmills*' first command; correct is:
```
sudo update-alternatives --config default.plymouth
```Then choose "ubuntu-logo.plymouth", followed by:
```
sudo update-initramfs -u
```Regards.

---

