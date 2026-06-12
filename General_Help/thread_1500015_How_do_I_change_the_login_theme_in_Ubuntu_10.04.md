---
title: "How do I change the login theme in Ubuntu 10.04?"
date: 2010-06-02
forum: General Help
---

### Post by OmegaAI on 2010-06-02
I remember back with 7.10, 8.04, 8.10, and I think even Ubuntu 9.xx I was able to change the login theme but now I cannot do that anymore with 10.04.


Does anyone know how I can do this?

If you do not understand what I mean, look here:

[http://linuxologist.com/eye-candy/30-cool-linux-login-screens/](http://linuxologist.com/eye-candy/30-cool-linux-login-screens/)


Before I could have installed all those themes and switched between them, even modify how they look...

What do I have to do?

---

### Post by mattweed9 on 2010-06-02
This is how I do it. Maybe not the best, but it works and is simple.



To change login screen


copy paste this into terminal

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop  
 
```


[B]Then Log out to the login screen and the theme window will open. Adjust to your liking.
[/B]

Then use this once you have logged back in. Copy and past it in the terminal. This just stops the theme window from opening every time you are at the login screen.

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by OmegaAI on 2010-06-02
e-e Done that already and not too fond of it... Hm... I wonder if lets me load themes into it.

---

### Post by philinux on 2010-06-02
Search gdm2 setup.

---

