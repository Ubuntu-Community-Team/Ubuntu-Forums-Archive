---
title: "How do I set a default desktop environment?"
date: 2012-09-17
forum: General Help
---

### Post by Welly Wu on 2012-09-17
I have a System76 Lemur Ultra Thin (lemu4) with Ubuntu 12.04.1 64 bit Long Term Service and I want to set Cinnamon to be the default desktop environment after I login to the Ubuntu Greeter (lightdm). Currently, it is set to the default Unity desktop environment. How do I change it and make everything work properly? Please help me if you can. Thank you.

---

### Post by Welly Wu on 2012-09-17
[http://www.tejasbarot.com/2012/05/17/howto-change-default-user-session-ubuntu-12-04-lts-precise-pangolin-login-session-desktop-environment/](http://www.tejasbarot.com/2012/05/17/howto-change-default-user-session-ubuntu-12-04-lts-precise-pangolin-login-session-desktop-environment/)

I followed this guide, but it produced an undesireable effect. I typed in this command:

sudo /usr/lib/lightdm/lightdm-set-defaults -s cinnamon.desktop
sudo /etc/init.d/lightdm restart

Now, the Ubuntu Greeter (lightdm) no longer loads up after I log out or when I reboot or power on my System76 Lemur Ultra Thin (lemu4) notebook PC. I get this alternative lightdm login screen that functionally works because it allows me to log in and choose my desktop environment, but it is not the standard Ubuntu Greeter.

How do I fix this problem so I get the Ubuntu Greeter (lightdm) screen again?

---

### Post by Welly Wu on 2012-09-18
I am getting the Warty Warthol login screen now. How do I change this back to the default Ubuntu Unity Greeter? This is getting to be annoying.

---

### Post by DeezyFaReal on 2012-09-18
Are you willing to reinstall the ubuntu desktop?
That's what I would do
I don't mean the operating system, I mean just the desktop

---

### Post by Welly Wu on 2012-09-18
No, that did not work. Any other suggestions to fix this problem?

---

### Post by vasa1 on 2012-09-18
My feeling is that Cinnamon has been best tested to work with the Mint OS.

---

### Post by Welly Wu on 2012-09-18
I got a response from System76:

Try running these commands from a command line:

sudo apt-get purge lightdm
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install ubuntu-desktop

This  will completely remove the Unity greeter, then reinstall it and any  other missing packages by getting the "ubuntu-desktop" command.

---

### Post by irv on 2012-09-18
If you really want to run Cinnamon as a desktop, what you could do is setup a duel boot system with Ubuntu with Unity and Mint with Cinnamon. That is if you have a big enough hard drive. I think there is a problem with trying to run unity and Cinnamon in the same install.

I like them both but my SSD is only 180gig so I chose to just run one and it is Ubuntu with Unity. One you run Unity for awhile it grows on you.

---

