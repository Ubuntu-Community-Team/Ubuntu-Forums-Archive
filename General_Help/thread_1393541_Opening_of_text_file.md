---
title: "Opening of text file"
date: 2010-01-29
forum: General Help
---

### Post by nomko on 2010-01-29
Hi,

Whenever i open a .txt file i get a pop-up menu with the following:

execute in terminal / view / cancel / execute

How can i change this into Gedit?
Many thanks!


(sorry for the Dutch picture, but I live in Holland a.k.a The Netherlands)

---

### Post by howefield on 2010-01-29
The file manager thinks it may be a program because the file has execute permissions set, so will ask you what to do.

Open Nautilus and navigate to Edit > Preferences > Behaviour Tab menu and set as required.

---

### Post by chaanakya_chiraag on 2010-01-29
A better (and more secure) thing to do is to right-click on the file, click "Properties", click on the "Permissions" tab, and uncheck "Execute".

---

### Post by audiomick on 2010-01-29
the view option will open it in gedit.

---

### Post by nomko on 2010-01-29
> **chaanakya_chiraag said:**
> A better (and more secure) thing to do is to right-click on the file, click "Properties", click on the "Permissions" tab, and uncheck "Execute".


This was the right solution!!
Many thanks!!

---

### Post by chaanakya_chiraag on 2010-01-29
No problem! :)

---

### Post by Morbius1 on 2010-01-29
Um ...... Am I missing something here?

For whatever reason the file has been marked as executable. You may not want it to be so by all means uncheck it. But you'll have to uncheck the next one as well.

To prevent the dialog box : Run in Terminal / Display /Cancel / Run:

Open Nautilus
Select Edit > Preferences > Behavior > "View executable text files when they are opened" It will then open in your default editor.

As opposed to the default "Ask each time"

It could be I misunderstood the question - happens to me a lot :)

---

