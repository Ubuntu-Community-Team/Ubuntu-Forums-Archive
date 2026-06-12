---
title: "change login screen without using any tweak app"
date: 2011-09-14
forum: General Help
---

### Post by sptutusukanta on 2011-09-14
I want to change the login background and icon at login screen. I know it can easily be done using ubuntu tweak. But I want to do it manually without replacing any icon/background file.

Acually I want to know where is the settings for the login screen. where I can put the location of the images & it will show up nicely!

Thank you!

---

### Post by jimmyxu on 2011-09-14
Pls refer to the below link, hope it can help u. Gook luck.

[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

---

### Post by Sigma1 on 2011-09-14
This method worked for me, though it doesn't entirely answer your question, just runs gnome-appearance-properties on the login screen: [http://ubuntuguide.net/an-effective-way-changing-ubuntu-11-04-login-screen-appearance](http://ubuntuguide.net/an-effective-way-changing-ubuntu-11-04-login-screen-appearance)

P.S. looks like jimmyxu beat me to it, with a more comprehensive reply!

---

### Post by sptutusukanta on 2011-09-14
> **jimmyxu said:**
> Pls refer to the below link, hope it can help u. Gook luck.

[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

I'm using gnome-shell/gtk3 over ubuntu-11.04 here I got an error:

[B][FONT="Courier New"]system@neos-pc:~$ sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
[sudo] password for system: 
cp: cannot stat `/usr/share/applications/gnome-appearance-properties.desktop': No such file or directory[/FONT][/B]

Please Help!

---

### Post by Sigma1 on 2011-09-16
Well perhaps gnome-appearance-properties.desktop is hidden somewhere else... If I were you I'd try ```
locate gnome-appearance-properties.desktop
``` first, to find where it is, if that gives you a viable path, then replace the /usr/share/applications/gnome-appearance-properties.desktop with that.

---

