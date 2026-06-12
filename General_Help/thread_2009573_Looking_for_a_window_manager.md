---
title: "Looking for a window manager"
date: 2012-06-24
forum: General Help
---

### Post by J V on 2012-06-24
I need a window manager and so far I've struck out on compiz xfwm and openbox.


[LIST]
[*]Compiz yields performance issues in games (Specifically limiting games to less than *half* their previous framerate because it sends renders back from the GPU to the CPU and just messes things up)
[*]XFWM is bugged in such a way that running vlc (My video player of choice) with the compositor on results in tearing the likes of which no man has ever seen.
[*]Openbox seem(ed) to work fine with both but was a configuration hell.
[*]I don't want to use unity gnome3 or cinnamon so this leaves me with MATE but I don't particularly want to move to a new system (like mint) unless I have no other choice.
[/LIST]

Does anyone know where I can find a feature table of window managers?

Or better yet could someone suggest window managers that would meet my needs of:

[LIST]
[*]compositing (So ffmpeg x11grab will work)
[*]without impeding game framerate
[*]or tearing up vlc?
[/LIST]

---

### Post by robtygart on 2012-06-24
Have you looked at icewm?

---

### Post by J V on 2012-06-24
No, does it have compositing?

---

### Post by flipper T on 2012-06-24
read this

[http://en.wikipedia.org/wiki/Comparison_of_X_window_managers](http://en.wikipedia.org/wiki/Comparison_of_X_window_managers)

---

### Post by lykwydchykyn on 2012-06-24
I don't know anything about ffmpeg X11grab, but if you need compositing with a window manager that doesn't support it, there are a number of standalone compositors out there:

 - cairo-compmgr
 - xcompmgr
 - compton
 - unagi

If one of those works, you can use whatever Window manager suits you.

I wonder if you ought to look at video driver compatibility, though; what's your video hardware?

---

### Post by J V on 2012-06-24
An nvidia GTX 680... Yes I know I know :D

The main issue is that without compositing (Openbox for example) ffmpeg screengrab through x11grab (By far the best screencasting on linux btw) shows up torn to shreds. With compositing it's nice and clear.

My framerate in games is limited in compiz because it needs all the info back from the graphics card for the CPU to deal with - I get the same 100fps in amnesia at max settings as I do in a 7 year old game in wine (In which I get up to 1000fps without compiz)

And then I couldn't use xfwm4 because a bug in their compositing made vlc tear a ton and they aren't going to release a fix for it for years. Yay.

---

### Post by rai4shu2 on 2012-06-25
Do you get tearing in fullscreen or just windowed mode?

---

### Post by J V on 2012-06-25
In windowed mode it happens too

---

### Post by Jose Catre-Vandis on 2012-06-25
In xubuntu I just use a launcher switch to turn compositing on and off as needed (to overcome tearing)

[http://bimma.me.uk/2012/06/14/xubuntu-turn-compositor-on-and-off/](http://bimma.me.uk/2012/06/14/xubuntu-turn-compositor-on-and-off/)

The effects are hardly bleeding edge (e.g. no wobbly windows or spinning cubes) so I rarely have it on anyway

---

### Post by cortman on 2012-06-25
I've always been a big Openbox fan but recently I've been using [Awesome WM]("http://awesome.naquadah.org/") and am really impressed with it.

---

### Post by J V on 2012-06-25
A more in-depth look at icewm shows their preference program last got an update in 2004... I'd rather not have a WM that's 8 years old thanks.

Awesomewm doesn't seem like my style either.

I may have to just switch compositing off and on on xfwm4 after all but I'd much (MUCH) rather not have to.

---

### Post by rai4shu2 on 2012-06-25
There's a lot to like about openbox. Sure, it's a pain to configure but how often do you need to do that?

---

### Post by J V on 2012-06-25
It's lack of compositing also makes decent screencasting impossible (With x11grab)

---

### Post by cortman on 2012-06-25
> **J V said:**
> It's lack of compositing also makes decent screencasting impossible (With x11grab)

Use xcompmgr with openbox for compositing. Install obmenu, obconf, and lxappearance, and a complete novice could configure it with ease.

---

### Post by LewisTM on 2012-06-25
I'd suggest you install and run compiz-icon at login. That will let you quickly switch between Compiz for work and videos and Xfwm4 for games.

Cheers!

---

### Post by J V on 2012-06-25
> **cortman said:**
> Use xcompmgr with openbox for compositing. Install obmenu, obconf, and lxappearance, and a complete novice could configure it with ease.Last time I tried that it wouldn't start X (Back when I was using a "From scratch" cli > openbox setup)

> I'd suggest you install and run compiz-icon at login. That will let you  quickly switch between Compiz for work and videos and Xfwm4 for games.Might as well just use xfwm4 and enable/disable compositing (Which is what I've done for now)

---

### Post by cortman on 2012-06-25
> **J V said:**
> Last time I tried that it wouldn't start X (Back when I was using a "From scratch" cli > openbox setup)

Might as well just use xfwm4 and enable/disable compositing (Which is what I've done for now)

Never had xcompmgr mess up X yet- but then I've used it primarily with Fedora.

---

