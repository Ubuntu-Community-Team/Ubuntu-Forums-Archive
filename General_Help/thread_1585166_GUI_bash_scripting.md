---
title: "GUI bash scripting"
date: 2010-09-30
forum: General Help
---

### Post by ekotsev on 2010-09-30
Hello, I want to start learning GUI bash scripting but I can't find the right tutorial. I'm interesting at creating menus like ex. IPTRAF or MC (midnight commander) ....

[IMG]http://articles.techrepublic.com.com/i/tr/cms/contentPics/t01820020107wal01_01.gif[/IMG]

but all i find is tutorials for KDE & GNOME. The idea is that I want to create programs that don't need X sessions. Can you help with the tutorial .... or advises ....

---

### Post by amauk on 2010-09-30
It's called ncurses, and is a standard way of emulating a GUI within a terminal window

Ncurses is a shared library, often #included in C/C++ programs (like iptraf) to provide a consistent, cross-platform console-based GUI without having to worry about the specific GUI toolkit present on the system

The bash frontend to ncurses is a program called dialog
```
sudo apt-get install dialog
```

see the man page for dialog for extensive help

*edit*
There are various other shell "frontends" to ncurses
One other one is whiptail (as used by the Debian & Ubuntu text installers)
have a look at that as well
It's got essentially the same functionality as dialog (just wrapping the ncurses functions into a program, callable from a shell script), but you may prefer it

*edit 2*
see here for some dialog examples
[http://linuxgazette.net/101/sunil.html](http://linuxgazette.net/101/sunil.html)

I'm not entirely sure how iptraf does it's complex GUI setup, with top & bottom bars as well as a menu in the centre
Possibly you get more flexibility when ncurses is used in a C/C++ program, as opposed to a shell script.
but have a play around

---

### Post by rnerwein on 2010-09-30
hi
another hint is --> have a look at zenity it's a display GTK+ dialogs tool kit ( looks nice for me ).
but dialog is nice too.
on the other side i'll agree with amauk--> Possibly you get more flexibility when ncurses is used in a C/C++ program, as opposed to a shell script.
ciao

---

