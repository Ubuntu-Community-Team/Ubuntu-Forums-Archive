---
title: "Missing features after upgrading"
date: 2012-04-28
forum: General Help
---

### Post by x371322 on 2012-04-28
I just upgraded to 12.04, directly from 11.10, and there seem to be a couple of missing features. I've Googled a bit but I can't seem to find much help.

First of all I'm missing the new video lens. 
Also the login background doesn't change to match the user wallpaper when I scroll through them. It just stays the default. I can change it with Ubuntu tweak, but that's it. 

I also don't have any login sounds for some reason. 

Thanks.

---

### Post by x371322 on 2012-04-28
No ideas?

After some tinkering in Ubuntu Tweak I've managed to get the login backgrounds to change. Still no video lens or login sounds though.

---

### Post by Frogs Hair on 2012-04-28
Try the following in the terminal . ```
sudo apt-get install unity-lens-video
```

---

### Post by grahammechanical on 2012-04-28
You do not have login sounds because that feature has been removed. The intention is not to slowdown the loading of the desktop.

The login screen background will match the static wallpaper chosen in System Settings>Appearance. If we chose the slide show than we get the default background.

Regards.

---

### Post by x371322 on 2012-04-29
Thanks guys for your help. 

Any idea about this though? Whenever my machine awakes from sleep I get a repeating message that says something about it being "unable to register watchdog device". I'm on a Lenovo x220. The message repeats once each time it comes out of suspension. It resets and starts over after restarting, and it doesn't seem to affect anything. I was just wondering what it's all about.

---

