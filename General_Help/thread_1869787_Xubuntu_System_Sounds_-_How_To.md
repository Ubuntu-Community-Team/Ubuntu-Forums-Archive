---
title: "Xubuntu System Sounds - How To"
date: 2011-10-26
forum: General Help
---

### Post by cottfcfan on 2011-10-26
This has been a pain for all those how have jumped from Ubuntu to Xubuntu, so here is how I managed to get system sounds in Xubuntu 11.10.

1st install the necessary apps:
```
sudo apt-get install dconf-tools ubuntu-sounds sox xfconf
```
Now the easy bit Login Sound.
Go to settings-settings manager-session & startup-application autostart-add.
For the Ubuntu login sound on the COMMAND Line add:
play /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
You can point the command toward any sound file you like (it may have to be a .ogg file though - not tested anything else)
Add to NAME & DESCRIPTION whatever you like and click OK.

Now system sounds:
Go to system/dconf Editor/org/gnome/desktop/sound.
Make sure the Event Sounds & feedback sounds boxes are ticked.
Then change the theme name to "ubuntu" (without the quotes)
All your gtk apps should now have the same system sounds that the main Ubuntu version has.
Now go to settings-settings Editor-xsettings-net & you will see SoundThemeName, change the value to "ubuntu" (without the quotes)
All your xfce apps should now have sound also.
Finally reboot.

---

### Post by zamos on 2011-10-26
Does that work for the sound notification in Thunderbird as well? 
I'm currently in Ubuntu so I can't test it out, but will most likely give it a shot again later.
The lack of sound notifications was about the only (all be it minor) annoyance I had with Xubuntu.

---

### Post by cottfcfan on 2011-10-26
When I open up Thunderbird, there is a sound Notification for any new mail in the Inbox, a popping sound, which is default.
I tend to use gnome-gmail-notifier though, that plays a sound whenever new mail arrives.

---

### Post by zamos on 2011-10-26
Just tried out the sounds and they work great! Thanks!

As for Thunderbird, if I want my own WAV sounds, I just have to install the following (which also works with Ubuntu)

Libaudiofile0
    Libesd0
   esound-common

---

### Post by cottfcfan on 2011-10-26
Glad it works.
Ive also tried the "Dream" sounds from here:
[http://xfce-look.org/content/show.php/Dream?content=75398](http://xfce-look.org/content/show.php/Dream?content=75398)
Just copy the folder to /usr/share/sounds & point dconf-editor & xfconf to "dream" instead of "ubuntu" & copy the button sounds across from ubuntu to dream.

---

### Post by mvario on 2012-02-03
Thanks, cottfcfan!  Just the information I was looking for, and it worked for me!

---

### Post by bartnortthwest on 2012-05-14
I'm using 12.04. New clean install of Xubuntu from CD and have not had system sounds ever.  Posted on absolute beginner and had replies about phonon.  Followed your directions exactly  and still no system sounds.  When I browse with file manager to the .ogg files they play nicely.  Any other ideas for me. The silence is defeaning, especially for a new user.

Thanks  in advance.

---

### Post by cottfcfan on 2012-05-14
Hi Bart,
My above instructions worked for 11.10 but not 12.04.
I was informed a couple of days back that extra packages are needed.
Try:
```
sudo apt-get install sox gnome-session-canberra xfce4-mixer
```
Then reboot.
See if that works.
I can't test it at the moment as I only have ubuntu/kubuntu installed.

---

### Post by bartnortthwest on 2012-05-14
Hi again  _cottfcfan,_

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xfcce4-mixer

I guess it's not available just yet.  I'll try tonight.

Cheers,

Bart

---

### Post by vasa1 on 2012-05-14
> **bartnortthwest said:**
> Hi again  _cottfcfan,_

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xfcce4-mixer

I guess it's not available just yet.  I'll try tonight.

Cheers,

Bart
Bart, maybe a typo at your end? Shouldn't it be xf_c_e4-mixer and not xf**cc**e4-mixer?

---

### Post by cottfcfan on 2012-05-15
Reinstalled Xubuntu today, and none of the above gets system sounds back in 12.04.
Music plays fine, can even enable sounds in gnome-games. Added login-sound to autostart, but just no system sounds (button press etc...).
If anyone has managed this could they please explain how.
This has been an issue i've wrestled with since beta 1 with no joy, and yet in 11.10 they worked fine.

---

### Post by bartnortthwest on 2012-05-17
Installed the mixer package and still no system sounds.  Also installed all recent updates.  Maybe it's now a configuration issue.  The mixer UI seems to make the volume bar move, but no sound.   I do hear a popping sound when I adjust volume using Pulse Audio Volume control, but no other System sounds play.  Do I need to uninstall Pulse Audio?

---

### Post by bartnortthwest on 2012-05-17
Definitely no joy here either.  Hoping this bug is addressed.

---

### Post by Toz on 2012-06-07
Okay - I've got event sounds working in my 12.04/Xfce 4.10 install. Only I'm not sure exactly what the secret piece of the puzzle was. Hoping someone can test it to see exactly what it was. 

I think it is related to the fact that GTK_MODULES is not being properly set/exported in 12.04 anymore. In 11.10, the following files exist:
```
cat /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules 
# This file is sourced by Xsession(5), not executed.

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi

export GTK_MODULES

```
...and
```
cat /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules 
# This file is sourced by Xsession(5), not executed.

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi

export GTK_MODULES

```

These files were missing in my 12.04 install (in fact, they are no longer part of the libcanberra-gtk-module package - which seems to have migrated to gconf) and as a result, there is no GTK_MODULES environment variable being set. In addition to the steps from post #1, creating these two files and rebooting has brought sound effects back for me.

I also installed a number of packages. But can someone try creating these files on their system to see if they are the key?

---

### Post by wkrekik on 2012-06-11
> **Toz said:**
> I also installed a number of packages. But can someone try creating these files on their system to see if they are the key?
Indeed creating this files enabled sounds (after installation of  gnome-session-canberra and sox). Thanks

---

### Post by Toz on 2012-06-11
> **wkrekik said:**
> Indeed creating this files enabled sounds (after installation of  gnome-session-canberra and sox). Thanks

Interesting, I don't have gnome-session-canberra installed. Sounds work without that package for me.

---

### Post by cottfcfan on 2012-06-11
I too can concur.
After creating the 2 files & installing sox & gnome-session-canberra, system sounds now work.
Wish they were just included in the stock install, rather than 3 months of trial & error.

---

### Post by bark50 on 2012-07-05
Following the first post, I now have a log-in sound.  Can somebody please tell me how to create the files from Toz's post, what to name the files, and where to put them?  Thanks.

---

### Post by Toz on 2012-07-05
> **bark50 said:**
> Following the first post, I now have a log-in sound.  Can somebody please tell me how to create the files from Toz's post, what to name the files, and where to put them?  Thanks.

Here is how. From a terminal window:
```
sudo leafpad /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
```
...enter your password when prompted and copy/paste the following code:
```
# This file is sourced by Xsession(5), not executed.

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi

export GTK_MODULES
```
...and save the file.


Then,
```
sudo leafpad /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
```
...copy/paste the following code:
```
# This file is sourced by Xsession(5), not executed.

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi

export GTK_MODULES
```
...and save the file.

IIRC, you need to log out and back in for it to take effect.

---

### Post by bark50 on 2012-07-05
Worked!  Thanks so much Toz!!

---

### Post by lupopa on 2012-07-11
Yes :)
Worked;)

but not play sounds i.e. window-slide.ogg, desktop-logout.ogg etc..

Is there an official list of file names of all supported system sounds?

what can i do?

---

### Post by Toz on 2012-07-11
> **lupopa said:**
> Yes :)
Worked;)

but not play sounds i.e. window-slide.ogg, desktop-logout.ogg etc..
So do sound effects work or not?

> Is there an official list of file names of all supported system sounds?

what can i do?

Its supposed to be aligned with the freedesktop sound naming specification (see: [http://0pointer.de/public/sound-naming-spec.html]("http://0pointer.de/public/sound-naming-spec.html")). Although, I find that not all sound effects are supported.

---

### Post by lupopa on 2012-07-11
> **Toz said:**
> So do sound effects work or not?

not all Sounds will playing...

only: bell.ogg, button-pressed.ogg, button-toggle-on.ogg, button-toggle-off.ogg, loginsound with entry in startprogramme, dialog-error.ogg, dialog-information.ogg, dialog-warning.ogg, system-ready.ogg

i search soundfiles (filenames for window-slide, window-minimizing etc...

> **Toz said:**
> 
Its supposed to be aligned with the freedesktop sound naming specification (see: [http://0pointer.de/public/sound-naming-spec.html]("http://0pointer.de/public/sound-naming-spec.html")). Although, I find that not all sound effects are supported.

I'm looking, thank you

---

### Post by lupopa on 2012-07-12
Hi,

The sound files must be defined somewhere in the system. But where?

The page you've suggested is, in 2008. I think it is not up to date.

Greetings

Lupo

---

### Post by Toz on 2012-07-12
From the libcanberra-gtk-module source, file canberra-gtk-module.c, there is this:
```
/*
   We generate these sounds:

   dialog-error
   dialog-warning
   dialog-information
   dialog-question
   window-new
   window-close
   window-minimized
   window-unminimized
   window-maximized
   window-unmaximized
   notebook-tab-changed
   dialog-ok
   dialog-cancel
   item-selected
   link-pressed
   link-released
   button-pressed
   button-released
   menu-click
   button-toggle-on
   button-toggle-off
   menu-popup
   menu-popdown
   menu-replace
   tooltip-popup
   tooltip-popdown
   drag-start
   drag-accept
   drag-fail
   expander-toggle-on
   expander-toggle-off

   TODO:
   scroll-xxx
   window-switch
   window-resize-xxx
   window-move-xxx

*/
```

---

