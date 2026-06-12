---
title: "can I add a toggle button to the new Nautilus location bar?"
date: 2010-05-31
forum: General Help
---

### Post by metalf8801 on 2010-05-31
Before Ubuntu 10.04 there was a toggle button for the location bar on Nautilus but for some reason it was removed and I'm wondering if its possible to add a toggle button to the new version of Nautilus? 

Thanks 
Dan

---

### Post by ks07 on 2010-05-31
I liked that feature too, however from what I've read so far on the matter it was removed upstream, so to get it back would not be simple. I guess we're stuck with ctrl+L, unless you want to permanently disable the breadcrumbs in preferences. :(

---

### Post by gadolinio on 2010-05-31
There's a way to at least get the functionality back, using gconftool.  You have to create a new empty file, and open it with gedit text editor.  Make the file's content like this:



#!/bin/bash

SHOW=$(gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry)
if [ $SHOW = "true" ] ; then
   gconftool-2 --set /apps/nautilus/preferences/always_use_location_entry --type=bool false
else
   gconftool-2 --set /apps/nautilus/preferences/always_use_location_entry --type=bool true
fi    


Save it. And finally create a launcher to that script. The  launcher's command should be:
sh /PATH_TO_SCRIPT/FILENAME. And in "type", choose "Application in  terminal".
That way, the launcher becomes pretty much the same as that button we  miss XD
but it will be in the panel instead of being by the location bar. I  guess it's something...

---

### Post by stinkeye on 2010-05-31
I've found it's not really needed.
If you right click on a file or folder and copy you can then paste the location into a text editor or terminal.

---

### Post by metalf8801 on 2010-06-01
> **stinkeye said:**
> I've found it's not really needed.
If you right click on a file or folder and copy you can then paste the location into a text editor or terminal.

Its true that the toggle button is not needed but it would be nice to have it there again.

---

### Post by stinkeye on 2010-06-04
You can install Nautilus Elementary (2.31.1).
Adds a customizable toolbar including a location toggle button.

Guide here:[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/06/nautilus-elementary-2311-now-with.html[/COLOR]_**]("http://www.webupd8.org/2010/06/nautilus-elementary-2311-now-with.html")
If you have any errors, check the comments for a solution.

---

### Post by metalf8801 on 2010-06-06
> **stinkeye said:**
> You can install Nautilus Elementary (2.31.1).
Adds a customizable toolbar including a location toggle button.

Guide here:[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/06/nautilus-elementary-2311-now-with.html[/COLOR]_**]("http://www.webupd8.org/2010/06/nautilus-elementary-2311-now-with.html")
If you have any errors, check the comments for a solution.

Thank you thats just what I've been looking for

---

