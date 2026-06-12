---
title: "Setting Default Applications"
date: 2006-04-02
forum: General Help
---

### Post by tspec on 2006-04-02
This is probably just a quick simple thing I haven't figured out how to do yet but is there a way I can specify when I open a certain file type, which application it will open in by default? This is in reference to quicktime files, i use totem-xine which seems to work for everything except files using quicktime7. I installed vlc which has no problem playing them but by default the files still want to open in totem-xine... i can of course right click on a file and open in vlc that way but it'd be nice to set up some kind of rule for .mov files that forces them to open in vlc.

---

### Post by ESPOiG on 2006-04-02
right click on the file u want to open and goto Open With and just add the program you want to open it by default, then make sure the little radio button is clicked and it will open in that program everytime :D

hope this helps

---

### Post by tspec on 2006-04-02
thanks... i knew about adding them via the right click menu but can only get them in the list when right clicking, I'm not sure where these radio buttons are you mentioned in terms of setting it as a default app... if the radio button is located in the right click -> properties area then im sh*t out of the luck as everytime i go to the properties of a quicktime file natilus crashes :)

---

### Post by nanotube on 2006-04-02
yep, that's when you go to rightclick>properties. so i guess you are SOL. 
if only i knew where nautilus ends up storing those preferences. there must be a text file somewhere with all that stuff.

---

### Post by tspec on 2006-04-02
ah ha, i see where it's located... checked with another file type. odd that it only  crashes with quicktime7 files (works with other types of quicktime files), if i had to take a pot shot guess as to why it's crashing, i'd say it's because it's trying to load a "preview" picture in the properties box and is barfing on attempt as quicktime7 encoded files are the only video files i have that don't show a preview picture in the general file browser... so yeah, if anyone has any suggestions on how to edit it manually, it'd be greatly appeciated :)

---

### Post by nanotube on 2006-04-02
well, how about this:
1. turn off all previews
2. go to the properties box and change your associations
3. turn previews back on if you really want to (personally, i keep them off cuz it eats resources)

see if that works. :)

---

### Post by tspec on 2006-04-03
Guess thats the obvious thing to do :) i seem to be in a non thinking mode today for some reason. Anyway i did try that but it made no difference, so i guess it's not related to the previews. Looks like it's going to be more difficult to solve than i originally thought so im not really fussed about having to right click on the file to open it, maybe it'll be magically fixed in dapper :) this only seems to happen on my laptop, all works fine on my PC. Thanks for all your help.

---

### Post by nanotube on 2006-04-03
hrm, i guess i found the solution to your problem. it was just a quick google search away. check out this link:
[http://www.ces.clemson.edu/linux/fc4_desktop.shtml#gfass](http://www.ces.clemson.edu/linux/fc4_desktop.shtml#gfass)
this will show you all the files you need to edit to correct your association. specifically, ~/.local/applications/defaults.list
~/.local/applications/mimeinfo.cache
try that and see if that works. :)

---

### Post by tspec on 2006-04-03
wonders never cease. it just took editing the defaults.list file. thanks heaps for your help.

---

### Post by nanotube on 2006-04-03
no probs. i learned something while investigating this, too. so we are even. :)

---

