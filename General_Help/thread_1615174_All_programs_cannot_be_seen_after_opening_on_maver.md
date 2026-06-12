---
title: "All programs cannot be seen after opening on maverick"
date: 2010-11-06
forum: General Help
---

### Post by markbeverley on 2010-11-06
Hi all,

I have a fairly major problem with my Maverick installation on my Laptop (Dell Latitude D630): when I go to open a program (as far as I can tell anything - program, settings window etc) the program loads (I can see it as a process from terminal with ps -aux) but it is no where to be seen on the desktop. One peculiarity is when I started OpenOffice Presentation I could see a fraction of the wizard in the corner of the screen. After moving it with alt+F7 and clicking 'create' the program appeared on another workspace...all other programs have not appeared on any workspace.

I should add that none of the programs appear on the panel - except for briefly flashing up when I start them and in the case of Firefox it appears on the panel but as soon as I click it it disappears.

So I guess this is a gnome/display issue.

Any help appreciated!

---

### Post by markbeverley on 2010-11-12
Just for the record, this seemed to be related to the file '%gconf.xml' in /home/user/gconf/apps. Although it didn't seem to contain anything, deleting it solved the problem - strange.

Mark

---

