---
title: "Mouse issue"
date: 2011-04-30
forum: General Help
---

### Post by MdR15 on 2011-04-30
Hello everybody,
I relatively new to Ubuntu, so perhaps this is a bit silly to ask.
When I am logged in to my normal user account, the mouse will not work in most applications, I have to use the keyboard for control. I don't have this problem in the root account. I have used Ubuntu 10.10 before, that version didn't have this issue. As you may understand, this is extremely annoying. Does anybody know a solution to this problem? I'm using the new Ubuntu 11.04.

Thanks in advance,
MdR15

---

### Post by Derek Karpinski on 2011-04-30
Is it by chance a wireless mouse?

I'm having the same issue.

[http://ubuntuforums.org/showthread.php?t=1745020](http://ubuntuforums.org/showthread.php?t=1745020)

---

### Post by MdR15 on 2011-04-30
Turns out I was just lucky a single time, after reboot the mouse doesn't work properly in root either.
I'm using a wired mouse, It's a R.A.T. 7, it has drivers in Windows to add additional functionality, but this normally doesn't pose any problem with other OS's.

---

### Post by rich.h on 2011-05-05
I'm having a similar problem; cursor moves but window controls will occasionally decline to respond to mouse clicks.  When this happens the cursor does not change shape when over a control that should change it, e.g. hyperlinks, so it looks like it doesn't know it's over a control.  Does not seem to be specific to any particular app, although pop-up boxes appear especially vulnerable.  No problems whatsoever before upgrade from 10.10.

HP Pavilion dv7-1270us; Core 2 duo; 4G RAM; nvidia 9600M gt; touchpad (haven't tried external mouse yet); Ubuntu 11.04, fully up to date.

---

### Post by yoda3616 on 2011-05-05
I'm having the same problem rich.  Can you still use the cursor to move between workspaces?  Also, is this happening all the time for you?  It only happens to me if I have a lot of programs running at once, then the functionality of the mouse never comes back.  This didn't happen to me in 10.10 either.

---

### Post by rich.h on 2011-05-05
> **yoda3616 said:**
> I'm having the same problem rich.  Can you still use the cursor to move between workspaces?  Also, is this happening all the time for you?  It only happens to me if I have a lot of programs running at once, then the functionality of the mouse never comes back.  This didn't happen to me in 10.10 either.

Workspace switching is fine, as best I can determine.  Whatever is going on, it appears to affect only window controls, text boxes, and the like.

I've experimented a little, and found a downright bizarre consistency: I'm working on a 1440x900 display.  Within a rectangular area on this display, x/y boundary 474,620 by 970,660 (give or take a few pixels,) mouse clicks on window controls simply do not work, and the cursor does not change when placed over a control.  Can reproduce at will using Thunderbird, LibreOffice Writer, GIMP, gedit, Liferea, and now Firefox while composing this reply - I moved the text box over that area, and I can no longer place the text cursor on lines 2/3/4 of this paragraph with the mouse.   

Two notes: The desktop also seems to miss the occasional mouse click, maybe one out of 50, anywhere on the screen.  Clicking a second time works.  Also forgot to mention that I'm using Unity.  Next step is to take a just-in-case backup and switch to Gnome to see if it'll fail the same way.  

RH

---

### Post by Dak101 on 2011-05-05
Same issue running HP pavillion tx2170ee.
Also got a screen issue, anyone have that too?

[http://ubuntuforums.org/showthread.php?t=1750401](http://ubuntuforums.org/showthread.php?t=1750401)

---

### Post by wi0 on 2011-05-05
> **rich.h said:**
> I'm having a similar problem; cursor moves but window controls will occasionally decline to respond to mouse clicks.  When this happens the cursor does not change shape when over a control that should change it, e.g. hyperlinks, so it looks like it doesn't know it's over a control.  Does not seem to be specific to any particular app, although pop-up boxes appear especially vulnerable.  No problems whatsoever before upgrade from 10.10.


This describes my experience very well. I didn't quote the more recent post with the box, as I don't know how to get x,y of mouse, and for me the problem seems to occur all over the screen.

Right now it's doing this with the buttons to submit/preview this post. And now it's OK. I only tabbed to the buttons.

Edit: [This]("http://ubuntuforums.org/showthread.php?t=1747222") thread is about the same problem. There's a link to a bug report. This is supposed to be caused by invisible windows, but sometimes it happens while working in one application only, so I'm not sure.

---

