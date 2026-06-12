---
title: "Wacom Intuos4 mapping buttons in ubuntu 11.04"
date: 2011-07-07
forum: General Help
---

### Post by tonqua on 2011-07-07
Hi,
I got a Wacom Intuos4, I remapped it to the dual monitor.
I'm now trying to set the buttons to shortcuts like ctrl, ctrl+space, right click, etc.
I have no idea where to start.

[I]xinput list-props "Wacom Intuos4 4x6 stylus"
[/I]tells me:
[I]Wacom Button Actions (569):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
[/I]
any idea how I can asign shotcuts to the wacom buttons?
Thank you.

---

### Post by Favux on 2011-07-07
Hi tonqua,

That's discuseed some on the OLED thread:  [http://ubuntuforums.org/showthread.php?t=1380744](http://ubuntuforums.org/showthread.php?t=1380744)  along with getting the OLEDs working.
And the Intuos4 thread:  [http://ubuntuforums.org/showthread.php?t=1120029](http://ubuntuforums.org/showthread.php?t=1120029)
You'd probably want to start at the ends and work your way backwards on both.

There is a sample xsetwacom script in post #2 of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also the Linux Wacom Project's mediawiki [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") and [HOW TO]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") pages.  And since you have Natty's X server 1.10 you can actually do some button configuration in xorg.conf.d if you wanted to.

---

### Post by tonqua on 2011-07-09
Favux to the rescue,
thank you very much for the links,
I used the two Linux Wacom Project's mediawiki [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") and [HOW TO]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") links and managed to set up the Intuos4

I needed to rotate my tablet and map it to the right ratio for the dual monitor set up. I got there by more or less blind trial and error following the transformation matrix method in the HOW TO link, I'm still not sure exactly what everything does.

First I rotated the tablet to have the buttons on the right hand side:
```

xinput set-prop "Wacom Intuos4 4x6 stylus" --type=float "Coordinate Transformation Matrix" -1 0 1 0 -1 1 0 0 1
```I then squished it vertically so the proportions would match my dual monitor setup. First I needed to find by how much I had to divide the height.
```

xinput list-props "Wacom Intuos4 4x6 stylus"
``` gets me the tablet resolution:* Wacom Tablet Area (564):    0, 0, 31496, 19685* which is a 31496/19685=1.6 ratio

my total dual monitor area according to```
xrandr
``` is 3520 x 1080 or 3.2 ratio

so the transformation matrix method became:

```
xinput set-prop "Wacom Intuos4 4x6 stylus" --type=float "Coordinate Transformation Matrix" -1 0 1 0 -2 1 0 0 1
```That mapped it correctly but it mapped it to the lower portion of the tablet. It's more confortable when its higher up so I moved it to the top of the tablet area. 
```
xinput set-prop "Wacom Intuos4 4x6 stylus" --type=float "Coordinate Transformation Matrix" -1 0 1 0 -2 2 0 0 1
```So now the tablet is correctly rotated 180 degrees and my circles are round.

I still need to change the buttons,
Having some trouble there,
Will post updates.
Thanks.

---

### Post by tonqua on 2011-07-09
All right,
Following the mediawiki [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") link, mapping the buttons go like this:

[I]xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 "key ctrl"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 3 "key alt"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 4 "key shift"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 5 "key ctrl alt shift o"  # Gimp brush down
xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelDown "key shift plus"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 1 "key 1"  # button inside touchring, zoom 100%
xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelUp "key minus"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 6 "key ctrl alt shift p"  # Gimp brush up
xsetwacom set "Wacom Intuos4 6x9 pad" Button 7 "key backspace"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 8 "key ctrl s"  # save
xsetwacom set "Wacom Intuos4 6x9 pad" Button 9 "key ctrl z"  # Undo in Gimp

[/I]I mapped it differently since I mainly use Mypaint but it seems to work fine.

Thank you Favux for the links

---

