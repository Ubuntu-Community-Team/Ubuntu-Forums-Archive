---
title: "looking for text editor"
date: 2011-09-15
forum: General Help
---

### Post by omeraygor on 2011-09-15
hi.
i am looking for text editor can compare two files. 
i am using geany. but i dont know whether it can do or not.

Thanks...

---

### Post by TeoBigusGeekus on 2011-09-15
Go to Tools>Plugin Manager and enable the Split Window plugin.
Then you can go to Tools>Split Window and split geany horizontally or vertically, thus making text comparison easier.

---

### Post by omeraygor on 2011-09-15
bu i want to compare like ultraedit.

---

### Post by vasa1 on 2011-09-15
> **omeraygor said:**
> bu i want to compare like ultraedit.

Notepad ++ does that nicely in MS Windows. I ended up having to use **diff** in the terminal.

---

### Post by polki@mac.com on 2011-09-15
Meld works for me (it has a GUI even).

---

### Post by vasa1 on 2011-09-15
> **polki@mac.com said:**
> Meld works for me (it has a GUI even).

Nice! Following your suggestion, I came across this:
[http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html](http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html)

---

### Post by karen729 on 2011-09-15
> Nice! Following your suggestion, I came across this:
[http://www.webupd8.org/2011/01/how-t...gedit-for.html]("http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html")

I really prefer gedit - I use it for all of my files. With meld added to it, it just went from better to great. Thanks!

---

### Post by Habitual on 2011-09-15
> **omeraygor said:**
> bu i want to compare like ultraedit.

Unix version of UE:
[http://www.ultraedit.com/downloads/uex.html](http://www.ultraedit.com/downloads/uex.html)

It's not free software but does have a 30 day trial.

---

### Post by MG&amp;TL on 2011-09-15
I use terminator and *nano* to compare stuff.
Terminator's pretty cool if you work from command-line.

---

### Post by vasa1 on 2011-09-16
Some more on gedit + meld (which may overlap with the other link I posted):
[http://ubuntuguide.net/meld-diff-viewer-compare-and-merge-filesdirectories-in-ubuntu](http://ubuntuguide.net/meld-diff-viewer-compare-and-merge-filesdirectories-in-ubuntu)
but in the comments section, there is this:
> This is great – I’m wondering if there’s a way to automatically push the current gedit windows into meld? If I have 2 documents open, it would be nice to compare them both rather than have to browse for the second doc…
and
> I answered my own question, and found this:
[https://github.com/mmuell23/mmuell23/tree/master/gedittools](https://github.com/mmuell23/mmuell23/tree/master/gedittools)
…which puts a compare button into gedit, and if 2 docs are open pushes them both into meld!
by "Doug"

---

### Post by karen729 on 2011-09-23
@ vasa1, I installed meld using [http://www.webupd8.org/2011/01/how-t...gedit-for.html]("http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html") and then installed gedittools from [https://github.com/mmuell23/mmuell23...ter/gedittools]("https://github.com/mmuell23/mmuell23/tree/master/gedittools")
and I am very happy with the ease of install and use. Like the info says, I opened two text files in gedit. From the main toolbar > Search > Compare current file to...  Both files were opened in a meld window with the differences highlighted. Can't get much easier than that! :p

Thanks for sharing the info.

---

