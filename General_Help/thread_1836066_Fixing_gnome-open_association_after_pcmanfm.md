---
title: "Fixing gnome-open association after pcmanfm"
date: 2011-08-30
forum: General Help
---

### Post by gsiliceo on 2011-08-30
I followed a tutorial to install pcmanfm instead of nautilus system wide, and i can't remember which one, i want to go back to nautilus and i got it to work with the places links and generally all the folder opening actions, but there still a problem when opening files for some programs for example the file-browser-applet for the gnome panel sends this error when trying to open a file for example:
> Could not display "/home/user/resume.pdf" the location is not a folder
And i tracked it down to trying to do
```
gnome-open "/home/user/resume.pdf"
```
or
```
xdg-open "/home/user/resume.pdf" 
```
I get the same error
I now it has something to do with file associations found in 
/usr/share/applications 
Because i found thats where gnome-open searches to know how to open a particular file extension suchs as pdf. This problems occurs with different programs for example gnome-do also use gnome-open to open files and sends the same error.
I must say that i can open files normally when browsing with nautilus, no problem with associations there, any help appreciated.

---

