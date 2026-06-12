---
title: "problem with Glade and XML"
date: 2010-09-19
forum: General Help
---

### Post by xtremesupremacy3 on 2010-09-19
Hey there,

I have been doing bash a while and fell in love with Python too.
But there is only so much you can do with CLI on python. There comes a time it has to look shiny too.

My first question is, is Glade the best and easiest way to make quick GUI's?

And secondly, I have tried a few tutorials for Glade but always run into the error that once the GUI has been designed and been implemented in the python code, I get the following error everytime:

```
(tutGUI.py:14353): libglade-WARNING **: Expected <glade-interface>.  Got <interface>.

(tutGUI.py:14353): libglade-WARNING **: did not finish in PARSER_FINISH state
Traceback (most recent call last):
  File "tutGUI.py", line 57, in <module>
    letsdothis = leeroyjenkins()
  File "tutGUI.py", line 30, in __init__
    self.wTree = gtk.glade.XML( "main.glade")
RuntimeError: could not create GladeXML object

```

Anyone have any idea on whats going wrong here?

I don't just get it with this python code, but also with just about every tutorial I follow

Arthur

---

### Post by Brandon Williams on 2010-09-20
The tutorials you're using are probably assuming the you specified a Libglade project, but the latest version of glade defaults to GtkBuilder. With the project open, click edit -> preferences and select Libglade as the project file format. Then save the project and try to run your program again.

If this works, then you might want to look for a more up-to-date tutorial, since the ones you're using were apparently written before GtkBuilder.

---

### Post by xtremesupremacy3 on 2010-09-20
I did indeed install glade through the ubuntu repos and have version

glade3 3.6.7

---

### Post by Brandon Williams on 2010-09-20
> **Brandon Williams said:**
> If this works, then you might want to look for a more up-to-date tutorial, since the ones you're using were apparently written before GtkBuilder.

Even though GtkBuilder is the way of the future, I realize that there are more tutorials out there that use libglade. Until glade-3.6, glade didn't even have builtin support for GtkBuilder (which is why your libglade tutorials don't mention this). [Here](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html) is one simple one. You won't need to use gtk-builder-convert any more, since your version of glade will save to GtkBuilder format for you already.

---

### Post by xtremesupremacy3 on 2010-09-20
Thanks for the reply and the link, will try it out.

I have to say though that the tutorial told you to use GTKBuilder not libglade.

Anyway,

Thanks...SOLVED

---

### Post by rvkbob on 2012-10-31
Hi guys.

I'm just now trying to get glade 3.12.1 to open my old glade files which are stored in lib.glade format. After reading and rereading the forum entries, I find that this new version of glade does not iniclude an optiion to edit preferences anywhere in the edit menu (or anywhere else that I can find). 

I downloaded this version of glade from the Ubuntu Software Center. Is there a different version somewhere that I should perhaps be using? I require compatability with the lib.glade format for multiple reasons, the most pressing one being that I have software which converts only that format into FreeBASIC source code. So I'm stuck until I learn how to get glade to load, edit, and save files in lib.glade format.

Thanks,
Bob

---

