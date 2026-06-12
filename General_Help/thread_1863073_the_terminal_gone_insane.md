---
title: "the terminal gone insane"
date: 2011-10-17
forum: General Help
---

### Post by Amgad elsaiegh on 2011-10-17
i opened my computer today and found the fonts of terminal went too ugly /unreadable although i did not tweak any thing lately , take a look at it :


[IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/Screenshotat2011-10-17172640.png[/IMG]


any explaination how to solve this ? / why it happened ?

---

### Post by 2F4U on 2011-10-17
What happens if you choose a different font for the terminal?

---

### Post by Amgad elsaiegh on 2011-10-17
i restored it back when entered the terminal profile prefrences and removed the tick in front of > use the system fixed width font

the weird thing is that i did not tick it at first place , this is weird , 

thanks for help

---

### Post by mcduck on 2011-10-17
Your terminal is set to a variable-width font, while only monospace (fixed-width) fonts work correctly for command-line interfaces.

Change the font to any monospace font and things will look a lot better again.

(The explanation is that command-line interfaces don't flow the text like a text editor would, for example, but instead the interface is built of rows and columns of characters, each row and column being exactly the same width and height. And for that to work you need to use a font where each letter takes the same amount of space. So the letter "i" uses as much horizontal space as letter "O" does. On a variable-width font "i" is considered much narrower than "O", and that kind of fonts just don't work with the fixed row/column arrangement.)

edit: Ok, you got it solved. That's great. :) Anyway, that checkbox is marked by default. Perhaps you used gnome-tweak-tool to change your fonts, and set the system fixed-width font to some font that actually *isn't* fixed-width?

---

### Post by Amgad elsaiegh on 2011-10-17
thanks for the explanation, the trick worked well :D

---

