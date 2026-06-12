---
title: "unable to upgrade 11.04 to 11.10 now what(dualboot)?"
date: 2011-10-30
forum: General Help
---

### Post by richman88 on 2011-10-30
I was trying to upgrade to 11.10 and it fail so i now i cant go into Ubuntu anymore. I'm able to go all to the login screen but it wont let me do anything. So i think i should reboot back to 10.04 but not sure how though. Oh i dualboot Ubuntu by wubi too.

---

### Post by bcbc on 2011-10-30
It sounds like the upgrade worked, but maybe your computer cannot handle the 3d unity? Try logging in with the 2D desktop - click the cog on the signon screen to change.

---

### Post by richman88 on 2011-11-01
I don't see it on the signon screen? Ima newbie to this ubuntu thing im so sry can u plz it explain it more in detail to me.

---

### Post by bcbc on 2011-11-01
> **richman88 said:**
> I don't see it on the signon screen? Ima newbie to this ubuntu thing im so sry can u plz it explain it more in detail to me.

This is what I mean: 
[http://www.ubuntugeek.com/wp-content/uploads/2011/10/1.png](http://www.ubuntugeek.com/wp-content/uploads/2011/10/1.png)

If you click on the cog you should see **Ubuntu** and **Ubuntu 2d** (not the other GNOME options shown in that screenshot)

"Ubuntu" is the 3d unity, and "Ubuntu 2D" is the 2D unity. Try the 2D.

---

### Post by richman88 on 2011-11-01
Oh ok but  my login screen just shows a pic of a computer desktop in the center which i cant put my username or password in and upper right corner an image of x that allows me to suspend, restart and shutdown that's it. So is there a way i could just go back to 10.04?

---

### Post by bcbc on 2011-11-01
There's no way to downgrade - if you made a backup of your root.disk before upgrading you can restore it but that's the only way.

Try the following to fix:

Drop to a terminal (Ctrl+Alt+F1) and login. 
```
sudo apt-get update
sudo apt-get install lightdm unity-greeter
sudo dpkg-reconfigure lightdm     #( select lightdm if gdm is selected)
sudo reboot
```

Explanation:
apt-get update (update available packages)
install lightdm unity-greeter (make sure you have these installed - the unity-greeter is that screenshot I posted and lightdm is the new display manager for 11.10)
dpkg-reconfigure (set lightdm as the default display manager)
reboot (restart and hopefully you'll get the new 11.10 login)

---

