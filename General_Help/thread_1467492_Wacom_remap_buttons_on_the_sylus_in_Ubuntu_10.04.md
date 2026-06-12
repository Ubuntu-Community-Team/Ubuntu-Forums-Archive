---
title: "Wacom: remap buttons on the sylus in Ubuntu 10.04"
date: 2010-04-30
forum: General Help
---

### Post by stephanecharette on 2010-04-30
In previous releases, I've always had to remap my Wacom stylus buttons to work as I want, where the button on the barrel is "right-mouse"click.

Back in the earlier Ubuntu 6.x and 7.x days, this is how I did it:

[http://ubuntuforums.org/showpost.php?p=3075591&postcount=5](http://ubuntuforums.org/showpost.php?p=3075591&postcount=5)

Then more recently with HAL the solution was as follows:

[http://ubuntuforums.org/showpost.php?p=6116009&postcount=3](http://ubuntuforums.org/showpost.php?p=6116009&postcount=3)

Now that HAL is gone again in 10.04, the solution that worked for me is to use the [FONT="Courier New"]xsetwacom[/FONT] tool.  Here is what I did to make the buttons work as I want:

> xsetwacom --list
Wacom Intuos 9x12 eraser ERASER    
Wacom Intuos 9x12 cursor CURSOR    
Wacom Intuos 9x12 STYLUS    


Now that I know my tablet is called "[FONT="Courier New"]Wacom Intuos 9x12[/FONT]", I ran these commands:

> xsetwacom --set "Wacom Intuos 9x12" Button1 1
xsetwacom --set "Wacom Intuos 9x12" Button2 3
xsetwacom --set "Wacom Intuos 9x12" Button3 3


By setting [FONT="Courier New"]Button2[/FONT] to the value "[FONT="Courier New"]3[/FONT]", the button on the barrel acts as a right-mouse-click.

Note that a lot of other Wacom parameters can be set this way.  Try this command to see all of the settings:

> xsetwacom --list param

(xsetwacom was already installed for me...run "[FONT="Courier New"]sudo apt-get install xserver-xorg-input-wacom[/FONT]" if you don't already have it installed.)

I hope all this helps someone enjoy their Wacom tablet with Ubuntu.

---

### Post by rabbitofdeath on 2010-05-04
excellent post! This worked flawlessly on my Panasonic Toughbook CF-19

For reference my tablet shows up as ```
Wacom ISDv4 90
```

---

### Post by stephanecharette on 2010-10-10
Also see [http://ubuntuforums.org/showthread.php?t=1588459](http://ubuntuforums.org/showthread.php?t=1588459) where I recently solved not only this problem, but the "sticky mouse click" problem in better way than having to run a script every time Ubuntu reboots.

---

### Post by locojets54 on 2011-09-09
nice little tutorial you gave here. i've looked around to try and figure out how to configure different X11 events for the buttons (to have them do something other than right click, namely scrolling). do you know where i could find a list of X events with the numbers i would have to use to set them up in xsetwacom? any help would be much appreciated, thanks.

---

