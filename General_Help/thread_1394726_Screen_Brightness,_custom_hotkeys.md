---
title: "Screen Brightness, custom hotkeys?"
date: 2010-01-31
forum: General Help
---

### Post by axima on 2010-01-31
in the power managment section there is a slider to adjust the brightness. is there anyway to set that slider to a custom shortcut on my keyboard?

my laptop has fn+up or fn+down to adjust the brightness but i want to use a external usb keyboard so that is the reason for the change in hotkeys

---

### Post by axima on 2010-02-01
surely someone has a laptop and has the same issue?

---

### Post by jacfalcon on 2011-06-15
I would also like to do this. I'm running a Cr48 and I don't have an Fn key. I'd like to just be able to use the keys already on my keyboard (F6 and F7) which have brightness icons on them.

---

### Post by jontsai on 2011-08-30
+1 I have a Samsung Series 5 Chromebook, would like to do the same.

---

### Post by Zorgoth on 2011-08-30
Try the following commands (you can hotkey them using ccsm or the keyboard shortcuts gui):

First (to install the software) - sudo apt-get install xdotool

xdotool key XF86MonBrightnessUp
xdotool key XF86MonBrightnessDown

xdotool is a program designed to mimic keyboard and mouse presses.  In this case, we're pretending we're pressing brightness up and down buttons.  This may or may not work on a computer without brightness buttons.

---

### Post by jontsai on 2011-08-30
That almost works for me. I can get the `xdotool key XF86MonBrightnessUp` command to work from a terminal, and I can program a keyboard shortcut in either CCSM and Keyboard Shortcuts to execute an arbitrary command (like F6 or F7 to run emacs). However, when I set the keyboard shortcut to execute the xdotool key command, it won't work.

> **Zorgoth said:**
> Try the following commands (you can hotkey them using ccsm or the keyboard shortcuts gui):

First (to install the software) - sudo apt-get install xdotool

xdotool key XF86MonBrightnessUp
xdotool key XF86MonBrightnessDown

xdotool is a program designed to mimic keyboard and mouse presses.  In this case, we're pretending we're pressing brightness up and down buttons.  This may or may not work on a computer without brightness buttons.

---

### Post by Zorgoth on 2011-08-30
> **jontsai said:**
> That almost works for me. I can get the `xdotool key XF86MonBrightnessUp` command to work from a terminal, and I can program a keyboard shortcut in either CCSM and Keyboard Shortcuts to execute an arbitrary command (like F6 or F7 to run emacs). However, when I set the keyboard shortcut to execute the xdotool key command, it won't work.

Try hotkeying 

bash -c 'xdotool key XF86MonBrightnessUp'
and same for down

---

### Post by jontsai on 2011-08-30
> **Zorgoth said:**
> Try hotkeying 

bash -c 'xdotool key XF86MonBrightnessUp'
and same for down

Hmm, I had to do:

bash -i -c 'xdotool key XF86MonBrightessUp'
(-i for interactive shell) inside of Keyboard Shortcuts, and CCSM didnt' work. The only problem now is that there is some lag time (about 0.5-1 second delay). If we can get it to be more zippy, I'd be a happy camper, but if not, this is still leaps and bounds better. Thanks!

---

### Post by Zorgoth on 2011-08-30
You could also make executable shell scripts:

for example you could make text files in your home folder, .brightnessup and .brightnessdown, and then they the first one has the contents:

#!/bin/bash
xdotool key XF86MonBrightnessUp

and the second is similar for Down.

Then make them executable using 'chmod +x ~/.brightnessup' and same for down, or else using "Properties -> Permissions" from nautilus and checking the executable box.

Then the commands for the hotkeys would simply be ~/.brightnessup and ~/.brightnessdown.  Maybe it would be faster?  I don't know.

---

### Post by hypertyper on 2011-09-17
I've tried the bash -i -c method and making executable shell scripts. Neither work when I try to map them to a key via the keyboards shortcuts. Both work when I run them via terminal. Trying to map the commands I get no error, with the executable shell scripts I get an "error while trying to run" with no more details.

I'm also on a Samsung Chromebook running Ubuntu 11.04.

Any ideas?

Cheers

edit: I used this mapping from CR48 and most keys work... except the brightness keys which seemed to work briefly and now even putting the xdotool commands into the terminal does nothing. I don't understand. I had installed another (xbrightness?) tool which didn't work and removed it but now it's all gone wrong. I tried reinstalling xdotools, new version says I'm on wrong architecture so back on the previous one. No luck. Any suggestions? 

I'm trying to get my head around Ubuntu and my little chromebook is a nice motivation but I'm getting frustrated...

Restored my Chromebook, installed everything again and now the bash command is working at least.

edit:
I came up with a solution:
[http://www.codetopf.com/2011/09/samsung-chromebook-ubuntu-fixing_23.html](http://www.codetopf.com/2011/09/samsung-chromebook-ubuntu-fixing_23.html)

Anybody who can change brightness through gconf-editor / ubuntu tweak should be able to use those scripts.

[http://dl.dropbox.com/u/9732528/BrightnessUp.sh](http://dl.dropbox.com/u/9732528/BrightnessUp.sh)
[http://dl.dropbox.com/u/9732528/BrightnessDown.sh](http://dl.dropbox.com/u/9732528/BrightnessDown.sh)

---

