---
title: "[Karmic] Get back Alsa Mixer Applet"
date: 2009-11-23
forum: General Help
---

### Post by _matz_ on 2009-11-23
When I have recently updated my Ubuntu to Karmic Koala, I sadly realized that the good old Alsa mixer applet has been replaced by a new pulse-applet. As pulse for me only causes problems, I've uninstalled it. Now I had no more mixer applet and the keyboard hotkeys for volume control where no longer working.

I always need these features, so i had to get a solution. I found an applet on [this forum]("http://swiss.ubuntuforums.org/showthread.php?t=1284219"), but it could only display a volume control bar and respond to hotkeys. Double-clicking on the icon did not open a mixer.

After a quick search xfce4-mixer turned out to be a good replacement for the Gnome mixer in older Ubuntu releases:

[IMG]http://www.matthias-sieke.de/getfile.php?file=xfce4-mixer.png[/IMG]



I modified the script in the way that xfce4-mixer opens by double-clicking on the speaker icon.

[SIZE=4][SIZE=3]The modified script can be downloaded[/SIZE][/SIZE]**[SIZE=4] [here]("http://www.matthias-sieke.de/getfile.php?file=alsa_mixer_applet_1.1.tar.gz")[/SIZE]**. For getting it to work, you need to intall the following packages: python, python-notify, python-gtk2, python-alsaaudio  and xfce4-mixer (for example using synaptic).

The files from "alsa_mixer_applet.tar.gz" can be extracted to any folder. I've stored them in /usr/local/bin .

When this is done, all contained files have to get execute permissions.


[IMG]http://www.matthias-sieke.de/getfile.php?file=ausfuehrungsrechte.png[/IMG]


If you want to use your keyboard's volume hotkeys, you have to set them in System> Preferences> Keyboard Shortcuts (or something near it - i've got german localization...)


[IMG]http://www.matthias-sieke.de/getfile.php?file=hotkeys.png[/IMG]


Finally the programs volbar.py and alsavol.py have to be set to start automatically. This can be set under System> Preferences> Startup Programs: (same here...)


[IMG]http://www.matthias-sieke.de/getfile.php?file=startprogramme.png[/IMG]


Now logout and login to test if everything is working.

 

A click on the tray icon opens the slider, double-clicking  opens the mixer

[IMG]http://www.matthias-sieke.de/getfile.php?file=volbar.png[/IMG]


Volume changes are shown via libnotify.

[IMG]http://www.matthias-sieke.de/getfile.php?file=pynotify.png[/IMG]


German Version:                  [**Ubuntu Karmic (9.10) Alsa Mixer Applet Nachrüsten**]("http://www.matthias-sieke.de/index.php?id=19")

---

### Post by Aq32 on 2009-11-30
Besten dank! That is really useful since I am in the same situation and it's such a small script. It also allows mouse scroll on the icon to change the volume which you can't do without a third party app on WinXP!

---

### Post by vadp on 2009-12-04
Thanks for the hint. BTW I've just configured gkrellm's volume plugin to launch xfce4-mixer at a right click

---

### Post by tlwolf on 2009-12-05
I had to install python-eggtrayicon, which wasn't on your list. But once that was installed it does exactly what I needed. Thanks!

---

### Post by JoshGreen on 2009-12-13
My solution to this was to patch gnome-applets to include the mixer again and use the Jaunty version of gnome-media for the gnome-volume-control program, so clicking the "Volume Control" button on the applet actually works.  Just like in Jaunty!  Sheesh! [-(

Wish they'd quit trying to push PulseAudio on everyone.

Here is a page I created for the unofficial deb packages I made and some other info:
[http://resonance.org/~josh/ubuntu.html](http://resonance.org/~josh/ubuntu.html)

---

### Post by alldaylong on 2010-01-17
Hey can someone help me get the volume control icon to reappear please? Your solution worked so that now I can control the volume with the keyboard "volume" buttons, which is great, but I still don't have the icon for volume in the top right and can't figure out how to get it back.

Also, if I go to system>preferences>sound - the sound controls don't open. I get a message that says "Waiting for sound system to respond" - I don't know if that's a big deal or not, but any insight on that would help a lot as well.

Pulseaudio didn't even work at all on my system, so the switch to alsa has been amazing - just need to get this last bit figured out and then my system will be perfectly the way I want it (for now, lol).

Thanks so much.

---

### Post by alldaylong on 2010-01-17
wow - the eggtrayicon package mentioned above and a restart did it.

However, the system>preferences>sound menu still gives the same message. Anyone have any advice for that one?

---

### Post by kindr on 2010-01-29
**Very good job** thanks very very much  =D>;) 
*pulse bye bye ... alsa is the best* :-D

---

### Post by defensorfedei on 2010-07-31
I realize this is an older post, but I recently made the move from Jaunty to Lucid, which puts me in the same position as far as lacking an alsa volume applet is concerned.

I used the modified script and all works well except that the icon background does not play nicely with my panel. I have a semi-clear panel, but the icon wants to keep the default gnome panel icon as its background.  I was wondering if anyone knows how to fix this, so that when the applet starts, it uses the background I have for my panel.  

Is there something in the script that needs modification, or is it something else?

Thanks in advance

---

### Post by DocteurX on 2010-08-16
Here is a modified version of the volbar.py for Lucid. I simply replaced the egg.trayicon by a gtk.StatusIcon. The background color should be ok with this one...

---

### Post by defensorfedei on 2010-08-18
To get more info on this fix, check out this link:[http://ubuntuforums.org/showthread.php?t=1553184](http://ubuntuforums.org/showthread.php?t=1553184)

There are details there about how to change back to your theme sound icon at the end of the post.

---

### Post by lobotomy42 on 2010-09-28
This is perfect, thanks everyone!

---

### Post by spacemarcy on 2010-10-25
It's working (almost) fine.

But changing the volume with the hot-keys, doesn't change the icon in the taskbar, so sound may be muted, but icon displays 3 waves.

Maybe a loop every few seconds to check the current status of the volume?

---

### Post by s4ms3milia on 2010-11-05
> **spacemarcy said:**
> It's working (almost) fine.

But changing the volume with the hot-keys, doesn't change the icon in the taskbar, so sound may be muted, but icon displays 3 waves.

Maybe a loop every few seconds to check the current status of the volume?

Same for me..

[s]Plus i get no Notifications via libnotify[/s].. anybody an idea why?

edit: libnotify works.

---

