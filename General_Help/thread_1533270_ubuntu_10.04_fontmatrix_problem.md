---
title: "ubuntu 10.04 fontmatrix problem"
date: 2010-07-17
forum: General Help
---

### Post by jazzerit on 2010-07-17
I've installed Fontmatrix. It deactivates fonts correctly, but when I try to reactivate them, it does not do so, and gives this error message:
"Fontmatrix has been unable to load the font in file 
/usr/share/fonts/truetype/ttf-liberation/LiberationMono-Bold.ttf.
 Please check missing files."
It is still possible to reinstall them using Gnome Font Viewer.
Does anyone know what to do about this?
Help will be greatly appreciated!

---

### Post by jazzerit on 2010-07-24
bump

---

### Post by lkejke on 2010-09-06
Yeah, I [have the same problem]("http://ubuntuforums.org/showthread.php?t=1569084"). I deactivated ALL the fonts and now I'm stuck running on some basic system sans font. I can't reactivate anything.

So much for Linux having a good font manager.

---

### Post by kemuri1 on 2010-09-07
The described issue in Font Matrix appears due to limited functionality.
Development of this software is not yet complete.
Try something else.

---

### Post by nemoinis on 2010-10-08
Fontmatrix lets you deactivate system fonts but it does not "notice" that they are now deactivated, nor does it let you reactivate them...
To reactivate a font you've accidentally deactivated, you can edit ~/.fonts.conf and remove everything between <rejectfont> and </rejectfont>

---

### Post by JorgeGhersa on 2010-10-15
Happened to me also in Maverick. 

I'm no programmer myself, but I think what the creator of FontMatrix calles here "[experimental code]("http://fontmatrix.net/node/41")" is to blame. Basically, he intended the program to be used only on user level fonts, yet later he added a way to deactivate system fonts... without a way to bring them back.

This thread would've been very helpful an hour or two ago, while I was trying to recover the Ubuntu typeface on my system... Anyway, the tagging functionality is not worth the pain; I'll stick to using un-nested collections with FontManager.

Filed the bug [here]("https://bugs.launchpad.net/ubuntu/+source/fontmatrix/+bug/661540").

---

