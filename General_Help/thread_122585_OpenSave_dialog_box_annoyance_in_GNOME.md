---
title: "Open/Save dialog box annoyance in GNOME"
date: 2006-01-28
forum: General Help
---

### Post by thessem on 2006-01-28
When trying to open a document I have stored over a SMB share I found there is no support in the open/save dialogs have no support for saving to anywhere other than your local filesystem.

Basicly, what I'm asking, is if there is some hidden menu or something to save to other places. If somebody who isnt very good at linux tried to open a cd or something, how would they now its under /media/cdrom0?

Basicly, If you can't be bothered reading this entire post, is there anyway I can save to the location "remote:///" in gnome, with applications such as OpenOffice.org, firefox, and thunderbird?

---

### Post by doclivingston on 2006-01-28
The reason for those applications not being able to save to remote (e.g. smb://) file systems, is that they don't support GnomeVFS. Any applications that have full GnomeVFS support can save to remote places.

OpenOffice, Firefox, Thunderbird and a lot of other applications don't have GnomeVFS support, for a number of reasons, including:
 * Changing the program to use it may be difficult.
 * It means that the application will depend on GnomeVFS, so you can't use the application without (at least some of) the Gnome platform installed.

---

### Post by thessem on 2006-01-28
Is there _any_ workaround I can use, because opening remote documents in openoffice is something I do ver often, and I dont have time to manually copy the files locally.

---

### Post by engla on 2006-01-28
[QUOTE=doclivingston]The reason for those applications not being able to save to remote (e.g. smb://) file systems, is that they don't support GnomeVFS. Any applications that have full GnomeVFS support can save to remote places.

OpenOffice, Firefox, Thunderbird and a lot of other applications don't have GnomeVFS support, for a number of reasons, including:
 * Changing the program to use it may be difficult.
 * It means that the application will depend on GnomeVFS, so you can't use the application without (at least some of) the Gnome platform installed.[/QUOTE]
I'm not a gnome developer (yet?) so I don't really have a clue, but why can't these applications use GnomeVFS on basis on the availability of the library? Firefox for example could check for the GnomeVFS lib and dynamically link to it, and if it doesn't find it it just cuts out those parts of the code...

---

### Post by thessem on 2006-01-28
[QUOTE=engla]I'm not a gnome developer (yet?) so I don't really have a clue, but why can't these applications use GnomeVFS on basis on the availability of the library? Firefox for example could check for the GnomeVFS lib and dynamically link to it, and if it doesn't find it it just cuts out those parts of the code...[/QUOTE]

You know, thats exactly what I'm thinking right now.

This problem is severe enough to make me go back to windows. At least I can open files across a network there.

I would install KDE, because I know it does exactly what I want here, but I can't be bothered getting it to look nice.

Is there any way I can set it up so KDE's open/save dialogs come up instead of gnomes ones in programs like openoffice?

---

### Post by doclivingston on 2006-01-28
> I would install KDE, because I know it does exactly what I want here, but I can't be bothered getting it to look nice.

That only works if the application uses KIO (which KOffice and conqueror do).


> Is there any way I can set it up so KDE's open/save dialogs come up instead of gnomes ones in programs like openoffice?

No, because it isn't the open/save dialogs that are the problem - it's the applications not knowing how to access the files across the network. The applications could be changed to use KIO, which could let them do it, but that is exactly the same as changing it to use GnomeVFS (aside from the different library).

The way to fix it properly is to complain to the application authors, and convince them to use GnomeVFS (for Gtk/Gnome applications) or KIO (Qt/KDE applications).


The other solution would be to mount the network shared using the mount command from a terminal, or an entry in /etc/fstab - so the standard C IO functions can access it.

---

### Post by thessem on 2006-01-28
Ok. I'm pretty sure that OpenOffice uses KIO then, because I could do all the saving via networks back when I was using suse (KDE based).

I think I may have to just go down the smbfs road, it will get what I want it to do done, but it will just be abit more difficult.

Thanks anyway doclivingston, I'm certainly alot less ignorant of all these things than when I started this thread.

---

### Post by doclivingston on 2006-01-28
Actually, I think I'm wrong. Try installing the "openoffice.org2-gnome" package. From it's description, it might provide GnomeVFS access in the same way that Suse had KIO access. I haven't actually tried it though.

---

### Post by thessem on 2006-01-28
OpenOffice.org-gnome does mention gnomeVFS in the description, but I already had it installed, so I re-installed and It didnt fix my problem.
Wats up with that?

---

### Post by thessem on 2006-01-28
It seems that the "openoffice.org-gtk-gnome" package in ver 1 does what I'm looking for, but the equiv in 2 doesnt?

---

