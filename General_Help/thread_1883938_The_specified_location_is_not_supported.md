---
title: "The specified location is not supported"
date: 2011-11-20
forum: General Help
---

### Post by linuxcss on 2011-11-20
xubuntu 11.10

When dragging a link location (such as a pdf link, and mp3 link) from a webpage to the desktop
 I now am getting this warning: The specified location is not supported 
and no file is transferred.

How can this be fixed?

---

### Post by Paddy Landau on 2011-11-20
Are you trying to make a shortcut to the link on your desktop?

I have found that making shortcuts like that on the desktop does not work. Rather bookmark it in the web browser.

---

### Post by linuxcss on 2011-11-22
Drag and drop link onto desktop to download the file, worked in the past on other ubuntu's and also on other machines running xubuntu 11.10.

---

### Post by beesthorpe on 2011-11-22
have you perhaps got the desktop icons disabled in settings manager >desktop > Icons?

---

### Post by Paddy Landau on 2011-11-22
> **linuxcss said:**
> Drag and drop link onto desktop to download the file, worked in the past on other ubuntu's and also on other machines running xubuntu 11.10.
Sorry, I misunderstood you.

I don't know; I am running Ubuntu, not Xubuntu.

If it used to work, have you considered raising a bug?

EDIT: beesthorpe beat me to it.

---

### Post by linuxcss on 2011-12-01
i found out how to fix this issue but another problem or bug gets exposed

if I install gvfs-backends I can then drag and drop, however whenever the machine is
rebooted the first opening of a folder (via default file manager thunar ver 1.2.3) I get a delay of 30 to 60 seconds that says "the folder could not be opened" ... which has something to do with automounting and network.mount .... changing autoMount=false within the file network.mount does NOT fix that problem

---

### Post by linuxcss on 2011-12-01
is there any other way to get the drag and drop functionality that gvfs-backends supports without installing gvfs-backends in xubuntu 11.10 ??

example:
a webpage has a link to an mp3 or a pdf file and I drag either of the links onto the desktop and it downloads the file to the desktop (or I drag and drop to some other folder, and it downloads to the given folder).

---

