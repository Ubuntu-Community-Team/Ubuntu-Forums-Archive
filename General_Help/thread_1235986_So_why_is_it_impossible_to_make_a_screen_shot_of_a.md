---
title: "So why is it impossible to make a screen shot of a video?"
date: 2009-08-09
forum: General Help
---

### Post by KinaU on 2009-08-09
Just curious, I stopped the video and made a screenshot, closed the video, and then the screenshots on my desktop become black.

It's disappointing. :(

---

### Post by zvacet on 2009-08-09
I never try that before but I did exactly as you described and it work.I choose **grab current window** and **delay of 2 sec**.Enabled effects too.I don´t know if this is of any help to you but just info.

---

### Post by hansdown on 2009-08-09
Hi KinaU.

Not sure why it didn't work for you.

I took one in vlc.

---

### Post by ridgeland on 2009-08-09
I've been playing with kdenlive.
I like it's feature of stepping frame by frame then when you are at the exact frame you want you export that image.

---

### Post by KinaU on 2009-08-09
I tried with Movie Player and VLC, and this is what I get:

[ATTACH]124224[/ATTACH]

Tried kdenlive and get "error occurred while parsing element". No idea what this means. :confused:

Anything else that can help?

---

### Post by ridgeland on 2009-08-09
In kdenlive with the frame I want displayed in the preview window I right click and select "extract frame".  Is that where you got the error message?
Do you have lots of free RAM?  what does "$ free" show while vlc is running?
I use ksnapshot for screen capture, what are you using?

---

### Post by KinaU on 2009-08-10
After a few tries I got kdenlive to work, found extract frame, and am happy again (for the moment). :D

Thank you all, I appreciate it. ;)

---

### Post by hibliss on 2009-08-10
VLC has an inbuilt screenshot utility. 

I think it is Ctrl+Alt+S

---

### Post by asmoore82 on 2009-08-10
+1 for VLC's builtin screenshot ability;

If you really want to take a shot with the other tools,
you have to go into your player of choice and turn off all forms of accelerated output:
```
mplayer -vo X11 *somemovie.avi*
```

The reason for this is with video acceleration, the graphics hardware
itself does the colorspace conversions and scaling so the video never actually exists
in a form that can be understood and captured through the standard graphics stack.

Such failed screenshots used to be a big blue box on GNU/Linux and a big green box on windoze systems;
I guess now it's a black box on linux.

---

### Post by hibliss on 2009-08-10
Thanks for posting that, very interesting. I always knew the effect, but never the cause.

---

### Post by andrew.46 on 2009-08-10
Hi KinaU,

If you manage to get the odd video effect sorted out you might be interested to try out MPlayer's screenshot ability. The syntax is:

```
mplayer -vf screenshot *[COLOR="Red"]input_file[/COLOR]*
```

Simply pressing the 's' key takes a single screenshot in png format in the working directory. If you wish to take a series of screenshots you can press the 'S' key and MPlayer will keep taking screenshots until the 'S' key is pressed again.

Andrew

---

