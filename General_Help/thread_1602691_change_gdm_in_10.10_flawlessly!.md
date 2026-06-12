---
title: "change gdm in 10.10 flawlessly!"
date: 2010-10-21
forum: General Help
---

### Post by twodogs on 2010-10-21
I have Ubuntu 10.10 installed and found out gdm2setup does NOT work in this new version of Ubuntu.

I did not like the default look and wanted it to look consistent with my desktop.

Following the directions below, and my included tips, you will have a nice gdm setup that looks great.

Basically,  you will run the gnome-appearance gui application at your login.  You will then choose the theme you want.  You can also choose the background, the icons, and the font.  This is the same application that you would use if you right clicked on your desktop and selected 'change background.'  For me, I chose 'Mirav2' for the theme (a kick *** dark theme that looks amazing!) and Ubuntu-Mono-Dark for the icons.  I changed the font to Droid and then chose to change the background to the same one I have on my desktop (I told you I wanted consistency!).

Here you go...

First open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:
 
    sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
 
Now close the Terminal window and logout.

When the login screen appears, the Appearance window pops up. Here you can make the changes you want and when you are done you can login as usual. 

To prevent the Appearance Manager from opening when you login, open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:
 
    sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

Enjoy!

---

### Post by Def_101 on 2010-11-01
Great work finding this little baby. The orange login color wasn't doing it for my dark background. Thanks for sharing.

---

### Post by WishMaster on 2010-11-21
Wow, thanks man !
I've come to hate the default Ubuntu colors (ambiance, dust, new wave, radiance), so I've set up my theme to match with the Xubuntu theme (Bluebird).
I was missing the GDM part, which is now completed thanks to you !

---

### Post by echo6 on 2010-11-22
Alternatively:
1. log out of your gnome session.
2. Switch virtual terminals ctrl-alt-F1
3. Login, sudo su
4. export DISPLAY=:0.0
5. sudo -u gdm gnome-control-center
6. ctrl-alt-F7 to switch back to your login screen and setup the appearance as required.

---

