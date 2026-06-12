---
title: "workaround for nvidia-setting crash on xorg.conf write"
date: 2009-10-04
forum: General Help
---

### Post by bcurry on 2009-10-04
For those of us who have updated to the Karmic Beta and have found that nvidia-settings crashes when you try to overwrite xorg.conf, I have found an easy work around.

I'm pretty new to posting to the forums, so forgive the formatting.  I'm doing the best that my geeky self can do.  I'm writing for noob's by using as many GUI's as possible.

On a fresh reboot open your favourite terminal 3 times

on the 1st terminal

> nvidia-settings

on the 2nd terminal

> sudo nautilus

on the 3rd terminal

> sudo gedit

Each of the sudo commands will ask for you password to have those GUI's opened with root permissions.  Use caution when using root permissions.

Now, minimize all the terminals to get them out of your way and you should have 3 things open:  Nvidia settings, nautilus in the root home and a gedit.

On the nautilus screen look for the "File System" option on the left column and click it.  Then go to /etc/X11 and find xorg.conf.
Right click xorg.conf and rename it to sumpin' you like.  I used "xorg.conf.orig".

On the nvidia-settings gui, set up your screen(s) in your favourite configuration.  On the "X Server Display Configuration" select "Save to X Configuration File", don't worry, since you don't have an xorg.conf file, this time it should not crash.  

A window will pop up.  Click "Show Preview".  This is the data that should be in your new xorg.conf file.  place your cursor any where in the text area and hit "ctrl-a" to select all the data.

On your gedit screen, middle click to paste the data into gedit.  Click File then Save.  Surf to Xll directory as instructed above and save the document as "xorg.conf"

...and you're done!  Next time you reboot you'll have all your handy-dandy nvidia settings without having to go through the nvidia-settings dialogue every time you reboot!

---

