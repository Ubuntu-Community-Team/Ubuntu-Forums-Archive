---
title: "How to make CD menus."
date: 2011-07-04
forum: General Help
---

### Post by Elimode on 2011-07-04
I have several documents that I would like to put on a CD.  I was wondering if there is a way to make a menu for the CD.  Are there any Application out there that will allow me to do this in Ubuntu.

---

### Post by Habitual on 2011-07-04
What would this menu "do" exactly?

There are options, but to be really helpful, we/I need to know what you plan to do as Menu **actions**?

What kinds of Documents?

Need...
more...
info...

---

### Post by Elimode on 2011-07-04
Well I have a couple of pdf document, stories that I have written.  Also there is a short movie.  The menu I want able for the use to click on links or buttons to directly open the pdf file's and movie.  I have one story called Cry, i want a link, button called Cry that is able to open the pdf file with the story in it.

---

### Post by Habitual on 2011-07-04
Well, my thought is to use yad (zenity fork) to be able to select which file you wish to open/view... I have to think some more on this avenue, so I will and perhaps someone else will contribute something in the meantime.

My brain isn't what it used to be so it may take awhile ...

how many of each filetype are we talking about?

---

### Post by Habitual on 2011-07-04
Did you want ncurses-based menu or a gnome'ish-based one? Dumb Q: "links or buttons"

Example:
(using yad, but you can get a feel for it using zenity which should be installed by default) 
```
zenity --info --title="Demo Menu Script" --text="Hello World                     "
```

and you can install yad with:
```

sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install yad

```
Shoot me a PM with your email address, this is going to be "involved"... :)

---

### Post by Habitual on 2011-07-05
Elimode:

Sadly, I have to withdraw my offer. Sorry about that.
The time and effort necessary to implement a CDMenu is way beyond the expected output. In short, it would just be the same thing as opening the contents of the menu and double-clicking any file to launch it..."Lipstick on a pig"

Have a great day.

Edit: I did manage to get a splash-screen for this idea and it remains a test-case for my bash+yad "poor-gramming" skills.

If anyone else is interested in a collaborative effort for this request, I'm listening. :)

---

