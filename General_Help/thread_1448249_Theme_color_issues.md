---
title: "Theme color issues"
date: 2010-04-06
forum: General Help
---

### Post by Flexico on 2010-04-06
When I customize Ubuntu's color scheme, especially when it uses light text on dark background, some places where text is ends up almost impossible to read -- because, for example, in Yahoo mail, it uses my system color for the text (light) and its own color (also light) for the buttons. Another, more intriguing example, is that when I use the "Darkroom" theme (my favorite) and make the "input boxes" dark with light text, when I rename a file, the text is black on black when I type. I figured that right in Ubuntu at least that kind of issue wouldn't happen. Any ideas on how to fix this?

---

### Post by ankspo71 on 2010-04-06
Have you tried telling firefox to not use system colors? Open Firefox then go to Edit > Preferences > Content tab, then click on the "Colors" button. Try disabling "Use system colors" and/or "Allow pages to choose their own colors..." 

I think gnome has a bug that causes dark themes not to display correctly (from what I heard). So for dark colored theme related problems in Gnome applications (gtk apps), I use the program called gnome-color-chooser. It allows us to change colors of input boxes, hover colors, selected colors, text and so on. This makes system wide changes, so changing the background color of the input boxes also effects the terminal background color, but only if the terminal is told to "use colors from system theme" in the terminal profile options. [Also gnome-look.org has "color schemes" uploaded by other users.]("http://gnome-look.org/index.php?xcontentmode=166") There aren't that many though

There are two popular firefox addons that might help too. "Stylish" and "Greasemonkey". I haven't used these before though.
Hope this helps.

---

### Post by Flexico on 2010-04-06
Adjusting Firefox's settings didn't help, but I plan to try that gnome-color program when I get time. :) Thanks!

---

