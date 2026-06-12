---
title: "Finding and installing GTK+2.0 source package."
date: 2010-12-15
forum: General Help
---

### Post by thelazydeveloper on 2010-12-15
I'm attempting to debug an xchat crash, it spits the following at me when I break on gdk_x_error: 

/build/buildd/gtk+2.0-2.22.0/gdk/x11/gdkmain-x11.c: No such file or directory.

when I try to download the gtk+2.0 source package via:

sudo apt-get source gtk+2.0

it tells me no source package was found. I saw this package: [http://packages.ubuntu.com/source/maverick/gtk+2.0](http://packages.ubuntu.com/source/maverick/gtk+2.0) thought I could just apt-get it but I'm unsure why it fails and where to go from here. 

Is this the right source package that contains gdkmain-x11.c? 
If it isn't, where might I find the correct package as I've installed a  ton of gnome, glib, gtk packages along with their associated -dev/-dbg  packages.

---

### Post by mc4man on 2010-12-15
Maybe try updating your sources, no reason you shouldn't retrieve.
Though I'd generally not apt-get sources w/ sudo, just apt-get ....

Otherwise just grab the tar.gz from page, if you want - create a folder, dl all 3 (.tar.gz, .dsc, .diff.gz), cd to that folder and 
```
dpkg-source -x *.dsc
```

(you can dl thru mouse clicks ect. or just grab them w/ mouse and drop into save folder, after a few seconds dl will start

---

### Post by thelazydeveloper on 2010-12-17
Aye I ended up having to grab the source manually and use the commands as you mentioned in your post mc4man. Not sure why it wouldn't work with apt-get source though. 

Where do files downloaded via apt-get source usually end up, is there a particular directory structure adhered to? 

At the moment I've just got a stray file full of source but I'd like to file it away in its proper place so I can forget about it and still have gdb auto-find the source when I attempt to debug a file.

---

### Post by mc4man on 2010-12-21
> Where do files downloaded via apt-get source usually end up, is there a particular directory structure adhered to

If you just apt-get a source the files are  saved loosely into your home folder.
Better to create a folder, (or one folder w/ a sub folder for each source), cd to it and then run your apt-get

(don't have any spaces in path to sources if you ever intend to build from...

---

