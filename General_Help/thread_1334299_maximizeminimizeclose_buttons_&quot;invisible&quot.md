---
title: "maximize/minimize/close buttons &quot;invisible&quot;"
date: 2009-11-22
forum: General Help
---

### Post by Don Andi on 2009-11-22
Hey there,

I just replaced compiz with emerald so i can properly use a theme. but so I can keep the compiz effects I included in my starting programs:

emerald --replace
compiz --replace
emerald --replace

so everything works alright, but just in some programs I can't see the maximize, minimize and close buttons, I can click there and it puts an info box down when I'm above them with my mouse arrow and they appear if I maxmize the window but otherwise I just can't see them.

It's not a big problem tho, if it's not hard to fix, I'll do it but I can live without these buttons, too.

Regards

---

### Post by Portable_Jim on 2009-12-12
Try going to "System" >> "Preferences" >> "Emerald Display manager" and try changing the theme (if possible).

---

### Post by jl7030 on 2010-02-19
Hey. I had the same problem today but got it showing again by doing this. Go into System, Preferences, CompizConfig Settings Manager. Then go to Effects and tick the box Window Decorator. It should come back up...:)

---

### Post by SecretCode on 2010-02-19
I also have this problem with Emerald ... it seems to come back intermittently regardless of which theme I use and what options I toggle. 

Currently living with it ... one day will investigate further.

---

### Post by Sisco55 on 2010-08-14
I know this is an old thread. but I'm having this issue as well and I've looked everywhere for help but it seems that I can't find the solution. A real pain I say. Anyway, entering "emerald replace" like I'm enabling emerald fixes the problem temporarily, then the minimize, maximize etc. buttons go away, typically when I close the terminal. It's really annoying that there seems to be no answer. I know I screwed it up somehow but I don't know what I did or what to do to fix it. 

Any help would be appreciated.

---

### Post by Quackers on 2010-08-14
I've had this problem a number of times and have used various methods. The one which works every time nowadays only works because I have compiz displayed in my Cairo dock. If I hover the pointer over the compiz icon one of the options is  "reload WM". If I click on that it fixes the problem every time.
I realize it doesn't really answer your question, but for me it is a fix.
I think the Window Manager gets confused sometimes and that's what causes it.
Previously I could sometimes fix it by reloading the window manager through the terminal.

---

### Post by Sisco55 on 2010-08-15
Thanks for the reply. Yeah, I can't seem to find a fix. Right now it's not a huge issue because I just enter emerald --replace  into the console and then put it into another desktop.Even though this works it's still a little weird I have to do this. I'm sure there's some way to fix it, probably very simple, I just don't know what it is.

Cheers.

---

### Post by WorMzy on 2010-08-15
I have this problem if I have one of the halo options ticked for a theme, but not the other. (The options are in Theme Settings -> Edit Themes -> Buttons

I fix it by disabling or enabling both. In recent months I've been having a problem with VLC's window losing it's buttons after coming out of fullscreen mode, not sure how to prevent that.

---

### Post by Quackers on 2010-08-15
It does seem to be a bit of a lottery as to whether it happens or not. It doesn't seem to happen in any particular set of circumstances. For me sometimes just a reboot would fix it, other times I'd replace metacity. Now I can just click on Reload WM in Compiz and that works every time.

---

### Post by akshay.toraskar on 2011-01-03
i also have same problem 
to solve that problem just go to system>>preference>>compiz setting manager
then go to effect>>windows decoration and at place of command just put
compiz --replace
that done .....
it work for me:guitar:

---

