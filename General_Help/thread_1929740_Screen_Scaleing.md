---
title: "Screen Scaleing"
date: 2012-02-22
forum: General Help
---

### Post by Inotamira on 2012-02-22
I'm trying to figure out how to get ubuntu 11.10 to scale windows to the  native screen instead of just displaying the windows resolution as is  making it in a box with nothing else around it. Perhaps I'm just being a  noob and this is a simple thing to do, but i honestly can't figure out how to  do it. In windows it was a simple driver manager or a setting somewhere  in the display settings.

---

### Post by Inotamira on 2012-02-23
Bump, i really want to know, and yes i've googled and searched the forums for the answer, I can't find an answer, any thoughts on the matter would be great

---

### Post by Grenage on 2012-02-23
Hi there.

I'm a little unsure what your problem is; do you have a display surrounded by a black border?  Is the visible display blurry or otherwise distorted?

---

### Post by Inotamira on 2012-02-23
Yes and no, the problem is when an application of any kind that has a lower resolution then the native screen, or even changed under it out right, instead of scaling the application or desktop to fit the native screen, Ubuntu will simply display it as is causing it to box the display and make a black "border" (more like two rectangles on either side). This annoys me as i prefer a scaled or stretched image fitting my whole screen instead of a boxed image keeping the resolution

---

### Post by Grenage on 2012-02-23
> **Inotamira said:**
> Yes and no, the problem is when an application of any kind that has a lower resolution then the native screen, or even changed under it out right, instead of scaling the application or desktop to fit the native screen, Ubuntu will simply display it as is causing it to box the display and make a black "border" (more like two rectangles on either side). This annoys me as i prefer a scaled or stretched image fitting my whole screen instead of a boxed image keeping the resolution

Forgive me; I'm probably just being obtuse, but I'm still unsure of exactly what's happening.

Is the default display (no applications open) the incorrect size or resolution?
When you open an application, does the resolution or screen size change?

---

### Post by Inotamira on 2012-02-23
No, when nothings open, the screen size is correct unless i change the resolution below the native (default) resolution. When i open an application, naturally, it goes below it and creates a black bar, what i want to do is make these windows that are below the native resolution, stretch to fit the whole screen

---

### Post by Grenage on 2012-02-23
Ah I see, so if you were to load a game, for example, it would display a 4:3 resolution on a widescreen monitor?  These kind of settings are normally controlled from within the application that is being run; is that not the case here?

---

### Post by Inotamira on 2012-02-23
Correct, and as far as i can tell no, wine doesn't seem to have a setting to scale a program/game that's full screen and the games built for Linux that do this are slightly old and may not have that function built in, in windows the driver for the graphics card dealt with scaling, is that not the same for ubuntu, or is that something that needs to be setup using the terminal and some config file?

---

### Post by 3rdalbum on 2012-02-23
> **Inotamira said:**
> Correct, and as far as i can tell no, wine doesn't seem to have a setting to scale a program/game that's full screen and the games built for Linux that do this are slightly old and may not have that function built in, in windows the driver for the graphics card dealt with scaling, is that not the same for ubuntu, or is that something that needs to be setup using the terminal and some config file?

Normally the monitor should do the scaling. It looks like it isn't though for some reason. Is there a setting in your monitor that is causing it to not scale?

---

### Post by Inotamira on 2012-02-23
it's an Intel® Sandybridge Mobile, a chipset that came with my dell inspiron N4110, even in windows i had to jump through a few hoops to get it to scale anything under the native resolution, by default the graphics card doesn't scale programs or images, it has to be told to by a driver, it even has to be told what aspect ratios to scale. In windows under the graphics driver I had to tell it to scale every aspect ratio under the native aspect ratio individually before it would do it.

---

### Post by Inotamira on 2012-02-23
I've been digging around looking at problems with my graphics card in particular, turns out that the sandy bridge architecture as a general rule is terribly wobbly with Ubuntu and the fact I have a working display is something of a miracle. Apparently alot of the work arounds for specific problems deals with the x.org files and I'm only a moderate ubutnu user. I'd go mucking about in the configuration files and what not but every time I have, I've destroyed my OS almost every time (not enough that i couldn't retrieve my files, but bad enough i couldn't repair it)

---

