---
title: "eclipse not opening files in eclipse"
date: 2010-09-11
forum: General Help
---

### Post by Adrienk on 2010-09-11
I recently had to reinstall Eclipse on ubuntu 10.10 and i did it twice, once just removing eclipse package, and the second time removing every package associated with an eclipse install.

when i launch eclipse I go into my package view and select a package and then double click on a Java file.
it opens in gedit even though eclipse is open.


help?

---

### Post by GregBrannon on 2010-09-11
Is that how you used to use Eclipse, before you uninstalled and reinstalled?  Eclipse typically complains when you try to open more than one .java file that way, because it says that it can only open one Eclipse application at a time.

So, better than double-clicking to edit a .java file in Eclipse, start a project and add .java files to it.

But if you must get the functionality you describe, associate .java files so that they open with Eclipse by default.  I use KDE, so your instructions might be different, but there are at least two ways in my DE: set file associations in desktop setup, advanced (I think) OR right click on a .java file, select "open with," choose eclipse, and then check the box that says to open with this application as the default application.  Your process should be similar.

Let us know if this doesn't work for you.

---

### Post by Adrienk on 2010-09-11
I don't think you understood what I wrote or I was confusing.

a month ago I installed eclipse, made a workspace called java and started creating projects.  you all know that after you create a project with packages, and class files **NOT IMPORT THEM BUT PHYSICALLY CREATE IT FROM SCRATCH** you can close eclipse,re-open it and your files are still there. you double click them and the **open in eclipse.**  ("double click them" refers to the class files and other associated files you created in eclipse).

Well yesterday I had to re-install eclipse. upon doing so, I opened eclipse to see that (yay) it opened to the same workspace as I created originally before re-installing.

So i went on as normal, I double clicked a file expecting it to open in eclipse (**this is double clicking a file inside the eclipse IDE package explorer**, not out side the IDE. (I think thats where the guy who responded got confused, he must have though I double clicked it **OUT SIDE**, when in fact I mean **INSIDE**).

So upon doing that and expecting it to open **INSIDE **eclipse, it opened in Gedit....

which it has never done before the re-install.


Hope this in depth explanation clears things up.

---

### Post by Adrienk on 2010-09-11
How do I make it so that ALL java files open with eclipse? instead of "right click each and every individual one"?

---

### Post by Adrienk on 2010-09-11
bump

---

### Post by GregBrannon on 2010-09-11
Yes, that guy who responded was confused. Your additional explanation significantly reduces the confusion.

My version of Eclipse has 4+ configurable editors.  If you right click on one of your source files in the project structure and select Open With, you'll be given the choices, Java Editor, Text Editor, System Editor, and Default Editor.  Mine is defaulted to select the Java Editor which means the Eclipse Java Editor.  If I select System Editor, the file will open in Geany, my system's default text editor.

Knowing that, I'm guessing that your Eclipse editor choices are not configured now as they were in your previous Eclipse install OR the default editor is not the Eclipse Java editor.  I tried to find where either of these items - either the default Open With editor choice or the default Eclipse Java editor - were configured, and I've given up.  Eclipse preference menus seem to never end.  Perhaps consulting the Eclipse documentation will help.

I suggest you look through the menus I've described above, your Eclipse preferences, and the Eclipse documentation to see if you can figure out how to change the preferences to work as you'd like.

---

