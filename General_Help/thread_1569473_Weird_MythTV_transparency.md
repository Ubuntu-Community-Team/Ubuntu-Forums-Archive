---
title: "Weird MythTV transparency"
date: 2010-09-06
forum: General Help
---

### Post by NertSkull on 2010-09-06
So I must have changed a setting somewhere, but my mythTV is acting really weird.

When navigating through menus, everything is fine.

But when playback (or live TV) starts, the screen goes transparent and you can see the desktop and whatever window is open.  While mythtv is faintly visible above.

Any ideas what I've done?  I selected a new theme recently (equinox) but other than that I don't think I've changed anything

BUT, mythtv works FINE in other accounts on the system.  So it has to be (i assume) some setting in my account only.

I attached two pictures to help describe.

Notice in the second, the blue bars are my background, but you can kind of see the OSD above it.

---

### Post by NertSkull on 2010-09-09
did i really mess this up in such a way that no one else has ever seen :)

---

### Post by NertSkull on 2010-09-13
allright I have figured out what has caused the problem

apparantly Cairo-dock doesn't play well with MythTV.  If I turn on cairo-dock then turn on MythTV I get the transparency issue.  If I turn OFF cairo-dock and then turn on Mythtv I STILL get the transparancy.

BUT, if I turn cairo-dock off, log out and log back in without ever having cairo-dock start, MythTV will work fine.  But as soon as I turn on Cairo-dock I can't get mythTV to work for the rest of the session.

I've used the find -mmin -2 command after turning on cairo-dock to see if I can find what has changed in the past two minutes, but the only things that I can tell change are files only cairo-dock uses.  No system files seem to be altered.

So does anyone know how I can potentially use both cairo-dock and mythtv (without transparency)???  I'd really like to use both.

---

### Post by eriktheblu on 2010-09-13
My first guess is that it's a Compiz settings issue. I'd say check the transparency settings using CCSM.

---

### Post by NertSkull on 2010-09-13
Well I tried looking around in compizconfig and couldn't find anything that looked to be the case.  But to be sure I tried changing a few settings.

Then I went ahead and turned off all modules that I could and re-started.  Same thing though.  Working mythtv UNTIL cairo-dock gets started-remaining even after turning off.  Only way to get back to normal is to restart.

Any other idea?  Or maybe something specific I should be changing in compiz?  I'm not 100% familiar with compiz, so I could be missing something.

---

### Post by eriktheblu on 2010-09-13
Fading Windows,Opacify, and Opacity/brightness/saturation would be the first things I suspect.

Easiest test, disable all desktop effects. That will tell you if this is even a worthwhile avenue to look at.

---

### Post by NertSkull on 2010-09-14
Well, if I disable all effects it works.  The transparency goes away.  But I'd like to keep some of those effects.

I changed as many settings as I could in fading windows, opacify, brightness/saturation, etc.  I even tried turning those modules off all-together and I still get it.

---

### Post by NertSkull on 2010-09-14
This is interesting though. 

I've discovered that ONLY the Cairo Dock with OpenGL causes the problem.

If I use the Cairo-dock (no OpenGL) then MythTV WILL work.

So does that mean it is something to do with OpenGL?

I guess I could just use the non OpenGL dock always.  But I'd kind of like to figure out whats going on.

---

### Post by eriktheblu on 2010-09-14
What I'm thinking is that the dock might be setting transparency for  it's window class, which just happens to be the same as your myth front-end.

I'm thinking if you specify that setting for your Mythtv window, it might override the class setting.

Alternatively, you might be able to run your dock in the non-OpenGL mode and manually set transparency in CCSM.

I'm really just guessing with this. My Mythtv runs on a dedicated machine with no effects, and I don't use docks.

---

### Post by eriktheblu on 2010-09-14
Try this:
With desktop effects enabled and the dock *not* running, start CCSM.
Check your settings.
Close CCSM.
Start Cardio-Dock.
Check CCSM to see if any settings changed.

---

### Post by boppa7 on 2010-11-23
I'm having the exact same issue on Ubuntu 10.4 so I'm wondering if there is a solution.    When running mythtv I get the desktop background bleeding through the picture when watching tv or recorded shows.    What I've noticed is that running cairo-dock with our without opengl makes no difference.  The ONLY time I don't have the transparency issue is if I turn off all compiz effects in the Visual Effects tab of &quot;Appearance Preferences&quot;.  Setting it to Normal or Extra causes the problem.    I've used CCSM to disable all effects but the problem persists.  Note that I'm new to cairo-dock and compiz so I'll keep playing as I may be missing something obvious.

---

### Post by NertSkull on 2010-11-24
I don't know if my problem was the same as yours.

I had to delete the cairo-dock settings in the home folder, then restart, then I could get mythtv to work.  Just turning cairo-dock off didn't do the trick for me.

I still don't know why it does what it does, which is why I've left this thread unsolved.  But try deleting ALL cairo-dock settings, then try mythtv.  Then you may try just using the non-openGL cairo dock with mythtv.

I don't have cairo dock installed anymore, but I seem to remember that I could get the non openGL version to work with mythtv.

Sorry I can't be more help.  In the end having a consistently working mythtv was more important to me than cairo-dock.

Someday when I have time I want to look at other docks.

---

### Post by CliveHarris on 2011-01-14
Hi,

I've been having this problem for a while and I think I've found a solution.
I found it on the forum on Parallels Workstation, which suffers from the same problem ([http://ubuntuforums.org/showthread.php?t=246863](http://ubuntuforums.org/showthread.php?t=246863)).

The answer is to set the environment variable "export XLIB_SKIP_ARGB_VISUALS=1" as you're starting MythTv Frontend. The easiest way to do this is to use a text editor to create a batch file to do it automatically. 
I created /home/clive/mythtv/mythtv_start_script, with the following contents:

export XLIB_SKIP_ARGB_VISUALS=1
mythfrontend --geometry 640x480

(The "geometry" setting is just to stop it filling the screen - leave it out if you don't need it)

Make this file executable (properties > permissions > execute). Then just click on it to start it. Also you can modify the MythTv Frontend start icon to call the batch file. (right click on icon > properties > command). Change the command to /home/clive/mythtv/mythtv_start_script (or wherever you put the script.

Let me know if it helps.

Clive

---

### Post by NertSkull on 2011-08-20
So I know its like 8 months later.  But that totally fixes it for me. 

Its nice to be able to use the dock again.  Thanks for the post.

---

