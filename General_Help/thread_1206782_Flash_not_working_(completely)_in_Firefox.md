---
title: "Flash not working (completely) in Firefox"
date: 2009-07-07
forum: General Help
---

### Post by mbreezy on 2009-07-07
I have Firefox and not all flash components are working properly.

My wife plays Farm Town on Facebook and not all the scroll bars work on that game as they do on a machine running Windows with Firefox.  Also, and this is where it really matters :) when I play poker online (also flash) it doesnt show all the tables I can choose from as it did with a Windows system.  I just find it odd that everything works with with flash like sound and picture (yes I can play youtube vids) but it's missing random components.

Anyone else run into missing flash components and have a work around on this?

---

### Post by Ra-Hoor-Khuit on 2009-07-07
What version of Ubuntu are you using and did you install the Adobe Flash plugin or are you using Gnash?

---

### Post by mbreezy on 2009-07-07
I have just about everything installed flash related trying to get this thing to work but yes, I have the flash plugin installed.

Here's a screen shot of what I see...
[IMG]http://i25.tinypic.com/qq97i0.png[/IMG]

Yeah, I circled those with my touchpad on my laptop lol

The big circles are where the lists with scroll bars go and the two smaller circles are where checkboxes would be but are not showing up.  Just so you can see what I'm talking about.  All this worked on a Windows box.

---

### Post by Ra-Hoor-Khuit on 2009-07-07
Whoa, dude... You can thumbnail those Hugh Jass pics, you know, by attaching them instead of posting them in-line.

So you know for a fact that you installed the Adobe Flash plugin?  Okay... 

In that case open Synaptic and search on:  **swfdec**.
Mark and UN-install any hits related thereto.

Repeat above steps using search-term:  **gnash**.

Restart Firefox and see if you can now play Poker.

---

### Post by mbreezy on 2009-07-07
Yeah, I have the following installed...

adobe-flashplugin
flashplugin-installer
flashplugin-nonfree

I also tried what you told me to do and it still doesn't work. :(

Oh and sorry about the big pic, just threw it up quickly.  ;)

---

### Post by mbreezy on 2009-07-07
Any other suggestions?

---

### Post by Geeb on 2009-07-24
I'm having the same problem with firefox and I haven't found a "fix" for it yet, however the workaround I am using for Farm Town is to use Seamonkey instead of Firefox.  The scroll bars work there for some reason.  I know it's not the greatest fix, but at least your wife will be able to plant what she wants now :D

---

### Post by Steelclan on 2009-07-24
It also does the same thing with StickAM it removes the enter chat button.

---

### Post by jonick on 2009-07-24
I found exactly the same issue's with Face Book apps using Jaunty & Flash 10. My only work-around was to run the windows version of SeaMonkey under Wine. Not Elegant, but it keeps the Missus happy :-)

Jonick.

---

### Post by mbreezy on 2009-08-03
Thanks.  I just installed Seamonkey, but not with Wine.  That browser is weak, but nonetheless the ol' lady is happy.  lol  Geez, wish there were just a fix for FX tho!  :)

---

### Post by Zw4nzig on 2009-08-05
So, I have stickam working 100% in Firefox with none of the V4L1<->V4L2 nonsense.

Go to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html") and under website permissions, Always Allow Stickam in the settings, and under Webcam settings (On the sidebar) and make sure Logitech Quickcam Pro 3000 or something similar is there. It works fine for me, with the latest Flash 10 available in the repos.

Edit: It appears you still have to restart Firefox if you end your video stream and attempt to restart it :(

---

### Post by justinheel on 2009-08-05
Install Flash all plug-ins.

---

### Post by High Roller on 2009-08-14
To answer the OP's question:

The missing elements problem is related to windowless mode and is a bug in flash.  To _workaround_ this problem do as follows.

Go to terminal...

```
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg
```

Add the line
```
WindowlessDisable = 1
```
Then save the file.

So far this has fixed the stickam chat problems for me.  The only thing I've noticed is drop-down menus might sometimes fall behind the content in some instances.
I haven't taken the time to file a bug at Adobe...  If anyone wants to beat me to the punch feel free! :)

---

