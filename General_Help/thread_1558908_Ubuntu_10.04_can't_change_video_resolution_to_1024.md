---
title: "Ubuntu 10.04 can't change video resolution to 1024x768"
date: 2010-08-22
forum: General Help
---

### Post by sycho sid on 2010-08-22
Hi everyone,
                           

I can't change the video resolution for[SIZE=4] **Intel 82740 (i740)**[/SIZE] video card.



I'm new to Ubuntu 10.04, as I've just installed it and I have a problem with video settings.
I can't change video resolution for my video adapter.  I can only choose between 800x600, 640x480, 400x300... not 1024x768 for example.
 

 

 No restricted or proprietary drivers...


I used Knoppix 5.1.1 Live CD and it automatically set the resolution to 1024x768.

I also used Puppy linux 5.1 Live CD and it had a configuration program which also utilised 1024x768.

If these versions of linux can utilise the 1024x768 resolution, why can't Ubuntu 10.04

---

### Post by grief -l on 2010-08-22
I had the same problem but a perusal of /var/logs/ showed it complaining about vertical refresh rate. I edited my /xorg/config file and set the refresh rate about 10  points lower on the low end and higher on the high end and now have 1024x768

---

### Post by sycho sid on 2010-08-22
I cannot locate the xorg conf files, can you tell me where they are located at.

I have also read other threads stating the same thing, but I think that Ubuntu 10.04

does not use conf. files.

---

### Post by grief -l on 2010-08-23
create an xorg.conf file with   

```
sudo Xorg -configure
``` edit it with 

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by LowSky on 2010-08-23
Edit it with ```
sudo gedit /etc/X11/xorg.conf
```

The X in X11 has to be capitalized or it you will have a blank page.

---

### Post by grief -l on 2010-08-23
> **LowSky said:**
> Edit it with ```
sudo gedit /etc/X11/xorg.conf
```The X in X11 has to be capitalized or it you will have a blank page.

Thanks for catching that LowSky, much appreciated!

---

### Post by LowSky on 2010-08-23
You welcome, glad to help.

---

### Post by sycho sid on 2010-08-23
Once I create:  /etc/X11/xorg.conf   what do I put in it...

---

### Post by sycho sid on 2010-08-23
After trying to create the this is what I got:


sudo Xorg -configure
[sudo] password for sid: 

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by realzippy on 2010-08-23
You have to close "X" first.Open a terminal,type: 
 
```
sudo service gdm stop
```

press alt+ctrl+F2,log in
at the shell,then run your command.

---

