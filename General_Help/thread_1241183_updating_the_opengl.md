---
title: "updating the opengl"
date: 2009-08-15
forum: General Help
---

### Post by rutrider on 2009-08-15
I want to update the opengl but I don't know how...

I couldn't find anything in the documentation on how to actually update it... So I'm posting here to find help...

Computer: Compaq
Ubuntu: 9.04 (Jaunty Jackalope)
Graphics card when it was Windows: Intel 845g

---

### Post by CatKiller on 2009-08-16
I have no idea what you mean by "updating the opengl."

> **rutrider said:**
>  Graphics card when it was Windows: Intel 845g

Unless you've changed the graphics card, that's still your graphics card.

There is a performance regression for Intel graphics with Jaunty. Some users have chosen to use the previous version, Intrepid, instead, and some users have chosen to install an experimental kernel to fix it. I don't use Intel graphics, so I don't know if there's another way.

---

### Post by rutrider on 2009-08-17
>  	
I have no idea what you mean by "updating the opengl."


As in making it 3.4 instead of 1.3... that's either called 'updating' or 'upgrading'

---

### Post by rutrider on 2009-08-17
Is there anyone that can help me? Or am I just going to have to do without the things I need for my job?

---

### Post by BinaryFeast on 2009-08-17
> **rutrider said:**
> As in making it 3.4 instead of 1.3... that's either called 'updating' or 'upgrading'

OpenGL is a graphics API. In order to run applications using a higher version of OpenGL you'll need a graphics card and a driver capable of that. From the looks of it, you are running an Intel integrated graphics card on a laptop. I doubt you'll be able to run OpenGL 3.4 on that machine (isn't 3.2 the stable release by the way?).

---

### Post by rutrider on 2009-08-17
Correction:

Tower, not Laptop

And I don't know about the stable version... Like I said... I'm new to Ubuntu

---

### Post by CatKiller on 2009-08-17
> **rutrider said:**
> As in making it 3.4 instead of 1.3...

What makes you think you're using OpenGL 1.3? I'd imagine you're using drivers for 3.1. 3.2 was released less than a fortnight ago.

It's considered impolite to bump a thread more than once a day.

---

### Post by rutrider on 2009-08-17
I try to use a program and it crashes... I go to said program's forums for help... I provide the appropriate logs of said program... Programmers tell me "It wont work with opengl 1.3, try upgrading it"

And that's what I'm *trying* to do here...

When was the release?

---

### Post by CatKiller on 2009-08-17
> **rutrider said:**
> I try to use a program and it crashes...

Which program?

> When was the release?

According to [Wikipedia]("http://en.wikipedia.org/wiki/OpenGL#OpenGL_3.2"), 3 August. So just over a fortnight ago, rather than just under as I'd previously thought.

---

### Post by Yellow Pasque on 2009-08-18
Short answer: You can't easily update it. It's limited by your driver.

Longer answer: You're probably using the Mesa Intel i915 DRI driver, which uses your GPU for OpenGL acceleration, but only allows OpenGL 1.3. The Mesa software rasterizer provides OpenGL 2.1 support, but everything is done in software (SLOOOOOOOOW). To use the software rasterizer, add the following line to the 'Device' section in /etc/X11/xorg.conf and restart X (i.e. log out)
```
Option "DRI" "false"
```

This command is useful in checking OpenGL information:
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by CatKiller on 2009-08-18
GLX version number != OpenGL version number.

---

### Post by Yellow Pasque on 2009-08-18
glxinfo still tells you the OpenGL version though..
```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.5
```

---

### Post by rutrider on 2009-08-19
> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.4

This right?

As for the program that CatKiller *not exactly fond of the name* asked for...

Pretty much half of the programs I got...
Blender in particular (one of the programs I need) has lots of glitches in the window... Can't exactly make what I need when I can't even see what I'm working with...

---

### Post by jbeukema on 2009-08-22
Where can I find OpenGL to install into Ubuntu (jittery jackalope or whatever it's called)? I didn't see it in synoptic

---

### Post by Yellow Pasque on 2009-08-22
> **jbeukema said:**
> Where can I find OpenGL to install into Ubuntu (jittery jackalope or whatever it's called)? I didn't see it in synoptic
It's provided by your video driver and it should be already installed.

---

### Post by rutrider on 2009-08-22
I never really received an answer to my question...

how do i upgrade the opengl (and/or check to see the highest my graphics driver will support)

I'm a bit desperate here... how can I make money off of my games if i cant even *test* them!?!?!?!?!?

*edit*
I'm REALLY desperate

---

### Post by heatblazer on 2009-08-22
> **rutrider said:**
> I never really received an answer to my question...

how do i upgrade the opengl (and/or check to see the highest my graphics driver will support)

I'm a bit desperate here... how can I make money off of my games if i cant even *test* them!?!?!?!?!?

*edit*
I'm REALLY desperate

Why don`t you try to install the latest driver for your videocard? Most drivers comes with the latest OGL libs inside them... Just my suggestion...

---

### Post by Yellow Pasque on 2009-08-22
> **rutrider said:**
> I never really received an answer to my question...
See [http://ubuntuforums.org/showpost.php?p=7804754&postcount=10](http://ubuntuforums.org/showpost.php?p=7804754&postcount=10)

To put it another way, get a better video card if you're going to do 3D development.

---

### Post by rutrider on 2009-08-24
> **heatblazer said:**
> Why don`t you try to install the latest driver for your videocard? Most drivers comes with the latest OGL libs inside them... Just my suggestion...

[QUOTE=Temüjin]To put it another way, get a better video card if you're going to do 3D development.[/QUOTE]

Why do you think I'm trying to upgrade the opengl in the first place!?

---

### Post by rutrider on 2009-08-25
I can't exactly make any money off of flash games... especialy if I have to pay $500 just to get the frikkin program >:(

How am I suposed to get a new graphics card without money?
I need to at least upgrade the opengl I have so Blender will run properly :(

---

### Post by Yellow Pasque on 2009-08-25
> How am I suposed to get a new graphics card without money?
Mow a lawn or two. An AGP Geforce 6 or 7 series card shouldn't cost that much and even the "low-end" ones should be a vast improvement over your current GPU.

---

### Post by rutrider on 2009-08-29
*sigh*

this is STILL not helping me!!!

the help I ask of is NOT that hard to answer...

I need to:

1) At least check the highest opengl my graphics card can handle...

2) Upgrade my current opengl to #1...

IS IT THAT HARD TO SAY 'NO' OR 'YES' !?!?!?!?

Seriously... I want to get the hell out of this house so I dont have to live off of my parents!

And there are no jobs that'll hire me!!

---

### Post by Yellow Pasque on 2009-08-29
> 1) At least check the highest opengl my graphics card can handle...
You already did; it's OpenGL 1.3...
> 2) Upgrade my current opengl to #1...
You're upgraded as far as you're going to get with that hardware.

---

### Post by rutrider on 2009-09-02
Thank you for saying:

"That's as high as it will go."

If you said that after I posted the test, I wouldn't be ANGRY!

If you did... I'm sorry...

---

