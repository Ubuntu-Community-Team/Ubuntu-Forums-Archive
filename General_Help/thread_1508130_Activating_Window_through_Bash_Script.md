---
title: "Activating Window through Bash Script"
date: 2010-06-12
forum: General Help
---

### Post by ncwilde43 on 2010-06-12
I'd like to create a bash script that's mapped to hotkey to bring up my Empathy contact list if it's on a separate workspace, mimized to tray, or hidden and hide the window if it's focused.

I think I need to use something like [FONT="Courier New"]wmctrl -l[/FONT] and [FONT="Courier New"]wmctrl -R[/FONT], but I can't figure out how to get the window status (minimized to tray, different workspace, etc.)

Example script that does not work
```
#!/bin/bash

## ---Check to see if wmctrl is installed
if [ $(which wmctrl | wc -l) -eq 0 ] ; then
    echo "wmctrl is not installed!"
    sudo apt-get -y --force-yes install wmctrl
fi

## ---See if Empathy is running
if [ $(ps -A | grep empathy | wc -l) -eq 0 ] ; then
    empathy # Run emapthy
# else
    ## ---Check emapthy window status
    # if minimized || different workspace
        # wmctrl -R "Contact List"
    # else 
        ## ---Minimize window
        # wmctrl -c "Contact List"
fi
```
Any help would be appreciated!

---

### Post by Jeroensum on 2010-06-18
There is no need to get the status of the window, just execute the wmctrl -R "window name" command and it will go to the desktop where the window is on and activate it, then close it. The -c option closes the window, you should play around with womething like
wmctrl -r "winow name" -b add,hidden
to hide a window

---

