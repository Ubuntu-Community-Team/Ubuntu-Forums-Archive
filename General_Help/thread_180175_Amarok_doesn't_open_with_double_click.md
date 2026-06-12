---
title: "Amarok doesn't open with double click"
date: 2006-05-21
forum: General Help
---

### Post by GG. on 2006-05-21
Hello,
yesterday I've installed and completed a minimal configuration on Kubuntu. Now I'd like to listen to my mp3 while I'm working, so I've follow all the instructions in the superlative wiki. ;) 
The problem I notice is that amaroK doesn't open a file when I double-click on it, but the same file is opened correctly, and I can listen to it, using the perspective "Files" in the playlist of amaroK. ](*,) 

Any hints?
Thanks,
GG

---

### Post by insulae on 2006-05-24
try to run amarok from the konsole, with this you meaby can see the error, if you dont understand, copy the error here.

---

### Post by pwaldo on 2006-05-24
Another option for seeing errors from applications is to  look at the file
~/.xsession-errors

---

### Post by an.echte.trilingue on 2006-05-24
You set the file associations to play mp3 with amarok, right?  (konqueror--> settings:/Components/--> File Associations)

---

### Post by GG. on 2006-05-25
Hello,
no errors from the console, and the file association is right.
The problem seems to be that Konqueror sends to amaroK a path with system:/... and amaroK cannot open it. 

This is strange, because when I try to open from Konqueror a file in my home, this "bug" arises, but I' ve also tried to open files from a cd/dvd and amaroK plays them perfectly....:???: :???:

---

