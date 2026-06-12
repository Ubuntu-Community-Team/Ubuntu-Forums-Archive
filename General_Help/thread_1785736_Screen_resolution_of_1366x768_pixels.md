---
title: "Screen resolution of 1366x768 pixels"
date: 2011-06-18
forum: General Help
---

### Post by Marzata on 2011-06-18
Brand new laptop Lenovo G570 with 

Intel Integrated HD Graphics 3000, 15.6", 1366x768. 

can't detect the correct resolution with Ubuntu 10.04.2 LTS. 

Any idea how to fix this? 
Thank you!

---

### Post by inameiname on 2011-06-18
Sometimes it won't. At least what I've noticed. Other times, if you happen to have it hooked up to more than one monitor, it will only give you the one resolution for the lowest quality monitor. That's an easy fix by unchecking the dual monitor option.

Anyway, I think its possible to force it to a certain resolution, whether your computer/monitor is capable of it or not, using Xrandr or something. I had to use that to force dual monitors out to TV sometimes. Sadly, I don't know how to do that for you.

Here is sort of how my dual monitors one changes the resolution. Maybe tweaking it some or something, IDK:
```

xrandr --addmode LCD 1366x768
xrandr --output LCD --mode 1366x768

```UPDATE:

Check this thread out. Might help you do the trick as the poster seems to have a similar issue as you:

[http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha](http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha)

---

### Post by Marzata on 2011-06-18
Linux Mint 10 (Julia) (with Gnome) detects the correct resolution. Any idea what to copy from Mint to Ubuntu installation in order to make it work?

---

### Post by inameiname on 2011-06-18
I don't really know. I've never used Mint. Why not just ask the Mint folks? Unlike in Windows, you can actually get a hold of, and possibly contribute to, the people who make the packages/distros.

---

### Post by Marzata on 2011-06-18
Thank you! I installed Ubuntu 11.04 (natty) and it works fine with resolution 1366x768. Thank you again!

---

### Post by inameiname on 2011-06-19
I'll take the accolade, but I am not sure what I really did. hehe. Was that other similar thread helpful for you to figure the issue out, or did you end up contacting Linux Mint folks?


UPDATE:

Oh...I reread your first posting and saw you were using Lucid. Yeah, often with newer, higher resolutions, its best to go with the latest version of a distro because it might support such. Anyway, glad it works on Natty for ya.

---

### Post by Marzata on 2011-06-20
In general I prefer to run a LTS release but for now I will stick to the normal one as it works out of the box. Thank you so much for your ideas and time!

---

### Post by inameiname on 2011-06-20
Understandable. Well glad to help.

---

### Post by tealio on 2012-12-26
i know it's an old thread, but i just had the same issue with a g570... upgraded to 12.04 from 10.04 and it works just fine now...

---

