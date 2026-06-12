---
title: "Can I specify which display I want a program opening on?"
date: 2012-03-04
forum: General Help
---

### Post by smintlin on 2012-03-04
I'd like to specify which display I open a specific program on - I want to run it @ 1280x1024 on the display connected to DVI, but it continues to open on the smaller display connected via VGA and shrinks to 1024x768. The program can't be resized once open, and refuses to open on the larger display. Any help is appreciated!!!

tl;dr
I want to force a program to open on DVI-0 rather than VGA-0 which it is opening on by default.

---

### Post by cortman on 2012-03-04
[This]("http://ubuntuforums.org/archive/index.php/t-863092.html") looks a little complicated, but it seems to address your issue.

---

### Post by smintlin on 2012-03-04
> **cortman said:**
> [This]("http://ubuntuforums.org/archive/index.php/t-863092.html") looks a little complicated, but it seems to address your issue.

Thanks for the help, but it doesn't seem anything in there helped.

---

### Post by cortman on 2012-03-04
Check the first few posts.
Ubuntu typically opens an application in whatever screen is set to primary in xrandr. Have you set the DVI-0 display as primary?

---

### Post by smintlin on 2012-03-04
> **cortman said:**
> Check the first few posts.
Ubuntu typically opens an application in whatever screen is set to primary in xrandr. Have you set the DVI-0 display as primary?

Forgive my ignorance, but I am unsure. I have to manually set the VGA display to appear to the left of the DVI display at each boot, but am unsure about which is the primary display.


The best I was able to do with anything in that linked post was have the program launch on the smaller display and then move itself to the larger display at the smaller size.

---

### Post by smintlin on 2012-03-04
Nevermind - all good! Got the primary display set and everything is working perfectly!

---

### Post by papibe on 2012-03-04
I know how to do it on separate xscreens.

When a application is open it will look at the shell variable DISPLAY. I have two screens.

For instance: in my main monitor:
```
echo $DISPLAY
:0.0

```
but in my second monitor (HDTV):
```
echo $DISPLAY
:0.1

```
If I want to launch a GUI application on the 2nd monitor (regardless where I am), I can force it but running:
```
DISPLAY=:0.1  eog Pictures/pic.jpg
```
(just viewing a picture in this case).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by cortman on 2012-03-04
> **smintlin said:**
> Nevermind - all good! Got the primary display set and everything is working perfectly!

Great! For an intelligent and inquiring mind, usually all we need to do is point it in the right direction.

Mark this thread as [SOLVED], if you would, using the thread tools in the upper right. And if the problem comes up again, papibe looks like they have some good ideas.

Good luck!

---

