---
title: "Openyahtzee won't launch"
date: 2011-10-28
forum: General Help
---

### Post by gregalynch on 2011-10-28
I downloaded openyahtzee from the software center and liked it a lot.  The first time I used it it worked, but the next time I tried to lauch it it didn't open.  I was getting a warning that it couldn't locate the gtk theme 'pixmap' when I ran it on a terminal, so I installed gtk2-engines-pixbuf.  Now I don't get the error message anymore, but the program still doesn't launch.  The process is running, but the window never opens.  I tried reinstalling, but that didn't work.

---

### Post by flick on 2011-10-28
Try starting it from a terminal window, often you will get error messages that may be useful in troubleshooting.

I just confirmed the bug you found. I installed openyahtzee, ran it fine the first time by starting it from the Dash, but it wouldn't start a second time from the Dash. When I tried to start it from a terminal window, I got the messages :

flick@lil-spooky:~$ openyahtzee

(openyahtzee:7369): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(openyahtzee:7369): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(openyahtzee:7369): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(openyahtzee:7369): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Workaround : looks like you MAY get it to work if you change the theme your desktop is currently using. See this askubuntu thread for details : [http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)

---

### Post by gregalynch on 2011-10-31
yep, this is exactly what happened to me.  I installed the pixbuf package listed in the thread you posted and now I don't get the error messages, but the program still doesn't launch.  I don't really want to change my theme.

---

