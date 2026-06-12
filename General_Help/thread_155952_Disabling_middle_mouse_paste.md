---
title: "Disabling middle mouse paste"
date: 2006-04-06
forum: General Help
---

### Post by Kray on 2006-04-06
I've seen few posts about it on this forum (and elsewhere...) but since no solution was pasted I'm asking again:

Is there any way to disable pasting on middle mouse button click?

I've tried to live with it, but no, I don't like it. Simple...

---

### Post by Noremacam on 2006-04-25
*bump* this is annoying the heck out of me as well. Anyone have a solution? This really messes up my web browsing

---

### Post by Zyphrexi on 2006-04-25
I may have a solution for you, that was bothering me as well, and I found this option simply by goofing off in firefox's preferences.

In firefox, go to Edit>Preferences>click the advanced tab and under browsing check the 'use smooth-scrolling' checkbox

hope that helps

---

### Post by TmP on 2006-04-25
You mean openoffice?
Tools, options, view, mouse, middle mouse button

---

### Post by Zyphrexi on 2006-04-25
> *bump* this is annoying the heck out of me as well. Anyone have a solution? This really messes up my web browsing
2 Weeks Ago 02:17 AM


I assumed it had to do with firefox.

---

### Post by peaceful_dragon on 2006-04-28
I'd like to bump this as well.

The problem is that when I'm scrolling through massive amounts of code using the mouse wheel in, say, SlickEdit, it's incredibly easy to just press a little bit too hard on the wheel and end up pasting junk in my code.

Sometimes I don't find out I accidentally pasted something until the next compile!

Very annoying. Grr.

---

### Post by gantengx on 2007-10-12
true... it is very annoying, i hope someone knows how to fix this...

---

### Post by ryanVickers on 2007-10-12
> **Kray said:**
> I've seen few posts about it on this forum (and elsewhere...) but since no solution was pasted I'm asking again:

Is there any way to disable pasting on middle mouse button click?

I've tried to live with it, but no, I don't like it. Simple...

It's _**not a problem**_ that needs to be fixed, [COLOR=Red]_**but a feature**_[/COLOR]. :p  There's some part of reconfiguring X that allows you to pick mouse options; and turn this off...

---

### Post by thethendi on 2007-12-19
This worked for me; I have a Thinkpad T43 which allows the use of the middle mouse button as a scroll button (so that when you hold the middle mouse button and move the pointer thing in the middle of the keyboard, it scrolls).  Anyway, with some help from the [[COLOR="Blue"]Thinkwiki[/COLOR]]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint") site, I configured my xorg.conf file's mouse section to look like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"
	Option		"EmulateWheelTimeout"	"1"
EndSection
```

I was having problems until I placed the "EmulateWheelTimeout" "1" in there.

As always, make a backup (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup) if you try this.

---

