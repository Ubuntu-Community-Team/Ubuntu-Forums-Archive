---
title: "how do i show/unhide the main panel from a console?"
date: 2010-12-31
forum: General Help
---

### Post by linuxd00 on 2010-12-31
hi!
 
i set up my panels so that i have a bottom panel (windows style) and i set it to autohide.

I'd like to be able to press the windows key (Super_L) to show it just like when you hover the mouse to the bottom of the screen.


so far i have been only able to set a keyboard shortcut to show the ubuntu menu... but it will only make the menu pop up while the panel remains hidden. :\

I need this because im using a tablet pc and i want to be able to press the buttons on the panel :)

any ideas how to do this?

---

### Post by TeoBigusGeekus on 2010-12-31
...Wrong thread...

---

### Post by mc4man on 2010-12-31
You could, if you wish, do something along these lines, will give ex. on how I'd do - 

Easiest with a bin in home folder that's in path  - to do that this and restart
```
mkdir bin
```

Then create a text file in ~/bin with a simple name, usually best to add a number so not reusing a possible linux command, in this case I named toogle1
Using this as a script
```
#!/bin/bash
key_value=$(gconftool --get /apps/panel/toplevels/bottom_panel_screen0/auto_hide)
echo $key_value | grep "false"
if [[ $? -eq 0 ]] ; then
	gconftool --type Boolean --set /apps/panel/toplevels/bottom_panel_screen0/auto_hide true
else
	gconftool --type Boolean --set /apps/panel/toplevels/bottom_panel_screen0/auto_hide false
fi
```

Then r.click on and make executable (or chmod +x ~/bin/toogle1

Then just create a keyboard shortcut, (and or desktop 'switcher') that uses a command of 
toogle1
Using will do the opposite of current state, in this case either hide the panel by enabling autohide, or expose by disabling autohide

Edit: had to look up - thanks go to hamidaddin for basic idea of a toogle switch

---

### Post by linuxd00 on 2011-01-09
hi thanks for the script... i just came to use it..

but it doesnt work :\

if i run it, it alternatively outputs the word "false" or does nothing.

the panel remains in autohide mode.

using Maverick 64.

maybe after toggling the value it is needed to do a refresh?

---

### Post by linuxd00 on 2011-01-14
edit: how do i delete this?

---

### Post by linuxd00 on 2011-01-14
YEAH! it works now.. turns out the panel is "top" even though its on the bottom...

it works as intended now!

attached for anybody who wants it

---

