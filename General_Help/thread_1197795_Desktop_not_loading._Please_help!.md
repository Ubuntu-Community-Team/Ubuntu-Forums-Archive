---
title: "Desktop not loading. Please help!"
date: 2009-06-26
forum: General Help
---

### Post by kerriejas on 2009-06-26
I had a sound problem which I resolved somehow, not sure how exactly with help from this forum ([http://ubuntuforums.org/showthread.php?t=1192529](http://ubuntuforums.org/showthread.php?t=1192529)).

now the desktop wont load. i cant see anything apart from the date and time, grey bar across the top saying ' home ' but can only acess the preferences etc. abuntu icon in top left that doesnt do anything, please help, i cant get in to my computer at all.

thanks :confused:

---

### Post by kerriejas on 2009-06-26
oh and i can not acess the internet, i am on my home pc right now.

---

### Post by siryuhan on 2009-06-26
Can you Ctrl+F2 and run gnome-panel? (Type "gnome-panel" without the quotes) Does this show the rest of your computer?

---

### Post by kerriejas on 2009-06-27
thankyou for your reply. I have tried ctrl and f2 nothing happens. i can get in to panel properties for the grey bar along the top, it brings up all files to choose a background....like 'file system' 'documents' etc.....but it looks like it only brings that up to choose a background pic/theme for panel.  ???

Is there anything i can do with the buttons when pressing power button, like 'log out' 'lock screen' suspend' hibernate' restart' shutdown'

---

### Post by HiImTye on 2009-06-27
alt+f2 brings up the 'run' dialogue

1.) type in 'gnome-panel' (it should auto-complete). this should bring up the panel with your menu, etc.

*if your panel comes back then do step 2a. if not then do step 2b.*

2a.) go to your menu>system tools>configuration editor (might be listed under 'programs' or whatever if you use the menu that is seperated into three)
2b.) press 'alt+f2' and type in 'gconf-editor' (it should auto-complete)
3.) navigate down the tree to /desktop/gnome/ and click on 'session' (don't click the arrow beside it, you want the values inside this folder not a subfolder).
4.) double click 'required_components_list'
5.) make sure that 'panel' is in this list (if not, then add it)

that's all I got for ya right now. hopefully that will help

---

### Post by kerriejas on 2009-06-27
ah i do see light at the end of the tunnel.....however.......there is no session folder.:confused:

---

### Post by HiImTye on 2009-07-04
The tree and values should be as shown in attached image

---

