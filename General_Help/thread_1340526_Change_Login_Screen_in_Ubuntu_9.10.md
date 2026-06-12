---
title: "Change Login Screen in Ubuntu 9.10?"
date: 2009-11-28
forum: General Help
---

### Post by kyle2595 on 2009-11-28
Hi, I was looking on the web, and I came across this:

[http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

It says that you can change your login screen, so I downloaded the .tar.bz2 file.  I want to know how to apply that image as my login screen.  Thanks!

---

### Post by mechro on 2009-11-28
System > Administration > Login Window... Local... Add

Edit: That's for 9.04, may not work in 9.10

---

### Post by mikeac72 on 2009-11-28
[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)
Does that help?

---

### Post by kyle2595 on 2009-11-28
In 9.10 the login screen settings are different. I included a picture of the window.  And to reply to "mikeac72", what si the "GDM" that it talks about.  Thanks!

---

### Post by mikeac72 on 2009-11-28
[http://projects.gnome.org/gdm/](http://projects.gnome.org/gdm/)

---

### Post by mikeac72 on 2009-11-28
[http://projects.gnome.org/gdm/](http://projects.gnome.org/gdm/)

EDIT: To "return to GDM" means to log out.

---

### Post by kyle2595 on 2009-11-28
OK, thank you, it worked wonderfully!

---

### Post by RJ12 on 2009-11-28
Yeah this is because the devs switched from GDM to the X server to improve boot time. So keep this in mind.:D

---

### Post by superotakuman on 2009-11-29
In case anybodys interested, I figured out how to simply change the background for the splash and login screen.

go to directory /usr/share/images/xsplash (you must login as root)
find image named bg_2560x1600.jpg
move this somewhere else for safekeeping
move the image you want as login background an this folder and rename bg_2560x1600.jpg
Give me props. my first finding on ubuntu. The first time around, I had to reinstall cause I crashed fiddlin around too much. THIS WORKS THOUGH AND ITS EASY! as for GDM, not sure yet.

---

### Post by StitchJAcket on 2010-01-16
> **superotakuman said:**
> In case anybodys interested, I figured out how to simply change the background for the splash and login screen.

go to directory /usr/share/images/xsplash (you must login as root)
find image named bg_2560x1600.jpg
move this somewhere else for safekeeping
move the image you want as login background an this folder and rename bg_2560x1600.jpg
Give me props. my first finding on ubuntu. The first time around, I had to reinstall cause I crashed fiddlin around too much. THIS WORKS THOUGH AND ITS EASY! as for GDM, not sure yet.

This worked great for me even stretched the photo to fit the screen resolution thanks for the tip!

---

### Post by etothex23 on 2010-03-19
> **superotakuman said:**
> In case anybodys interested, I figured out how to simply change the background for the splash and login screen.

go to directory /usr/share/images/xsplash (you must login as root)
find image named bg_2560x1600.jpg
move this somewhere else for safekeeping
move the image you want as login background an this folder and rename bg_2560x1600.jpg
Give me props. my first finding on ubuntu. The first time around, I had to reinstall cause I crashed fiddlin around too much. THIS WORKS THOUGH AND ITS EASY! as for GDM, not sure yet.

**I did this method and had no problems**

---

### Post by thelastquincy on 2010-04-19
> **etothex23 said:**
> **I did this method and had no problems**

Same here. Worked like a charm. Thanks man, I was really looking for something like this.

-quincy :)

---

### Post by rob22941 on 2010-04-19
> **superotakuman said:**
> In case anybodys interested, I figured out how to simply change the background for the splash and login screen.

go to directory /usr/share/images/xsplash (you must login as root)
find image named bg_2560x1600.jpg
move this somewhere else for safekeeping
move the image you want as login background an this folder and rename bg_2560x1600.jpg
Give me props. my first finding on ubuntu. The first time around, I had to reinstall cause I crashed fiddlin around too much. THIS WORKS THOUGH AND ITS EASY! as for GDM, not sure yet.

I used this method above however instead of logging in via root, which I've read may be unsafe for your system if you're not careful or not very experienced, I used the terminal.

[http://ubuntuforums.org/showthread.php?t=1316640](http://ubuntuforums.org/showthread.php?t=1316640)

I just changed the name of my image before hand and did basically as stated in the thread I listed a few lines up.

---

### Post by Timmer1240 on 2010-04-25
Heres what I do go to terminal enter this command gksudo -u gdm dbus-launch gnome-appearance-properties

---

### Post by towheedm on 2010-04-29
Interested in customizing gdm, then check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

