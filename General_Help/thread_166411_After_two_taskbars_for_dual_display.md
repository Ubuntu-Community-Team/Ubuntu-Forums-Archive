---
title: "After two taskbars for dual display"
date: 2006-04-26
forum: General Help
---

### Post by rez on 2006-04-26
Heya peeps,

*First things first - I want to say thanks to all the people who put time into helping people here.  Basically my first post, but all the help that has been posted on these forums has got me through all my dual head display woes (although I haven't been game enough to try 3D acceleration yet).*

What I haven't found anything on (or anything specific to this) is once you've got the dual head working as a large or extended desktop ... **how can you go about adding a second taskbar to the secondary monitor?**

With Windows, *Ultramon* is the easiest way to get this working; I haven't found anything like that for Ubuntu or any other linux distribution.

I won't post my xorg.conf at the moment (as it really is quite messed up), but wondering if the solution lies in reconfiguring that somehow.

Any ideas? ;)

---

### Post by JoeMetal on 2006-04-26
Have you tried just clicking "add panel"?  Then just slide it over to your second desktop.  That worked for me, but then again there are many ways to get dual head working.

---

### Post by rez on 2006-04-27
wicked - I'll try that when i get home.  unfortunately this morning when i booted up, ubuntu wouldn't load.  might have to reinstall (again).

cheers dude ;)

---

### Post by ZylGadis on 2006-04-27
The Add Panel works with an NVidia TwinView, confirmed :)

---

### Post by rez on 2006-04-27
Yep - add panel has solved the problem of adding the taskbar.

However, the application associated with/displayed on the secondary monitor doesn't sit in the secondary taskbar ... it's still on the primary one.  Would really, really, really like the applications to sit on the relevant task bar.

Any takers?

---

### Post by JoeMetal on 2006-04-27
I once had mine set up to do that.  But I wansn't using TwinView or Xinerama.  I would actually have two desktops each with its own taskbar, own 4 workspaces and everything.  It was REALLY buggy though and the window switcher and taskbar would always break.  And I also couldn't move windows between desktops.  

If you wanted, I could try to dig up my old xorg.conf and you can give it a try.

---

### Post by mtdewulf on 2006-05-07
I just added a second panel and put it on my right monitor (i have two 19" side by side).  I then added a window list to each of the two panels.  I.E. I have a window list on my panel on the left monitor, and a seperate window list for my panel on the right.  With this setup, windows are correctly put on the correct window list and even change lists when i move a window from one monitor to the other.  Hope this helps.  I should note that I am using TwinView.

---

### Post by toon on 2006-06-01
Good one. Though, anyone know of a regular panel (applet) that makes this possible, instead of having it in some dropdown menu?

Thanks.

---

### Post by tenmuses on 2007-07-01
I'd like to second a confirmation that the add panel method works with Twinview.

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=221174") to get twinview working.

A right-click on the existing taskbar gives the option for a "new panel."   After dragging the new blank taskbar over to the second monitor, you click "Add to Panel" and choose "window selector" from the Desktop and Windows portion.

Works like a champ - thanks JoeMetal!

---

### Post by Aqualung on 2008-01-05
> **mtdewulf said:**
> I just added a second panel and put it on my right monitor (i have two 19" side by side).  I then added a window list to each of the two panels.  I.E. I have a window list on my panel on the left monitor,I think that comes by default these days, with Gutsy.> and a seperate window list for my panel on the right.  With this setup, windows are correctly put on the correct window list and even change lists when i move a window from one monitor to the other.  Hope this helps.  I should note that I am using TwinView.Awesome! Thanks! Closer to Ultramon!

---

