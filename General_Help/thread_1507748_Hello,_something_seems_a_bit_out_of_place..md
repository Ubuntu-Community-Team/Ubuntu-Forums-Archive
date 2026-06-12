---
title: "Hello, something seems a bit out of place."
date: 2010-06-12
forum: General Help
---

### Post by ironhoof on 2010-06-12
Hello I am new here, I switched to Linux like a few weeks ago and
I am fine and everything is good love it. However:

I got my dad to switch from windows on his new laptop and installed Ubuntu and everything works 100% right from the start.

I ran an update for him since he didn't update in about a week and a half. Everything was fine then we was adjusting his panel for him and sudden the gnome-menu vanished off the panel.

Well I restarted his computer and it was still gone. I added one in its place and restarted. This is where it gets a bit strange.

It boots up to his desktop normal logs in and then it shows his desktop and mouse cursor and his wireless goes online. Then it hangs for a long time - AFTER the "your connected to <so and such> wireless network" bubble goes away. It takes an additional 20 seconds for the panels to finally slide down.

It used to go right from log in to the desktop and panels then a little bit after the wireless would connect.

Everything is working fine but it WAS booting up much faster than that.

Is this something I can fix? 

I am very familiar with the CLI and 80% of its commands already
so I am not afraid to jump in and try to fix it. I just need a pointer or two to get a clue of whats going on. Plus I wonder just because the gnome-menu went away its probably still in the startup. Its just not showing up in the panel and its likely still in the startup configuration. I am a hobby programmer so I can kinda imagine that being a likely possibility.

I really appreciate the input!  

Thanks :p

---

### Post by chayzer on 2010-06-12
You can check dmesg in a terminal for some more info maybe.

I also like to go to ctrl+alt+F1 and run```
tail -f /var/log/syslog
``` too.

Might give you some idea of what's going on.

---

### Post by ironhoof on 2010-06-12
I'll give it a try in the morning since its with him, thanks! :)

---

