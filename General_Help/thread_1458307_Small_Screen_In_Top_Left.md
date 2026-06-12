---
title: "Small Screen In Top Left"
date: 2010-04-19
forum: General Help
---

### Post by N!NJA on 2010-04-19
Hey guys,

 I recently tried out the Ubuntu 9.04 live CD because I found it lying around the house and decided to try out Ubuntu before installing. So I use it once boots up and everything is fine and I use it for about 10 minutes because I had to leave. 

 The next day I start up the live CD and it goes through the loading screen and everything and then I get a small part of the real screen in the top left of my monitor. I get a mouse courser but I can't move it out of the top left of the of my monitor.

So how do I fix this?

Also, what if I decided to install Ubuntu would that fix the problem?

Thanks In Advanced

---

### Post by P4man on 2010-04-20
Sounds like something aint working right :)
Id be hesitant to recommend installing it if even a live session doesnt seem to work properly, although its possible installing and then installing the proper videodrivers cures it.

What machine is it, do you know what videocard it has?

Also, if you can reproduce the problem, then try pressing control+alt+F1 and see if that gives you a "dos" screen. If it does, try control+alt+F7 (in some cases F8 or even F9) to return to the GUI.

---

### Post by N!NJA on 2010-04-20
> **P4man said:**
> Sounds like something aint working right :)
Id be hesitant to recommend installing it if even a live session doesnt seem to work properly, although its possible installing and then installing the proper videodrivers cures it.

What machine is it, do you know what videocard it has?

Also, if you can reproduce the problem, then try pressing control+alt+F1 and see if that gives you a "dos" screen. If it does, try control+alt+F7 (in some cases F8 or even F9) to return to the GUI.

It's a Dell Inspirion 531s and the videocard is a NVIDIA GeForce 6150SE nForce 430.

If I have time I will do what you said.

---

### Post by N!NJA on 2010-04-21
Bump

---

### Post by P4man on 2010-04-21
is it 100% reproducible, happening every time, or only sporadic?
When it does happen, can you switch to a tty using control+alt+f1 or is the system completely frozen...?

Could be many things, from a bad or scratched cd, to a bug or a hardware issue. Any extra info you could provide would be helpful.

---

### Post by N!NJA on 2010-04-21
It happens every time now, and I would just like to confirm that when I do press control-alt-f1 that Ubuntu won't try to change anything on my computer.

---

### Post by P4man on 2010-04-22
And your installed operating system works fine I assume (otherwise its clearly a hardware problem) ?

Since it worked once, and since a livecd doesnt save anything anywhere and you cant change anything on the disc, Im gonna to blame a bad disc. Perhaps you can download and burn another CD or usb stick to try with?

---

### Post by N!NJA on 2010-04-22
Um, I'll try the Crtl-Alt-F1 thing, but I don't think it's the disk since I also tried the 8.10 Live CD and I got the same problem.

---

### Post by P4man on 2010-04-22
and the computer works fine in windows or whatever OS you have installed?

---

### Post by N!NJA on 2010-04-22
Ya, when I use Windows the computer works fine.

---

### Post by N!NJA on 2010-04-24
Alright, so when I do the Crtl-Alt-F1 it takes me to a "dos" screen in full screen and I am able to see everything fine, but I still can't see the whole screen when I want to use Ubuntu.

---

### Post by P4man on 2010-04-24
and then control alt F7 gets you back your "small" screen with a frozen mouse pointer?

A few things you could try. in the terminal ("dos screen") enter this command:

```
dmesg
```

you'll get to see a lot of things that will make no sense to you, but have a look at the last lines and tell us what they are.


Another thing you could try is booting in safe graphics mode. At the cd menu, press F4 and select safe graphics mode:

[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=bootf4.png[/IMG]

---

### Post by N!NJA on 2010-04-24
I didn't try the F7 to get back to the screen, and when I have time later I will do the "dmesg" thing.

EDIT: I did the Crtl-Alt-F7 thing and I got back to the "small screen" without a cursor at all.

---

### Post by N!NJA on 2010-04-26
Bump

---

### Post by P4man on 2010-04-26
I find it rather rude to keep bumping without answering my questions or responding to the simple suggestions I already made and that are still valid:

/me unsubscribing from this thread.

---

