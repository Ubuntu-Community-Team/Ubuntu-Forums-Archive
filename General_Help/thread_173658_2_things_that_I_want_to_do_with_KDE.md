---
title: "2 things that I want to do with KDE"
date: 2006-05-10
forum: General Help
---

### Post by albox on 2006-05-10
Hi,

There are 2 things that I want to do with KDE :

First, I use the following command to launch a console usually :
konsole -schema /usr/share/apps/konsole/GreenOnBlack.schema --workdir ~/rep &

But I'd like to launch 4 consoles, one in each corner of my screen. Do you know how I can do that ?

Second, is it possible to tell KDE to launch an application on the same desktop every time. For example, I'd like to launch emacs on the desktop number 2 every time.

Thank you ;)

---

### Post by kb3hkg on 2006-05-10
in kde settings you can specify the default desktop for programs. as for konsole's you may have to just run the command 4 times, or just open it through the desktop just as many times.

---

### Post by ltmon on 2006-05-10
For the Konsoles you may be able to hack together a script using dcop.  You use emacs, so I assume you are into that kind of thing :)

Use 'kdcop' to launch the dcop browser, which allows you to run functions on programs remotely.  Look for the functions to run against the 'kwin' object, as kwin looks after the location of windows.  You can then get the id of a window with a certain title, and probably move it via the script.

To run a dcop command in bash the command is simply 'dcop <object> <function> <arguments>'.

So your bash script would launch a konsole, find it's window ID using dcop and the name of the window, move it to a corner, and then repeat 3 more times.

Good luck,

L.

---

### Post by albox on 2006-05-11
I just looked at the KDE API Reference and I think I found what I need :
[http://developer.kde.org/documentation/library/cvs-api/kdelibs-apidocs/kdecore/html/classKWin.html](http://developer.kde.org/documentation/library/cvs-api/kdelibs-apidocs/kdecore/html/classKWin.html)
static void 	setExtendedStrut (WId win, int left_width, int left_start, int left_end, int right_width, int right_start, int right_end, int top_width, int top_start, int top_end, int bottom_width, int bottom_start, int bottom_end)
static void 	setStrut (WId win, int left, int right, int top, int bottom)

Thank you ;-)

---

### Post by albox on 2006-05-11
If somebody know how to create a konsole with the API kde, i'm interested. I didn't find how to do that for the moment...
I'm also looking for an example to create an application with just one simple console...

Thank you :-D

---

### Post by ltmon on 2006-05-11
[QUOTE=albox]I just looked at the KDE API Reference and I think I found what I need :
[http://developer.kde.org/documentation/library/cvs-api/kdelibs-apidocs/kdecore/html/classKWin.html](http://developer.kde.org/documentation/library/cvs-api/kdelibs-apidocs/kdecore/html/classKWin.html)
static void 	setExtendedStrut (WId win, int left_width, int left_start, int left_end, int right_width, int right_start, int right_end, int top_width, int top_start, int top_end, int bottom_width, int bottom_start, int bottom_end)
static void 	setStrut (WId win, int left, int right, int top, int bottom)

Thank you ;-)[/QUOTE]

I think the KDE API reference you pointed to is internal functions only.  The external functions (i.e. those you can call from bash or another easy scripting language) are documented in the program 'kdcop' (run it from a terminal).  It is much easier to use dcop calls rather than writing something to directly interact with the KDE libraries.  

Cheers,

L.

---

