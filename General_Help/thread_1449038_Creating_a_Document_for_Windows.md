---
title: "Creating a Document for Windows"
date: 2010-04-07
forum: General Help
---

### Post by JugglinPhil on 2010-04-07
I need to print some documents I created in OO (.odt), but our printers are not Linux compatible, which means I somehow need to transfer the files to a Windows computer. I can't use the .odt files because MW can't open them (I can't install OpenOffice on the machines), and saving in either .doc or .docx does not work either because it totally messes up the document. So I tried print to file and created several pdfs, but again Adobe Reader on Windows can not open them.
I am sort of running out of ideas, and the other thing is I am not really sure if the files I created are pdfs at all. When you open them in gedit they all start with
[CENTER]%!_PS_-Adobe-3.0
[LEFT]which to me looks more like a post script file.  
Ideas welcome.
[/LEFT]
[/CENTER]

---

### Post by Yogotiss on 2010-04-07
There is an Open Office plug-in within the software center to successfully save a .odt to whatever extension you need. You can also install Microsoft Office using (WINE), I'll try to make a quick tutorial on Youtube just for you and who ever else if need be and I'll post the link here.

By the way what is the make and model of the printer?

---

### Post by arashiko28 on 2010-04-07
You don't need to print to file, on the openoffice word document, you have the option to convert to pdf at any time. Right before the printing button, you have pdf button. Also, you can install msttcorefonts and it wouldn't mess up when you do the change. 3rd option, install ms office through wine.

> [http://ubuntuforums.org/showthread.php?t=1102840&highlight=install+office+2007](http://ubuntuforums.org/showthread.php?t=1102840&highlight=install+office+2007)

Good luck

---

### Post by JugglinPhil on 2010-04-07
> **Yogotiss said:**
> There is an Open Office plug-in within the software center to successfully save a .odt to whatever extension you need.
Hey that would be pretty cool, could you tell me the name of the plug-in?

---

### Post by Yogotiss on 2010-04-07
> **JugglinPhil said:**
> Hey that would be pretty cool, could you tell me the name of the plug-in?


When you open the software center type (office --libraries), this should give you all the Open Office extension builds and libraries.

---

### Post by JugglinPhil on 2010-04-07
> **Yogotiss said:**
> When you open the software center type (office --libraries), this should give you all the Open Office extension builds and libraries.
Do you mean Synaptic or the Software Center? Because Software Center is not finding anything.

Anyway I solved the problem by choosing "Export to Pdf" instead of print to file. Thanks for everything. :)

---

### Post by Yogotiss on 2010-04-07
> **JugglinPhil said:**
> Do you mean Synaptic or the Software Center? Because Software Center is not finding anything.

Anyway I solved the problem by choosing "Export to Pdf" instead of print to file. Thanks for everything. :)

Either one is fine but I'd used the software center [Click Here]("http://i1047.photobucket.com/albums/b478/Tuxintosh/Screenshots/Screenshot.png") for a screen shot

---

### Post by JugglinPhil on 2010-04-07
Hm when I enter just the same nothing appears. Maybe it's because I am using 64?

---

### Post by Yogotiss on 2010-04-07
> **JugglinPhil said:**
> Hm when I enter just the same nothing appears. Maybe it's because I am using 64?

It shouldn't matter about the platform you have with Open Office libraries
If you have wine installed and have a copy of Microsoft Office you can follow this short tutorial I made [here]("http://www.youtube.com/watch?v=03jl1ybFy10")

---

