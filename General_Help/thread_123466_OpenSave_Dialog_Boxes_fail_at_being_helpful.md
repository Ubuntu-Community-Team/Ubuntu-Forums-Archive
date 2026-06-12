---
title: "Open/Save Dialog Boxes fail at being helpful"
date: 2006-01-30
forum: General Help
---

### Post by thessem on 2006-01-30
The default Open/Save dialog boxes within ubuntu only show places on your local filesystem, and no-where else.
From memory, when I was using OpenSuse10 (kde) the boxes gave me some of the other places in a seperate sidebar,
media:// Connected devices (Like My Computer in ubuntu)
and the important one I NEED to have is
remote:/// ( wich is basicly your networks, or most importantly, Samba)

The thing is, every single open/save dialog box within gnome gives me none of these options, just a location bar and a windows for saving stuff on my local filesystem. I gave up, and installed kubuntu-desktop (because I'd seen exactly what I want within OpenSuse's kde), and to my horror, kde had the exact same type of dialog boxes!

What I am asking, is, is there any way I can save to a samba share, in (k)(x)ubuntu, with the open/save in OO.o, firefox and thunderbird (and preferably other apps) short of using smbfs to mount at least 20 different samba shares on my local filesystem?

If there is no way to do this (Which I highly doubt) I will have to go back to OpenSuse.

P.S If anybody here wants to complain about my other thread regarding the same question, please don't. I've reposted this because the other thread was focused on OO.o's ability to use GnomeVfs, which is clearly not the problem.

P.S.S For the non accronym savy, OO.o == OpenOffice.org2

---

### Post by ow50 on 2006-01-30
For GTK/GNOME/Ubuntu:

Is this perhaps the GTK file chooser set local only property?
[http://developer.gnome.org/doc/API/2.0/gtk/GtkFileChooser.html#gtk-file-chooser-set-local-only](http://developer.gnome.org/doc/API/2.0/gtk/GtkFileChooser.html#gtk-file-chooser-set-local-only)

If so, that defaults to true (local only) and application developers would themselves have to specifically define their application's open and save dialogs to be able to access remote files. Alternatively, GTK would have to be patched to default to false for local only and as the API suggests, that causes somewhat different behaviour that could break apps.

The GTK dialogs do work with connected devices, if you mean USB memory and such, that get automounted. At least my USB stick shows up right below the CD- and floppy-drives in the open dialog.

---

### Post by sirclaudio on 2006-01-30
That is not a problem, it's what the people from GNOME decided.

---

### Post by Viro on 2006-01-30
Hmm, I don't know about Samba shares as I'm not connected to any. But as far as local media is concerned, mine shows up just fine (see attached screenshot).

---

### Post by thessem on 2006-01-30
Then what is happening on my system/sytems. Out of two computers I've installed ubuntu on, all I get is a dialog box similar to the one above, but without the left hand panel.

can anysone suggest anything?

---

