---
title: "change gdm theme in ubuntu 10.04"
date: 2010-05-22
forum: General Help
---

### Post by pythonscript on 2010-05-22
What happened to the gdm configuration screen where I could change the default gdm theme? This seems to have disappeared from ubuntu 10.04, and in my personal opinion, the white/purple default theme of the new gdm is terrible and I would like to change it. Where is the GUI for this in lucid, and why has it disappeared?

EDIT:  System -> Administration -> Login Screen only allows me to change automatic logins and other features like that. The GUI I'm referring to *isn't* there.

---

### Post by pythonscript on 2010-05-22
I just learned that this feature was removed since 9.10; I never looked for it in karmic because I didn't find the default theme detestable, but unless anyone has any other simple ideas for how I can change it, it looks like I'm stuck with the default theme for now.

---

### Post by Frogs Hair on 2010-05-22
Appearance preferences > customize allows you to change controls , icons, window borders , colors , and pointer.

---

### Post by dcstar on 2010-05-22
> **pythonscript said:**
> I just learned that this feature was removed since 9.10; I never looked for it in karmic because I didn't find the default theme detestable, but unless anyone has any other simple ideas for how I can change it, it looks like I'm stuck with the default theme for now.

[http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496)

---

### Post by pythonscript on 2010-05-22
> **Frogs Hair said:**
> Appearance preferences > customize allows you to change controls , icons, window borders , colors , and pointer.

This was completely useless, as I'm talking about the GDM log in screen, not the environment once I logged in. I've already configured that section to my liking. 

> **dcstar said:**
> [http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496)

I'll give this a run and report back; thanks for the help!

---

### Post by pythonscript on 2010-05-26
Ubuntu tweak works great; thank you for the tip!

---

### Post by csmith6594 on 2010-05-26
Much thanks to the individual who blessed the Ubuntu community with knowledge in changing the detestable gnome login screen.  May the Linux gods show favor.:guitar:

---

### Post by neo.patrix on 2010-06-25
Ubuntu Tweaks - a program to tweak something which you cannot do normally through adminstration programs provided by regular Ubuntu repositories .... smells foul at philosophical level...bit too much M$ platform.

It would be in best long term interest to have GDM Login configuration back. 

I need following question answered, please...

Did GNOME remove GDM configuration for technical reasons or Ubuntu Developer Team though removing GDM configuration important for simplicity and "greater good" ?

Thanks...

---

### Post by warfacegod on 2010-06-25
All of the things you can do with Ubuntu Tweak can also be done by you as well. Ubuntu Tweak simply makes finding the options easier.

Another option for configing the Loggin screen is here: [http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

With a little more work this will be a fantastic app and I think it should replace the lame crap that gdm Loggin has become.

---

### Post by 4hp007 on 2010-06-26
> **dcstar said:**
> [http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html#more-5496) 
Worked well for me

---

### Post by RedSingularity on 2010-06-26
The Tweak application is great.  Thanks for that. :)

---

### Post by tad1073 on 2010-06-26
and yet another...

[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

---

### Post by _MsG_ on 2010-06-27
But why do they keep removing functionality just because of ol' granny who doesn't need it? I hate it that Ubuntu is too much going that way.

---

### Post by Spr0k3t on 2010-06-27
I prefer this method to change the new GDM theme.

To change the theme add gnome-appearance-properties to GDM's autostart applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. Select a new theme/wallpaper/font/icons/pointer. Log in and remove gnome-appearance-properties to GDM's autostart applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Simple, interactive, and no additional applications needed to make the changes.

---

### Post by sqeeek on 2010-08-20
> **Spr0k3t said:**
> I prefer this method to change the new GDM theme.

To change the theme add gnome-appearance-properties to GDM's autostart applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. Select a new theme/wallpaper/font/icons/pointer. Log in and remove gnome-appearance-properties to GDM's autostart applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Simple, interactive, and no additional applications needed to make the changes.

Nice work, thanks for that. I've been looking for a way to make it look less like crap for weeks. Not that it's essential or anything, but I finally feel complete :) I even added both commands to a script, much shorter to type customgdm_on or customgdm_off. *happy*

As for whoever decided to make gdm uncustomizable, what the heck? I mean, when I switched to Linux, the fact that everything could be set up just the way you like it was one reason I'm not using a mac right now.

---

### Post by Jonathan Moerman on 2011-03-19
[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/) this worked great for me but you might have to replace Ctrl+ALT+F7 with Ctrl+ALT+f8

---

### Post by UburR00T on 2011-07-22
> **Spr0k3t said:**
> I prefer this method to change the new GDM theme.

To change the theme add gnome-appearance-properties to GDM's autostart applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```Log out. Select a new theme/wallpaper/font/icons/pointer. Log in and remove gnome-appearance-properties to GDM's autostart applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```Simple, interactive, and no additional applications needed to make the changes.

Thanks a lot, Perfect in Simplicity ;)

---

### Post by dgh1973 on 2011-10-07
[http://www.ubuntugeek.com/how-to-ins...html#more-5496](http://www.ubuntugeek.com/how-to-ins...html#more-5496)


I'm sorry but that right there is BS!

That is a WINDOWS/MAC methodology. What happened to the Linux I knew and love?? What happened to giving me the tools I need already baked in to the system?

If I have to download special utilities to access simple configuration settings now in Ubuntu this is IMHO showing a BAD TREND in moving toward commercial acceptance and leaving the geeks behind.

Speaking for geeks, many of us are past the "install slackware because that's for geeks" phase of our existence, I still want an os that is fast to install and easy to use while giving me access to all of the underpinnings.

Now I understand why Linus says "Just use KDE". This "wash away all the ugly stuff, period" approach is wrong, this is the best OS on the planet, we should be able to have our cake and reach inside and get messy with it too if we want to.

Disappointed...

EDIT: Respect to UburR00T for the *real* solution here

---

