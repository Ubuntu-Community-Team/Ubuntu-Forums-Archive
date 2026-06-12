---
title: "Change Login Window"
date: 2010-04-30
forum: General Help
---

### Post by RedSingularity on 2010-04-30
After installing the newest ubuntu, 10.4, i have noticed that I cannot set a custom login screen like i could in previous versions.  Is there a work around for this?

---

### Post by slvr42 on 2010-04-30
Here is a sort of workaround

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

This will cause the gnome appearance properties to appear when you logout.

Logout and edit what settings you can.  You can set the background and change the theme but that's about it.

Now you can either remove it from the login window directory or use the unlink command which does the same thing.

sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

or

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

Now it won't appear when you log out.  If you need it back just copy it back in there.

---

### Post by -_-' on 2010-05-03
But I can't edit the loginin screen, only my background, the theme of my windowss  etc. Not my login screen.  Am I doing something wrong?

---

### Post by slvr42 on 2010-05-04
No you aren't doing anything wrong.  Unless you build a custom GDM theme there will only be so much you can edit on the Login screen.

---

### Post by thongstele on 2010-05-19
Dear all,
In this previous version of Ubuntu, with GDM we can choose a theme to change (for example a theme like Mac os), but in Ubuntu 10.4 we cannot. See link as follow: [http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2)
For my purpose is that I want to change my Login screen as Mac os. However I cannot do anything in Ubuntu 10.4. I'm sad...

---

### Post by vnrat on 2010-05-20
the link provided by you just only used for ubuntu older versions

---

### Post by bbrg548 on 2010-05-21
> **vnrat said:**
> the link provided by you just only used for ubuntu older versions

I think that's what he's getting at - why did they take this away?

I'd like to know, too. I want my custom login screen back!

---

### Post by hardyrocks on 2010-06-25
hey i was able to change the login windows n all on ubuntu 10.04....
here's the tutorial for making it look like mac.. :)

---

### Post by hardyrocks on 2010-06-25
hey i was able to change the login windows n all on ubuntu 10.04....
here's the tutorial for making it look like mac.. 
[http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08]("http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08")
:)

---

### Post by philinux on 2010-06-25
[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

---

