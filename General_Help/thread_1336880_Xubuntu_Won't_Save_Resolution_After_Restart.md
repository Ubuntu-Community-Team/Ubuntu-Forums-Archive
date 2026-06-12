---
title: "Xubuntu Won't Save Resolution After Restart"
date: 2009-11-24
forum: General Help
---

### Post by terrorhawk on 2009-11-24
Can anyone help me out with this issue?

I have an older model computer that I just switched on which I now run Xubuntu. I'm liking it so far, and getting used to it.

I ran all the updates, and that went fine... until I restarted.

Every time I shut the computer down or restart it, Xubuntu won't remember the resolution settings. I have it set to 1280x1024, and then if I shut it down, it goes back to 1024x768.

Anyone know how I can fix this? Thanks.

---

### Post by raktarok on 2009-11-25
Hi there,

I have not used XFCE for a long time now, and I don't think what I am suggesting is the standard way to solve the problem, but this should work.

I am assuming that you are changing resolution from the graphical tool bundled with xfce, and after changing the res, it doesn't stick after you login again right?

Open the startup applications tool (I forget the exact name) and add this in the list
   ```
xrandr -s 1024x768
```

This will ensure that once xfce starts, the resolution will always change to the specified one. You can try running the command from the terminal to test it - it merely changes the resolution.

Hope this helps!

---

### Post by etnlIcarus on 2009-11-25
raktarok is pretty much on the money. I had this problem with the beta and first 4.6 release of Xfce. You want to go to Settings>Sessions and Startup>Application Autostart>Add.

Call the startup entry something like xrandr, don't worry about a description and add the following to the command entry box:
```
xrandr -s 1280x1024
```
Click Ok and the next time you start Xfce, that command will run, correcting the screen resolution.

It may have something to do with xfconfd not starting properly or crashing during shutdown and thus failing to write your configuration to file.

I'm still using Jaunty but I'm using an updated Xfce 4.6.1 from this repo:
```
deb http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu jaunty main
```
Which you can add, using, "Software Sources". That may fix the problem; it did for me.

---

### Post by terrorhawk on 2009-11-25
Thanks guys. I'm not at home right now, but I made sure to check back here for replies. I'll definitely try that when I get back home. I'll reply back with either a fail or success story.

Appreciated!

---

### Post by terrorhawk on 2009-11-25
> **etnlIcarus said:**
> raktarok is pretty much on the money. I had this problem with the beta and first 4.6 release of Xfce. You want to go to Settings>Sessions and Startup>Application Autostart>Add.

Call the startup entry something like xrandr, don't worry about a description and add the following to the command entry box:
```
xrandr -s 1280x1024
```
Click Ok and the next time you start Xfce, that command will run, correcting the screen resolution.

It may have something to do with xfconfd not starting properly or crashing during shutdown and thus failing to write your configuration to file.

I'm still using Jaunty but I'm using an updated Xfce 4.6.1 from this repo:
```
deb http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu jaunty main
```
Which you can add, using, "Software Sources". That may fix the problem; it did for me.


Thanks. I'm going to restart, but before I do I need to find out how you get the key for that repository add? I hit "Reload" (cause sometimes repo adds don't need keys) but this one did...

Any suggestions?

---

### Post by etnlIcarus on 2009-11-25
I have no idea if that PPA has a GnuPG key. I certainly don't have it; I never bother with the keys. I just put up with a half-dozen consolidated nags every time I update my package cache. :P

---

### Post by raktarok on 2009-11-25
You can do a google search for the ppa, go to its page and follow the step by step instructions there to get the key.

Or just use the perl script I have attached here (I had to zip it, as I could not upload the .pl file directly)
Execute it like this:
```
perl launchpad-ppa-fix.pl
```
It will search for the missing keys from all your software sources, and saves you from all the hassle.

---

