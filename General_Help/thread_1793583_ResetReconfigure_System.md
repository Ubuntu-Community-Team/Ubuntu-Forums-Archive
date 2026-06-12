---
title: "Reset/Reconfigure System"
date: 2011-06-29
forum: General Help
---

### Post by peterlauri on 2011-06-29
Is there any way to reconfigure/reset the system to its original settings/configuration?

My webcam stopped working, and I'm getting desperate, and re install will be done tomorrow if I cannot manage to get this to work. And I don't want to do that, rather go out in the sun and to other things.

---

### Post by nzjethro on 2011-06-29
[This site]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") will help you restore your DE to default.

The code
```
sudo rm -rf ~/.*
```
will delete all your user settings (you'll have to restart afterwards), but **be careful using this command.**

Try these and see whether it has reset the settings you want, but I think the easiest option may just be to save anything important, and then re-install. And hey, set it installing, then head out into the sun! :)

---

