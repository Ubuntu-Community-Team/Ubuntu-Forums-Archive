---
title: "Ubuntu 12.04: Gimp 2.6 Does Not Show in Launcher, And Toolbars are Unmovable"
date: 2012-05-18
forum: General Help
---

### Post by gsparky2004 on 2012-05-18
Just loaded Gimp 2.6 onto Ubuntu 12.04 via the Ubuntu Software Center.  When I started it up, I got the two toolbars (Layers and Toolbox) along with the main window.  However, there is no launcher present in the Unity toolbar and the two toolbars have their tops (with the part of the window that allows you to click and drag them) hidden behind the Unity top task bar.  As if that wasn't enough, one of the toolbars (Layers) is on the far right of my right-most screen (I have two large dual monitors.  Nice, but not when this happens.)

What I've done to try to fix the problem:  I've closed the program and re-opened.  Same thing.  I've tried to right-click on the windows to see if somehow I can get them to move.  No dice.  If I minimize the main window, there's no way to get it back since it doesn't show up in the Unity toolbar.  I have to do a "ps" in terminal and kill the program, then restart it.  

Here's [_a screenshot to help you better understand the problem._]("http://site2241.net/images/Gimp_problem.png")  If anyone here has any ideas, I'm all ears.

Thanks!

**UPDATE:** There was a very small amount of the toolbox window sticking out from underneath the top taskbar that I was able to move it.  The other window (Layers, etc) I had to separate each window, which then moved it.  But I still don't have anything showing in the Unity taskbar so I cannot minimize Gimp if needed.

---

### Post by ajgreeny on 2012-05-18
Does an icon show in the launcher when gimp is running?  It should do, and if so you can just right click on it and choose "Keep in launchbar" or some similar option; I do not run unity, so have forgotten the exact words.

As to your separate window positioning, you can set it all up as you want, moving the partly showing windows by holding Alt and dragging with L mouse button with the cursor anywhere in the window (that's a standard window management trick, also used in Windows, I think).  Then go to gimp Edit >Preferences >Window management and make all settings as in my screenshot then click on the "Save Window Positions Now."

Next time you open gimp the windows will all be exactly as you last set them up.

---

### Post by gsparky2004 on 2012-05-18
Thanks for the ALT+left-mouse-button trick.  I didn't know that one.  So if that ever happens again, that problem is solved.
As for your first question, no, it's not showing on the Launcher.  I've been starting the programs as I load them, then right-clicking on the icon in the Launcher and saying "Lock to Launcher".  But Gimp is not even showing.  I believe this is a bug, as I just found out [here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/995916").

Thanks for the assist, ajgreeny.  I'm marking this as "Solved" since you solved my first problem, and the second is a bug of Gimp.

---

### Post by gsparky2004 on 2012-05-18
**UPDATE:**  [As stated before]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/995916"), there's a bug with Gimp in which the icon will appear in the Launcher for a split-second when you start-up Gimp, then the icon will disappear.  I managed to right-click on it for the brief instant it appeared on the Launcher.  Two things then happened.  One, Compiz blew up.  The entire desktop disappeared (only the background image was seen), then reappeared with a message that Compiz had a fatal error.  The second thing was that the Gimp icon was now visible in the Launcher, and has stayed there through a re-boot.  It also remains when I start-up the program.  Take that for what it is worth.

---

### Post by abdulmajid on 2012-05-20
I have the same problem with GIMP 2.8 and Unity. :(

---

### Post by Simeo on 2012-05-25
> **abdulmajid said:**
> I have the same problem with GIMP 2.8 and Unity. :(

I'll second that.

---

### Post by philinux on 2012-05-25
> **abdulmajid said:**
> I have the same problem with GIMP 2.8 and Unity. :(

This should have been fixed now. 

 [https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916)

---

### Post by Simeo on 2012-05-25
> **philinux said:**
> This should have been fixed now. 

 [https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916)

I read this don't understand the fix. Should it be automatic or do I need to do some sort of workaround? I have all updates installed as far as I know.

---

### Post by abdulmajid on 2012-05-25
> **philinux said:**
> This should have been fixed now. 

 [https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916](https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916)

So that means I'll have to run the update and the issue will be fixed, without any workaround?

---

### Post by philinux on 2012-05-25
> **abdulmajid said:**
> So that means I'll have to run the update and the issue will be fixed, without any workaround?

Yep. Sorted here I'm using 12.04 and gimp 2.8 from the ppa.

---

