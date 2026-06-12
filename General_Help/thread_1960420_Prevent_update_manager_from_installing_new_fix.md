---
title: "Prevent update manager from installing new fix"
date: 2012-04-17
forum: General Help
---

### Post by Benchrest on 2012-04-17
I have a machine that will not show Flash movie's and games with 11.2 version of Flash. I fixed it with some help by installing the older Flash 11.1. 
My problem is that update Manager shows there is a new version of 11.2 to install.  Is there a way to mark that update so I am not notified of it? for one thing I can't tell if I have new fixes or if the little orange sun is just for Flash. and sooner or later I am going to get distracted and install it and then have to reinstall 11.1. 

So I need a way to mark a product "do not install" so Update manager ignores it.

---

### Post by jadtech on 2012-04-17
the problem with that  in my experience is  that version of flash will stop working and yo will need to update in the end once the games and video games up-date to keep up with flash ..

im sure there is a way to prevent the update most like change the permissions or something ..

---

### Post by wallaroo on 2012-04-17
You can freeze a version by running 'Synaptic Package Manager', highlight the required package and then select the 'Package' drop-down menu and click on 'Lock Version'.

You will still see the updates listed in 'Update Manager' but they will be greyed-out (disabled) until you unlock it.

---

### Post by lovinglinux on 2012-04-19
The problem is the place where you put the *libflashplayer.so*.

Follow this tutorial on how to downgrade and you won't need to worry about the updates:

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

