---
title: "Lock Screen not working in 12.04"
date: 2012-04-26
forum: General Help
---

### Post by rmcellig on 2012-04-26
I just installed 12.04 and it looks great so far.I do however have a problem. When I select Lock Screen from the upper right hand icon, nothing happens. Even trying Control-Alt-L doesn't do anything. Am I missing something here? I tried in 2D and regular 12.04 login with the same results.

---

### Post by codingman on 2012-04-26
Same with me, I for some reason can't do Ctrl-Alt-T sometimes same with meta and lock.

---

### Post by mordalo on 2012-04-27
I found a workaround in an article posted on [webupd8.org]("http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html"):

To quote:

[I]To get CTRL + ALT + L to lock the screen and start the screensaver, go to System Settings > Keyboard and on the "Shortcuts" tab, under "System", change the "Lock screen" keyboard shortcut from CTRL + ALT + L to something else, then under "Custom Shortcuts", click the "+" button to add a new custom shortcut, under "Name" enter "Xscreensaver" and under "Command" enter "_/usr/bin/xscreensaver-command -activate_", then click "Apply".

And finally, click next to the newly created shortcut and press CTRL + ALT + L to assign it to it (or use any other keyboard shortcut you want, but make sure it's not already assign to something else). [/I]

I did have to log out and log back in, but it does work.  The article didn't list using the "-activate" command, but I found that through trial and error.

---

### Post by borikanes on 2012-07-02
Hey guys all you need to do is 
sudo apt-get install gnome-screensaver
It so happens that when you were installing xscreensaver you removed gnome-screensaver. I'm guessing lock screen is implemented in gnome-screensaver so when you try to lock it, it doesnt know what lock screen means. Again its a guess I'm not sure if lock screen is implemented in gnome-screensaver.

---

### Post by Zvikatron on 2012-07-05
> **borikanes said:**
> Hey guys all you need to do is 
sudo apt-get install gnome-screensaver
It so happens that when you were installing xscreensaver you removed gnome-screensaver. I'm guessing lock screen is implemented in gnome-screensaver so when you try to lock it, it doesnt know what lock screen means. Again its a guess I'm not sure if lock screen is implemented in gnome-screensaver.

Thank you very much, that worked for me :)

Finally!

---

### Post by bluepearlsky on 2012-07-26
> **borikanes said:**
> Hey guys all you need to do is 
sudo apt-get install gnome-screensaver
It so happens that when you were installing xscreensaver you removed gnome-screensaver. I'm guessing lock screen is implemented in gnome-screensaver so when you try to lock it, it doesnt know what lock screen means. Again its a guess I'm not sure if lock screen is implemented in gnome-screensaver.

Sorry bro, I did as above, but it is not working. After the set time, the screen goes half dark and the computer hangs. Nothing wakes it. I need to press RESET button to shutdown and reboot. 

Please help. 

~bluepearlsky~
akbagchi at gmail dot com

---

### Post by MNNorthStars on 2012-11-12
> **borikanes said:**
> Hey guys all you need to do is 
sudo apt-get install gnome-screensaver
It so happens that when you were installing xscreensaver you removed gnome-screensaver. I'm guessing lock screen is implemented in gnome-screensaver so when you try to lock it, it doesnt know what lock screen means. Again its a guess I'm not sure if lock screen is implemented in gnome-screensaver.

Worked great for me! Thanks! :)

---

### Post by stylintile on 2013-04-21
I don't know if this is the right place to post this but I am having a similar problem.  With gnome screensaver I can't seem to change the screen from blacking out.  However when I install and run xscreensaver, screen lock doesn't work at all.  I tried clicking on the indicator applet and using ctrl-alt-l, and I tried changing the keybinding to alt-e and neither one worked.  I don't use a screensaver and don't want my screen blacking out, but I do want to be able to lock my screen since there is a thirteen-year-old boy here who has discovered porn sites.  Any help would be greatly appreciated.  Thanks in advance.  Stylintile


Never mind.  I had to reinstall because I crashed my system trying to install themes that I guess were incompatible.  Disabled in the brightness and lock in settings and now it works.  Thanks anyway

---

### Post by experimancer on 2013-05-12
Hi,

the same thing happened to me; the lock screen just suddenly stopped working. so that pressing CTRL-ALT-L or the graphical command in the upper right corner did nothing.

The reason was that I had accidentally removed the gnome-screensaver config file, while doing some updates to my system. As posted in #4 re-installing gnome-screensaver did the trick, and lock screen works again now!

Cheers,
-jukka

---

### Post by stylintile on 2013-05-13
Hello again,
     I tried reinstalling gnome-screensaver, but I still couldn't get it to stop blacking out the screen.  However, it's no longer an issue with me.  I reformatted and installed Xubuntu and everything is working perfectly.
Thanks anyway:D

---

### Post by drbono on 2013-05-14
If you have Cinnamon installed (even if you are using unity) and you recently got the 1.8 version update, it uninstalls gnome screensaver.  If you reinstall gnome screensaver, logout and back in...worked for me.

---

### Post by OrangeVixen on 2013-05-15
I believe what is happening here is a conflict between gnome-screensaver and xscreensaver.

By default when you install Ubuntu 12.04 Precise, you get gnome-screensaver. However all gnome-screensaver does is blank the screen (or lock the screen) to black.

xscreensaver on the other hand has a lot more "eye candy", however it is not integrated to the GNOME settings and you can not lock it from the Session Menu (the menu item at the upper right corner of the panel).

Further, xscreensaver conflicts with gnome-screensaver (even though the packages do not seem to indicate it). so you need to check (run Synaptic) and see if you have both installed. You can check by running Synaptic and type in "screensaver" in the Quick Filter.

You should only have one installed, there is this HOWTO: Replace gnome-screensaver with xscreensaver [http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

