---
title: "fonts dillema"
date: 2011-10-31
forum: General Help
---

### Post by Amgad elsaiegh on 2011-10-31
i wanted to make some tweaks in fonts cause arabic font in ubuntu really sucks so i searched for font settings but i found nothing useful so i googled it and found that i should install a tool called GNOME TWEAK [how an operating system can`t change its font without a third-party application] ,after opening it i found many font types like the image below 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/fonts.png[/IMG]
[/CENTER]
i wanna know which one is used in web-browsers ?? and i wanna know **what is a monospace font ???**

i will give some examples here to show why arabic font in ubuntu sucks , 

[SIZE="3"]**the first example**[/SIZE] is a text written in windows in arabic , here is a screenshot of the proper look of it 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/notepad.jpg[/IMG]
[/CENTER]
and here is how it looks in ubuntu: 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/Screenshotat2011-10-31174946.png[/IMG]
[/CENTER]

total crap, isn,t it?? 


[SIZE="3"]**second example** :[/SIZE] this is a screenshot of a page written in arabic in windows{proper look} using opera 11.52:

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/operawin2JPG.jpg[/IMG]
[/CENTER]
and this is the same page on Ubuntu {using opera 11.52 too}

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/operalinux2.png[/IMG][/CENTER]

link to this page [http://www.almesryoon.com/news.aspx?id=84692](http://www.almesryoon.com/news.aspx?id=84692)

[SIZE="3"]**third example **:[/SIZE] another example from facebook , here ubuntu reads arabic letters correctly but in an extremely ugly font that stress your eyes, make you don`t wanna surf the internet at all ](*,) , take a look at the difference between windows and Ubuntu yourself :

in windows : {the right look} 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/operawin.jpg[/IMG]
[/CENTER]
in ubuntu : {the ugly look} 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/fblinux.png[/IMG][/CENTER]


any help ? how to make things right in ubuntu ?

** i am using ubuntu 11.10 32-bit

---

### Post by gsmanners on 2011-10-31
If you look in the "Edit / Preferences" in gedit, that should have a tab for Fonts and Colors. Plus, I'm not sure, but Opera ought to have its own settings for fonts, as well.

---

### Post by Amgad elsaiegh on 2011-10-31
thanks gsmanners for replaying , i tried changing the font in gedit to Arial like windows but nothing happens, result still the same :confused:

---

### Post by christopher.wortman on 2011-10-31
You need to download and install the language packs in order to work in Arabic in Ubuntu. Sometimes during the installation it fails on one language say Japanese and doesn't install any of them lol. 

> sudo apt-get install language-pack-ar

I have seen it with new releases especially if you install within the first week after an upgrade lol.

[http://www.1001freefonts.com/arabic-fonts.php](http://www.1001freefonts.com/arabic-fonts.php)

Also you can install these fonts  using the instructions here:
 
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by Amgad elsaiegh on 2011-10-31
hey christopher.wortman :D
the arabic language pack is already installed , take a look :

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/ar.png[/IMG][/CENTER]

---

### Post by gsmanners on 2011-10-31
Might be an encoding issue for gedit. I'm pretty sure gedit can only handle UTF8.

EDIT: Here's a pic of me copy-pasting from wikipedia.

---

### Post by mcduck on 2011-10-31
First, Gnome-tweak-tool is not a third-party application, it's official part of the Gnome 3, it's just that Gnome developers choose not to include it by default.
[http://live.gnome.org/GnomeTweakTool]("http://live.gnome.org/GnomeTweakTool")

Anyway, the fonts used on web pages are not affected by these settigns, they are defined by your web browser, and of course the web page itself (to the limit of what fonts you actually have installed). The web page can suggest a list of fonts, from which the browser tries to sue the first one. IF that's not available on your system, it tries the second one, and so on until finally choosing whatever font is defined in the browser's settings for that certain type of purpose. If you want, you can usually force all web pages to ingore this font selection mechanism and only use the fonts you have designated in the browser's preferences.

Finally, monospace fonts are used for command-line interfaces, and quite commonly for text editors as well. They are fonts where every letter uses the same amount of space (so for example "I" takes as wide space as "O" does), which is required for the way how command-line interfaces work.

What comes to your text problems, are these texts written originally in Windows? Ubuntu assumes UTF8 by default, as it supports all languages at the same time. Windows on the other hand tends to use language-specific character sets instead. You might need to convert the texts written in Windows into UTF8, or specifically tell Gedit to use the same character set you used in Windows. (Or use a Windows text editor that supports UTF8)

---

### Post by Amgad elsaiegh on 2011-11-01
@gsmanners : yes gedit gives me the same result if the text file is written in ubuntu , but the problem is that it is written in windows 

@mcduck: first, thanks for replaying , i understood your explaination well, but what you are not aware of is that most text files comes from friends or from the web are written in windows so this is a nightmare, even movies subtitles in many cases do not display correctly because they are written in windows too

**[COLOR="DarkRed"]is there a text viewer in ubuntu that display these files correctly ?[/COLOR]**


my question to **ubuntu staff** is why they do not support both systems to make life easier on non geek users like me ???

finally , i think arabic fonts needs some work and needs to be improved in 12.04, don`t you agree with me ?

---

### Post by mcduck on 2011-11-01
Sure, if the fonts aren't working correctly automatically then of course that's something that should be improved to meet Ubuntu's design philosophy. (The actual issue is likely to fall under Gnome developer's responsibility though, not Ubuntu devs.)

Anyway, this plugin for Gedit might be useful for you: [http://code.google.com/p/gencodingconverter/]("http://code.google.com/p/gencodingconverter/")

What comes to supporting both systems, as far as I know Windows should mostly be using (or at least support) UTF8 as well these days, as do every other platform. Notepad however is known for it's terrible handling of text encodings (as well as being terrible editor in general :D ). Sadly fixing that might be impossible. ;)

---

### Post by gsmanners on 2011-11-01
> **mcduck said:**
> What comes to supporting both systems, as far as I know Windows should mostly be using (or at least support) UTF8 as well these days, as do every other platform. Notepad however is known for it's terrible handling of text encodings (as well as being terrible editor in general :D ). Sadly fixing that might be impossible. ;)

I don't think it's fair to say that Windows is deficient because of its lack of UTF8 support, considering it didn't really become a finalized standard until around late 2003.

[http://en.wikipedia.org/wiki/UTF-8](http://en.wikipedia.org/wiki/UTF-8)

---

### Post by Amgad elsaiegh on 2011-11-01
i tried the encoding tool you provided me mduck but it didn`t install successfully , it seems to be not updated for gnome 3 yet :confused: , take a look at the picture below

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/terminal.png[/IMG][/CENTER]

---

### Post by Vaphell on 2011-11-01
you know you can copy-paste the text and put it in [code] tags?

either way, in windows arabic is supposedly encoded with win-1256 charmap. In gedit in 'open' window there should be a dropdown with encodings at the bottom. Add win-1256, select it and then try to open the file.

---

### Post by Amgad elsaiegh on 2011-11-06
thank you **vaphell** for replaying the trick you said about converting the encoding is working and below is a screenshoot , but it is very annoying to open each file from file menu then open then changinging the encoding to arabic win-1256 everytime i open a file , this sucks , why don,t the ubuntu staff solve the problem from the os itself?? :confused:

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/texteditor.png[/IMG][/CENTER]


*** i tried to search for an alternative text viewer/editor , i used one calld geany and altough the first result was very good like the image below but , 

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/geany.png[/IMG][/CENTER]

**on testing more documents , it failed on some of them like below**

[CENTER][IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/geanyfail.png[/IMG][/CENTER]

[SIZE="4"]i hope ubuntu team do something about that in their next release .[/SIZE]

---

