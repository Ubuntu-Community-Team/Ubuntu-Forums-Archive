---
title: "Volume Control Missing from Panel"
date: 2010-05-12
forum: General Help
---

### Post by UUU1 on 2010-05-12
I just want to  point out I tried reseting my panel several times at which point it did  reset everything except the volume control is still missing. Everything  else is there.
 
I followed what was said here:
[http://ubuntuforums.org/showthread.php?p=9257307](http://ubuntuforums.org/showthread.php?p=9257307)

yes the volume control icon is still missing. I have no idea why it's  not showing up for me. For the love of god please help.

---

### Post by nothingspecial on 2010-05-12
Right click on the panel and add it back.

---

### Post by r_s on 2010-05-12
On the panel ,right click and then select add to panel, in the list select notification Area and then add it to panel.

---

### Post by UUU1 on 2010-05-12
> **r_s said:**
> On the panel ,right click and then select add to panel, in the list select notification Area and then add it to panel.

When I do this all I get is that funky = looking thing
[IMG]http://i934.photobucket.com/albums/ad182/UUU1/Screenshot.png[/IMG]

---

### Post by r_s on 2010-05-12
Because you already have one notification are activated, remove it and then try again.

---

### Post by UUU1 on 2010-05-12
> **r_s said:**
> Because you already have one notification are activated, remove it and then try again.
[IMG]http://i934.photobucket.com/albums/ad182/UUU1/Screenshot-1.png[/IMG]

---

### Post by r_s on 2010-05-12
Why don't you just change  the panel settings back to its default settings.
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by UUU1 on 2010-05-12
> **r_s said:**
> Why don't you just change  the panel settings back to its default settings.
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)
[IMG]http://i934.photobucket.com/albums/ad182/UUU1/Screenshot-2.png[/IMG]

---

### Post by r_s on 2010-05-12
Well just found out that lucid does not show the volume icon in notification area, well I'm still using karmic.
why don't you try this out and then report what happened.
[http://swiss.ubuntuforums.org/showthread.php?t=1436043](http://swiss.ubuntuforums.org/showthread.php?t=1436043)

---

### Post by Calash on 2010-05-12
Try removing and adding the Indicator Applet to the panel.  During upgrades from 9.10 I have noticed it holds on to some odd settings.

You are also missing the -ME menu.  Remove and add the Indicator Applet Session to the panel and it should clear that up as well.


If that does not work try the following

For sound:
```

sudo apt-get install indicator-sound

```

For -Me menu
```

sudo apt-get install indicator-me

```

---

### Post by UUU1 on 2010-05-12
> **Calash said:**
> Try removing and adding the Indicator Applet to the panel.  During upgrades from 9.10 I have noticed it holds on to some odd settings.

You are also missing the -ME menu.  Remove and add the Indicator Applet Session to the panel and it should clear that up as well.


If that does not work try the following

For sound:
```

sudo apt-get install indicator-sound

```For -Me menu
```

sudo apt-get install indicator-me

```
the sudo install sound indicator brought up the blue one. i decided to try and add another indicator applet for the hell of it and it seems to have brought it up!
[IMG]http://i934.photobucket.com/albums/ad182/UUU1/Screenshot-3.png[/IMG]

---

### Post by Calash on 2010-05-12
Click on each.  The default Lucid one will have the bar going horizontal, while the older one will have the bar vertical.

My instructions will get you the newer one.  If you want the older one you can uninstall the indicator-sounds app and then add gnome-volume-control-applet to your startup applications.

---

