---
title: "Alter Ubuntu 11.10 Login Screen"
date: 2012-03-23
forum: General Help
---

### Post by uRock on 2012-03-23
I used to use this tutorial, but it does not work with 11.10. [http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

When I run the command in the terminal I get this,```
urock@uRock-Desktop:~$ sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
cp: cannot stat `/usr/share/applications/gnome-appearance-properties.desktop': No such file or directory

```Can someone tell me how to do this in 11.10?

---

### Post by PhantomTurtle on 2012-03-23
Ubuntu 11.10 uses Lightdm, not gdm(well not anymore atleast). You cannot do this in Ubuntu 11.10. If you want to change the background, just use this tutorial - [http://www.omgubuntu.co.uk/2011/10/simple-lightdm-manager-lets-easily-tweak-ubuntu-11-10-login-screen/]("http://www.omgubuntu.co.uk/2011/10/simple-lightdm-manager-lets-easily-tweak-ubuntu-11-10-login-screen/")(its really easy, much easier than that tutorial:)).

---

### Post by uRock on 2012-03-23
That did work very well. Thank you!:)

---

