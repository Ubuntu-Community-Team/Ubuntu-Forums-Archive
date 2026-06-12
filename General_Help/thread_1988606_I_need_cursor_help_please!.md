---
title: "I need cursor help please!"
date: 2012-05-27
forum: General Help
---

### Post by WyattJ on 2012-05-27
Why does my cursor show the default style when hovering on an open window but it shows a "crystal blue" style when hovering over the desktop and taskbars?
I am also kind of new to the whole scripting and Linux crowd so don't give me too many codes or commands, unless you explain it really good.


Thanks!

---

### Post by stinkeye on 2012-05-27
Firstly, I am assuming your using the crystalblue cursors from here [**_[COLOR="DarkRed"]crystalblue[/COLOR]_**]("http://gnome-look.org/content/show.php/Crystal+X+cursors?content=88455") 
Check there is a **cursor.theme** file in your downloaded theme.There wasn't in my download.
[ATTACH]218808[/ATTACH]

If not, open gedit and save this as **cursor.theme** in your downloaded theme's folder.
Check it is the same as your [COLOR="magenta"]theme folder name[/COLOR]
```
[Icon Theme]
Inherits=[COLOR="Magenta"]crystalblue[/COLOR]
```


Install your theme in **/usr/share/icons**
eg Open nautilus as root...(copy and paste in the terminal)
```
gksudo nautilus /usr/share/icons
```
Open another file browser window to where your downloaded theme is
and drag and drop your theme to the **/usr/share/icons** window.

Install galternatives..(terminal)
```
sudo apt-get install galternatives
``` 

Open galternatives (search in dash)
and click on **x-cursor-theme** in the left panel.
[ATTACH]218809[/ATTACH]


Cick on the add button then browse.
Use the top dropdown to navigate to the root directory (/)
[ATTACH]218810[/ATTACH]


Then under folders, navigate to **usr/share/icons/crystalblue**
and select the cursor.theme file. click ok.
[ATTACH]218813[/ATTACH]


Select your new theme and close.
[ATTACH]218811[/ATTACH] 


Then change your theme as you would normally using gnome-tweak-tool(Advanced Settings) or similar.
log out/in.

---

### Post by zombifier25 on 2012-05-28
There's a left-handed cursor (haven't tried it) in the repo, it's called comixcursors-lefthanded. After installing it, simply follow the above instructions, minus the downloading (the galternatives part down)

---

### Post by stinkeye on 2012-05-28
> **zombifier25 said:**
> There's a left-handed cursor (haven't tried it) in the repo, it's called comixcursors-lefthanded. After installing it, simply follow the above instructions, minus the downloading (the galternatives part down)

Does he want a lefthanded cursor???

---

### Post by vasa1 on 2012-05-28
> **WyattJ said:**
> Why does my cursor show **the default style** when hovering on an open window but it shows a "crystal blue" style when hovering over the desktop and taskbars?
...
From what I understand, there are two changes that need to be done. See these threads for more links:
[http://ubuntuforums.org/showthread.php?t=1988022](http://ubuntuforums.org/showthread.php?t=1988022).
and
[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

---

### Post by zombifier25 on 2012-05-28
> **stinkeye said:**
> Does he want a lefthanded cursor???
Sorry, posted in wrong thread. There's another thread in which OP asked for a left-handed cursor and I kinda mistook it for this one.

---

### Post by stinkeye on 2012-05-28
> **zombifier25 said:**
> Sorry, posted in wrong thread. There's another thread in which OP asked for a left-handed cursor and I kinda mistook it for this one.
Ahh ok. No problem.

---

