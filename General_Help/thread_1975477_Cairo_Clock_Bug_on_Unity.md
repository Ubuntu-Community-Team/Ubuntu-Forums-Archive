---
title: "Cairo Clock Bug on Unity?"
date: 2012-05-07
forum: General Help
---

### Post by wmichaelb on 2012-05-07
I'm running 12.04 with Unity on a test machine, and one of the things I'm fond of is an analog clock on the desktop. I've used Mac's Cairo Clock to good advantage, but if I put it into the Startup Applications folder, i get an over sized quarter circle and no hands. If I simply quit and restart the application, it works fine. The command shown is:

cairo-clock

and this is what I've entered into the startup application. I've also tried the full path:

/usr/bin/cairo-clock

in startup, but I get the same response. It's not the end of the world, but I'm curious if anyone else has seen this and it's some sort of startup bug in 12.04 Unity.

Thanks in advance for any light you can shed. :confused:

---

### Post by Cheesemill on 2012-05-07
It sounds like the clock is loading before the desktop is fully loaded. You can try waiting a few seconds before starting the clock by using:
```
sleep 3 && cairo-clock
```
as your command in startup

---

### Post by wmichaelb on 2012-05-09
Cheesemill: thanks for your prompt reply! The answer seems good, but Gnome startup doesn't seem to see the "3" part, only the "sleep". Cairo clock doesn't open at all now at bootup.

I first edited the Startup application for Cairo-clock, and inserted the command:

```
sleep 3 && cairo-clock
```I logged out and back in, but no clock. 

I then found ~/.config/autostartup/, but the link there was to cairo-clock.desktop. So I opened cairo-clock.desktop with sudo gedit and found that the "3" was missing. I added that number, saved the file, and logged out and back in. But still no clock. 

So I'm still missing something but not sure what.

Nonetheless, I appreciate your suggestion. If I figure this one out, I'll repost.

---

