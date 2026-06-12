---
title: "Same interface at ubuntu 11.04 like 10.10 why ?"
date: 2011-08-29
forum: General Help
---

### Post by Ayzenlawl on 2011-08-29
Hello. I just instaled Ubuntu 10.10 and then i upgrade it tu 11.04 but i got the same interface why ? Look this picture :
[[IMG]http://img51.imageshack.us/img51/2457/screenshotaur.png[/IMG]]("http://imageshack.us/photo/my-images/51/screenshotaur.png/")
IDK why On my laptop i got that Luncher bar and all the new stuffs but on my dekstop pc i don't have Idk why please help me 
And i Instaled ubuntu cuz i got a keylogger in windows - Will the keylogger still work in ubuntu ?

---

### Post by Vaphell on 2011-08-29
at the login screen, after selecting your user, but before providing a password expand the dropdown that should appear on the bottom bar. What options do you see? Gnome2 interface you have is under Ubuntu Classic, is there any other option?

Another question - what is your gfx card? If i remember correctly, if you have no accelerated 3d required by unity interface, you get the fallback mode of gnome2.

and no, keylogger installed in windows won't work in linux.

---

### Post by Ayzenlawl on 2011-08-29
Well when i log on i see Ubuntu , ubuntu Classic . Ubuntu recovery and more , now i'm using ubuntu and still the same and i think i have Nvidia 1gb geforce 210 i guess but idk why can i see it
And i remeber something abut 3d graphics when i instaled the 11.04  but i didn;t read it and press yes :D

---

### Post by Vaphell on 2011-08-29
run jockey-gtk in terminal (it's the same as 'Hardware drivers' or whatever it's called in menus) and check the state of affairs with the nvidia driver

also run
```
sudo apt-get install mesa-utils
glxinfo | grep direct

```
if you get the following line in the output
```
direct rendering: Yes
``` then you have hardware acceleration enabled and everything should be fine

---

