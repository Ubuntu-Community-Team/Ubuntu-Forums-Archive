---
title: "Getting Gnome from Kubuntu?"
date: 2011-02-16
forum: General Help
---

### Post by Mariane on 2011-02-16
Hi, 

Before I used to get KDE from gnome, it was just a matter of guessing the correct packages names. When I log out I have the option to change the session at will and log back in. 

From Kubuntu 10.10 however I did not manage to get Gnome. I found something called gnome-desktop-somethingorother and installed that. I also installed xfce4 which is usually very easy. But when I log out I still don't see the option to change the session. Please help. 

Mariane

---

### Post by kn0w-b1nary on 2011-02-16
you have to install ```
gnome-session
``` or ```
xfce4-session
```

Hope this helps!

---

### Post by ajgreeny on 2011-02-16
The easiest way is probably now to install ubuntu-desktop package.  That will add a few more packages to the standard gnome that you have already, but should then give you all the desktop change options you're looking for.  This can all be accessed in the Session menu, bottom right of the login screen (on gnome; I've no idea where on the kubuntu login screen), but the menu will not appear until you have chosen the user, but before you enter the password.

---

### Post by Mariane on 2011-02-17
Thank you. gnome-session and xfce4-session I had already. ubuntu-desktop did the trick but I saw some scrolling message that said it was removing alsa to install *** pluseaudio. 

I tested with: 

```

say hello

```

and the output was:
he~lo######~T
Could not open localsound device, error 2
Client side error: Could not set up a stream

And no sound. So yeah, looks like pulse-audio alright. 

Anyway this is a different problem, so I'll mark this thread as solved. 

Mariane

---

### Post by ajgreeny on 2011-02-17
>  I saw some scrolling message that said it was removing alsa to install *** pluseaudio. That seems very odd to me as pulseaudio in ubuntu needs alsa to work; it can not work all on its own.  Perhaps a new thread needed?

---

