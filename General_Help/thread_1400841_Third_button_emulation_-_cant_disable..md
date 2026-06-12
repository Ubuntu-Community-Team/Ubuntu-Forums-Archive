---
title: "Third button emulation - cant disable."
date: 2010-02-07
forum: General Help
---

### Post by marmilho on 2010-02-07
Hello. Ive been trying to disable the third button emulation using xinput but to no avail... I just dont know how to config it.

to put simple:

```
marm@linux-desktop:~$ xinput list | grep 'id='
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"ImPS/2 Generic Wheel Mouse"	id=3	[XExtensionPointer]
"Power Button"	id=4	[XExtensionKeyboard]
"Power Button"	id=5	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
marm@linux-desktop:~$ xinput get-button-map 3
1 2 3 4 5 6 7 
marmlinux-desktop:~$ xinput set-button-map 3 ??????
```

????? being what do I do here? 

Or Im going the wrong way there?

Thanks in advance.

---

### Post by marmilho on 2010-02-07
By the way. I forgot to mention I'm using 9.10 (karmic koala)

On later versions it was donne editing xorg.conf right? Now my xorg.conf is pretty much empty

---

### Post by marmilho on 2010-02-08
Come on guys, please? I really need to disable this emulation.

---

### Post by ledomira on 2010-03-17
I don't know which mouse you want to disable it for, but the command to enable it is:  Evdev Middle Button Emulation (231):    2


So, type: xinput list.  
Find the mouse you want to edit.  Then type: xinput set-int-prop "whatever the name of the mouse is" "Evdev Middle Button Emulation" 0

That should disable it.

---

