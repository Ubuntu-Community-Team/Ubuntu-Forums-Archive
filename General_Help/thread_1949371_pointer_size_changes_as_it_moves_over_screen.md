---
title: "pointer size changes as it moves over screen"
date: 2012-03-30
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-30
My pointer size, which I have set to the largest size, on oneiric (but not on Maverick) is inconsistent, and jumps back and forth between that and tiny. It will be small over some aps, big over others. Has anyone else observed this effect? And does anyone have an idea what I might do about it?

---

### Post by Ms. Daisy on 2012-03-30
What did you use to change the size of the pointer in the first place? Did you install a package?

Here's a thread discussing how to change the pointer size, maybe pick a different theme & see if that has the same problems.

[http://ubuntuforums.org/showthread.php?t=1932443](http://ubuntuforums.org/showthread.php?t=1932443)

---

### Post by Dreamer Fithp Apprentice on 2012-03-31
Thanks, Ms. Daisy.

> **Ms. Daisy said:**
> What did you use to change the size of the pointer in the first place?

MENU:System,Preferences,Appearance
TAB:Theme,BUTTON:Customize
TAB: Pointer,SLIDER:Size slid to large all the way right.

> **Ms. Daisy said:**
> Did you install a package?

Not at first. I just used the built in pointers and the standard graphical approach described above. Later I installed the Comix pointers hoping they might be more consistent. They aren't.

> **Ms. Daisy said:**
> Here's a thread discussing how to change the pointer size . . . 
[http://ubuntuforums.org/showthread.php?t=1932443](http://ubuntuforums.org/showthread.php?t=1932443)It is possible I missed something but while the OP in that thread does ASK for a way to change the "mouse cursor" size (to me an oxymoron, cursor is one thing, pointer is another, but I am upon the point of surrendering to popular usage here) the ANSWER seems to be erroneous and illustrates why it is better to give things their correct name because the method suggested relates to the CURSOR, the little thingamajig in a text entry field that tells you where the next letter you type will appear, NOT  to the POINTER, the doodad that tells you where your next mouse click will take effect. Maybe I missed something but that is all I can see there. Anyway, I tried bumping the number and it had no effect on my pointer. And anyway my problem is not with SETTING the pointer size but with getting all aps to HONOR the setting. Some do, some don't.

I also went all through mateconf-editor but the available settings there are pretty much the same. 

> **Ms. Daisy said:**
>  . . . maybe pick a different theme & see if that has the  same problems.
I've tried that quite a bit. Indeed the problem is NOT the same in all themes. In some it is worse, in that they don't allow adjustment of pointer size at all. The behavior I described is what happens in those that do allow adjustment. I've also tried the Comix pointer, huge white (it has to be installed) -- but it behaves the same way as a slider adjusted pointer, appearing over some aps but replaced with a tiny pointer about the size of a 10 point letter "o"over others.

---

### Post by Ms. Daisy on 2012-03-31
Yeah, I didn't read that link all the way through- my bad.  

I remember from some other thread that when you change the pointer size in the desktop theme it may not change it for all the apps as well.  In the apps that your pointer is small, have you checked to see if there's a way to change the pointer size from within the app itself?

---

### Post by Dreamer Fithp Apprentice on 2012-04-01
Thanks again, Ms. Daisy.

> **Ms. Daisy said:**
> In the apps that your pointer is small, have you checked to see if there's a way to change the pointer size from within the app itself?A good thought. I had not but now I have. Nautilus, Caja, Thunar, Synaptic, Mirage, Epiphany all suffer the Tiny Pointer Syndrome and have no setting for pointer size that I have been able to discover.

The behavior is not uniform. In most, I think all, of the programs that do NOT exhibit this problem the pointer is still small in the title bar, which I presume is drawn by the window manager, Marco in my case. So that's understandable. BUT,  in Mirage and Epiphany the pointer is small everywhere except for the left margin, where it is the large size it is supposed to be. In Synaptic the pointer is small everywhere except the text entry fields, the area where a selected package is described in greater detail, and again, the left margin. In Pluma, a Gedit fork, the pointer is large in the text area and small everywhere else.

There is a program called gcursor, which despite my own conservative nomenclature pedantry, seems to be about pointers. The g in gcursor, btw, stands, I believe for Gtk, not Gnome. Anyway, I installed it. I ran it from the command line. I got a bunch of warnings, thus:

(gcursor:2281): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gcursor:2281): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

(gcursor:2281): libglade-WARNING **: could not find signal handler 'extract_theme'.

(gcursor:2281): libglade-WARNING **: could not find signal handler 'entry_selected'.

(gcursor:2281): libglade-WARNING **: could not find signal handler 'size_changed'.

Despite that, the GUI popped up and it had a dial for size initially set at 24 pixels. It wouldn't take any setting past 64. I put it on 64 and closed it. Nothing changed. I opened it and it was back to 24. I selected a different pointer style and changed the number back to 64 and closed it. Again, no change, neither in style or size. I did it again and clicked the "Install Theme" button before closing it. Same result. I just did it again to check and got the same warnings and the size number was back to 24.

The only other thing I can add is it doesn't happen in Maverick. I don't recall if it happened in Natty. I didn't run Natty for more than a day or two.

Thanks for your thoughts.

---

### Post by Dreamer Fithp Apprentice on 2012-04-02
One more thing I've noticed. When switching from an application that shows the tiny pointer to Firefox which shows the big pointer correctly it takes maybe 15 or 20 seconds at a guess for the pointer to change from the tiny size to the correct large size. Dunno what that means but maybe somebody has a guess.

---

### Post by cmcanulty on 2013-03-20
I have same issue

---

