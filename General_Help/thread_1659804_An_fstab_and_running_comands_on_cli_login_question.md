---
title: "An fstab and running comands on cli login question"
date: 2011-01-04
forum: General Help
---

### Post by flammenwurfer on 2011-01-04
Hopefully these will be easy to answer questions for somebody.

First, I have an external hdd hooked up with usb that has an entry in fstab using UUID that mounts perfectly and everything is great.  I now have an esata port available and want to start using that instead of usb.  With UUIDs can I just shutdown the computer and hdd, switch cables and turn it all back on?  Will the UUID stay the same and will it mount just like before?

Second, I have disable gdm/gnome and boot to a command line to run boxee without a desktop environment running in the background.  For sound to work I need to run "pulseaudio --start" as user.  Then I have small script that is supposed to facilitate starting boxee and restarting it in case it crashes.  What is the best way to go about that?  Can I include all of that in my .xsession file?  How also can I get that stuff to run when I login?

---

### Post by seawolf167 on 2011-01-04
> **flammenwurfer said:**
> 
First, I have an external hdd hooked up with usb that has an entry in fstab using UUID that mounts perfectly and everything is great.  I now have an esata port available and want to start using that instead of usb.  With UUIDs can I just shutdown the computer and hdd, switch cables and turn it all back on?  Will the UUID stay the same and will it mount just like before?


UUIDs are unique to that particular piece of hardware, there are something like 3x10^38 different unique combination so removing and replugging with a different connection should encounter no problems unless the other entries have changed (i.e. drive format [ext3, ntfs, etc.)

> **flammenwurfer said:**
> 
Second, I have disable gdm/gnome and boot to a command line to run boxee without a desktop environment running in the background.  For sound to work I need to run "pulseaudio --start" as user.  Then I have small script that is supposed to facilitate starting boxee and restarting it in case it crashes.  What is the best way to go about that?  Can I include all of that in my .xsession file?  How also can I get that stuff to run when I login?

I wouldn't be the best person to answer this, but what I'd do it create a script (.sh file), make it executable, then place it in init.d to run upon startup

EDIT: [UbuntuBootupHowto Link]("https://help.ubuntu.com/community/UbuntuBootupHowto")

For a script running on login, I believe you want it in the .bashrc file ([.bashrc config info]("http://heimhardt.com/htdocs/bashrcs.html"))

---

### Post by QLee on 2011-01-04
UUIDs are set at the time the partition is formatted, it is persistent until the next format of that partition.

---

### Post by flammenwurfer on 2011-01-05
Great, thanks for the help guys.  I don't know why, but the hard drive thing still makes me nervous.  I will shutdown and switch cables and cross my fingers.  Thanks again!

---

