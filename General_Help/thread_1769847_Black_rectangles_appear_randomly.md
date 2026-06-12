---
title: "Black rectangles appear randomly"
date: 2011-05-28
forum: General Help
---

### Post by AndroidSisa on 2011-05-28
Hi

I've installed Ubuntu 11.04 32bit on three different computers.
The problem is that while working, suddenly some of the graphics become like black rectangles which are not refreshed.

This is happening out of nowhere and is very annoying. The problem did not occur on version 10.

Its also weird since I searched the net but haven't found similar problem, however as i mentioned, it occur on three different computers.

I'm attaching a screenshot which demonstrate what i mean.
If anyone know what cause this and how to fix it, I would appreciate your help.

---

### Post by ram0042 on 2011-05-28
> **AndroidSisa said:**
> Hi

I've installed Ubuntu 11.04 32bit on three different computers.
The problem is that while working, suddenly some of the graphics become like black rectangles which are not refreshed.

This is happening out of nowhere and is very annoying. The problem did not occur on version 10.

Its also weird since I searched the net but haven't found similar problem, however as i mentioned, it occur on three different computers.

I'm attaching a screenshot which demonstrate what i mean.
If anyone know what cause this and how to fix it, I would appreciate your help.
GNOME3 is still buggy. Check their bug reports for similar complaints. I had that same problem but not with Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-05-28
> **AndroidSisa said:**
> Hi

I've installed Ubuntu 11.04 32bit on three different computers.
The problem is that while working, suddenly some of the graphics become like black rectangles which are not refreshed.

You are using Gnome 3, and it's not ready for prime time yet. You would want to post this question to a Gnome 3 developer group. 

I would do a PPA Purge on Gnome 3, if I was you and switch to "Gnome Classic" instead to solve this.:P

---

### Post by paxxus on 2011-05-28
> **linuxinstalledfromhdd said:**
> You are using Gnome 3, and it's not ready for prime time yet. You would want to post this question to a Gnome 3 developer group. 

I would do a PPA Purge on Gnome 3, if I was you and switch to "Gnome Classic" instead to solve this.:P
I have used ubuntu 11.04 in "classic" mode for some weeks now and I'm frankly a little frustrated with all sorts of buggy behavior, the gravest of which is occasional crashes when the screen saver is started (even when I just use blank screen).

Could you please be more specific as to how one does a "PPA Purge on Gnome 3" in order to get a more stable Gnome classic?

---

### Post by ram0042 on 2011-05-28
> **paxxus said:**
> I have used ubuntu 11.04 in "classic" mode for some weeks now and I'm frankly a little frustrated with all sorts of buggy behavior, the gravest of which is occasional crashes when the screen saver is started (even when I just use blank screen).

Could you please be more specific as to how one does a "PPA Purge on Gnome 3" in order to get a more stable Gnome classic?
that is not gonna help at all but to remove the PPA of Gnome 3. you will still have to remove Gnome 3 as well. I cannot find the old repositories in which gnome 2.32 have been kept on.

---

### Post by AndroidSisa on 2011-05-29
Guys, first of all, thank's for your answers.

I just installed Ubuntu 11.04 and have this problem right from the start.
So what I understand from you is that Ubuntu 11.04 comes with Gnome 3, which is buggy, thus I cannot use it and need to install version 10.

Did I get this right? Or can you offer another solution?

Thanks again !

---

### Post by CoolJohnB on 2011-05-29
If you have just done a straightforward install of 11.04 then you DON'T have Gnome 3!  11.04 comes with Gnome 2.32.1

I think you need to look at your video drivers, have you checked to make sure they are the latest?  Also you might need to install a propriety driver you do this by going to "System Settings" and then "Additional Drivers".

Hope that helps and you solve your problem.

---

### Post by paxxus on 2011-05-31
The annoying problems I have (sorry for the hi-jack) does not seem to be video driver related (I don't have any available for my system anyway), just from the top of my head:

1. If mouse is positioned near the edge of a window the window focus may start to oscillate (I use auto-focus).
2. Double-clicking on a window does not maximise vertically even though I have customised it to do so.
3. Vertical maximise (by middle clicking the maximise icon) maximizes the window vartically, but not all the way to the bottom - a gap is there.
4. The Gnome GUI crashes about once a week - black screen with only the mouse pointer. I think this is related to the screen saver (which I need for security reasons) but I'm not sure.
5. Keyboard mapping is wrong in terminal mode (Ctrl+Alt+F1) making is almost impossible for me to even log in (I have special characters in my password).
6. The micro windows shown in the workspace switcher randomly disappear.
7. When I select "Open Tab" in a terminal window, the window may grow in height (as it should) to make room for the tabs. But when the window is already at the bottom of the screen it should grow upwards instead of downwards (forcing me to manually reposition the window).
...and so on.

I know these may seem like small issues, but ALL of this worked perfectly in 9.10. In classic mode I cannot detect any substantial difference compared to 9.10 - the only difference is that all sorts of small stuff is now buggy. I just don't understand why they messed around with this for apparently no reason. It's frustrating because I don't want to be stuck on an old distro forever, on the other hand all this adds up to a less than smooth experience.

I will give it some months to see if the updates will fix these things :popcorn:

---

