---
title: "make a program start on boot up!"
date: 2010-12-06
forum: General Help
---

### Post by sale666 on 2010-12-06
Hello i have installed the galaxy wallpaper that i find really cool but i allways have to alt+f4 it to start can i make it auto start?
if so could some 1 explain how? thanks =)

---

### Post by lrgmmc on 2010-12-06
to set an app for autorun add it to system-->Preferances---> startup aplications

---

### Post by sale666 on 2010-12-06
Ok thank you however i dont think this is an application is it? its more like a plugin? will this work? what should i do here?

---

### Post by akand074 on 2010-12-06
A wallpaper? Can't you just go to System > Preferences > Appearance and go to the wallpaper tab and just add it. I've had similar wallpapers in the past they don't require anything to cause them to run? Otherwise it's not so much a wallpaper.

---

### Post by sale666 on 2010-12-06
yes well that ermmm inst an wallpaper its a live wallpaper however it goes over any wallpaper you tube galaxy wallpaper ubuntu you will get the point i like it its kind of relaxing XD.. but when i restart it just doesnt want to start automaticly! i need to press alt+f4 to start it manualy! 

Thank you!

---

### Post by bodhi.zazen on 2010-12-06
> **sale666 said:**
> yes well that ermmm inst an wallpaper its a live wallpaper however it goes over any wallpaper you tube galaxy wallpaper ubuntu you will get the point i like it its kind of relaxing XD.. but when i restart it just doesnt want to start automaticly! i need to press alt+f4 to start it manualy! 

Thank you!

What code do you put when you launch the 'wallpaper' with f4 ?

Use the same code on a custom launcher.

---

### Post by cgroza on 2010-12-06
I am just going to take a bean.

---

### Post by sale666 on 2010-12-06
im sorry if i sound stupid but im not very experienced im still learning i do have some knowledge i user super+f4 so how am i exactly making a launcher on this? could you be a little bit more speciffic? sorry if this is a waste of time but it is usefull knowledge to me as i will use this later on! 
Thank you!

---

### Post by sisco311 on 2010-12-06
*Galaxy Wallpaper* is a Compiz plugin. I don't use Compiz, so I'm not sure how to autostart it. Check out the settings in System -> Preferences -> CompizConfig Settings Manager.

---

### Post by bodhi.zazen on 2010-12-06
> **sale666 said:**
> im sorry if i sound stupid but im not very experienced im still learning i do have some knowledge i user super+f4 so how am i exactly making a launcher on this? could you be a little bit more speciffic? sorry if this is a waste of time but it is usefull knowledge to me as i will use this later on! 
Thank you!

No problem, it is easy

[http://www.liberiangeek.net/2010/09/create-custom-application-command-ubuntu-main-menu-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/create-custom-application-command-ubuntu-main-menu-ubuntu-10-10-maverick-meerkat/)

Under preferences, look for the "startup" option

Add a your command to a custom startup =)

[img]http://www.somethingkindawierd.com/blog/wp-content/uploads/2010/05/Selection_001.png[/img]

---

### Post by sale666 on 2010-12-06
thank you both! 
Bodhi that helps a lot however here is where i do not know what to write in as that is a compiz plugin and its confuzing what do you suggest i try? have you ever tryed to make a compiz plugin auto start?

Thank you for your time!

---

### Post by sisco311 on 2010-12-06
I guess, you could use dbus-send:
[http://wiki.compiz.org/Plugins/Dbus](http://wiki.compiz.org/Plugins/Dbus)

---

### Post by bodhi.zazen on 2010-12-06
> **sale666 said:**
> thank you both! 
Bodhi that helps a lot however here is where i do not know what to write in as that is a compiz plugin and its confuzing what do you suggest i try? have you ever tryed to make a compiz plugin auto start?

Thank you for your time!

What do you type when you hit f4 ? put the same thing in the custom start , in the "command" box.

Probably an easier way, but no I do not use compiz. You may wish to look through the compiz options.

---

### Post by bodhi.zazen on 2010-12-06
Here is a walk-through:

[http://n00bsonubuntu.net/content/install-galaxy-live-wallpaper-compiz-plugin-ubuntu-1010-maverick-meerkat](http://n00bsonubuntu.net/content/install-galaxy-live-wallpaper-compiz-plugin-ubuntu-1010-maverick-meerkat)

look on the bottom of the page.

It appears it is activated / deactivated via F4, not sure what command that is running exactly.

---

### Post by dpiddyTx on 2010-12-29
bump

---

