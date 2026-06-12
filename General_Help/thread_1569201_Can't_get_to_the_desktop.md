---
title: "Can't get to the desktop"
date: 2010-09-06
forum: General Help
---

### Post by fibrebiz on 2010-09-06
After selecting ubuntu (I am using Lucid) from GRUB2 (I share the hard drive with winXP and a windows recovery partition) I am presented with the purple ubuntu splash screen. 
That purple splash screen will stay like that forever, with the system not appearing to be doing anything

Ctrl alt f2 brings up a console which I can then use to execute commands but ctrl alt f7 only brings me back to the same splash screen.

When I try startx, I get the response
Fatal server error:
Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock
 and start again.

yet the display command won't work

the package xserver-xorg is installed, so I've clearly done something to it I shouldn't have. 

Everything was working until I tried to change the splash screen using system > preferences > splash screen

What have I done and how do I get my beloved desktop back?

---

### Post by howefield on 2010-09-06
> **fibrebiz said:**
> Everything was working until I tried to change the splash screen using system > preferences > splash screen

Can you clarify this bit.., "system > preferences > splash screen"

Were you following a tutorial or howto, which one ?

---

### Post by fibrebiz on 2010-09-06
gnome-splashscreen-manager is what I used to get that option

The guide is from here:
[https://help.ubuntu.com/community/UbuntuEyeCandy#Changing%20the%20Gnome%20Splash%20Screen](https://help.ubuntu.com/community/UbuntuEyeCandy#Changing%20the%20Gnome%20Splash%20Screen)

---

### Post by howefield on 2010-09-06
> **fibrebiz said:**
> The guide is from here:
[https://help.ubuntu.com/community/UbuntuEyeCandy#Changing%20the%20Gnome%20Splash%20Screen](https://help.ubuntu.com/community/UbuntuEyeCandy#Changing%20the%20Gnome%20Splash%20Screen)

I'm not comfortable with giving advice on a tutorial so old, given that you are using 10.04.

But if it were me, I'd log into the console (Ctrl + Alt + F1) and purge gnome-splashscreen-manager from the system.

```
sudo apt-get purge gnome-splashscreen-manager
```

---

### Post by fibrebiz on 2010-09-06
Unfortunately that didn't improve things.

Any other suggestions?

---

### Post by udito on 2010-09-06
looks like you are having the same issue as I have...

I could resolve it (temporarily) doing this: [http://ubuntuforums.org/showpost.php?p=9809946&postcount=11](http://ubuntuforums.org/showpost.php?p=9809946&postcount=11)

unfortunately not a permanent fix... still struggeling for one...

---

### Post by fibrebiz on 2010-09-06
That didn't resolve the issue unfortunately.

After entering **sudo stop gdm **the console closed automatically, 
sending me to the same splash screen but giving me a black X which acted as a cursor (not that it could do anything)

I went back into the console via ctrl alt f2 and tried **startx** but got the same error as described in my first post.

---

### Post by fibrebiz on 2010-09-06
Resolved.

I used the command:

sudo init 4

then I used

sudo /sbin/init 4

Then 
startx

I'm not quite sure what they do but now I can use my ubuntu properly again.
:D

---

