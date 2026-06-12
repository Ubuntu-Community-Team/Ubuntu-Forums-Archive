---
title: "Monitor out of range"
date: 2009-09-14
forum: General Help
---

### Post by knottshawk on 2009-09-14
I've been using a 17" lcd with a vga connection... I got a new monitor today and am now using a 19" lcd with a DVI connection... when I first start up it says "Starting up..." and that's the last thing I see.

I hear the ubuntu startup drums and then the monitor says "Out of range" "H.Frequency 64.9KHz V.Frequency 60.0Hz"

If I hit ctrl+alt+F2, I can login but the bottom of the screen is off the monitor by a lot. I tried "sudo dpkg-reconfigure xserver-xorg" but, again, I couldn't see what I was doing since it was cutting most of the screen off...

What do I do? Please bear in mind that I'm a novice, so be specific. :)

---

### Post by Woody1987 on 2009-09-15
graphics card and driver?

---

### Post by P4man on 2009-09-15
Your monitor should have an "auto" button that i guess will cure the terminal being "off screen".

Then try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Altough to be honest, x should detect the new monitor and resolution without typing that, so Im not sure it will help much. you might have to edit your xorg.conf manually if the monitor is not detected properly.

---

### Post by Tux+ on 2009-09-15
I have found it can be the graphics card not detecting the monitor correctly. Try using VGA port instead of DVI (requires a reboot I think). Another option is to try a different graphics card

---

### Post by aleazerreilly on 2009-09-15
I want to purchase a LCD 17" inch. With Speaker. Please help Me.

---

### Post by knottshawk on 2009-09-15
Okay, I fixed it... here's how: 

It's stupidly simple, but I hooked up a different monitor and set the resolution to 800x600, then hooked up the new monitor and set the appropriate final resolution. I think the problem was that I had been using a 17" 4:3 and my new monitor is a 19" 16:9... it didn't like resolution setting for the 17".

Anyway, it's all happy now. Thanks for bearing with me...

---

