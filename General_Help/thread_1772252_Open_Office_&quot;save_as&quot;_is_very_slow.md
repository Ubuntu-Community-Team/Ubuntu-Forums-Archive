---
title: "Open Office: &quot;save as&quot; is very slow"
date: 2011-05-31
forum: General Help
---

### Post by Mariane on 2011-05-31
The saving process itself is normal, but when I save something for the first time it often takes ages to open the "save as" window. Then I click on a directory and I have 2 little white spots circling one another, OO's way of saying "wait". After a while the contents of directory I chose is displayed. Going to the next (sub) directory again takes a long time. 

Only OO is doing this, when I save from other programs going to the directory where I want to save the stuff takes no time at all. The subdirectories are displayed immediately after I click on the parent directory. 

Mariane

---

### Post by Mariane on 2011-06-02
bump.

---

### Post by V-Star on 2011-06-02
I am running Natty and Save As is very slow with everything? Any ideas? Anyone!

---

### Post by MARP1961 on 2011-06-02
Are you still using Open Office? Natty now installs LibreOffice3 by default. LibreOffice is a fork from Open Office and is likely to run better on regularly updated versions of Ubuntu. Install the latest LibreOffice version and see if everything speeds up.

---

### Post by linuxinstalledfromhdd on 2011-06-02
I would suggest LibreOffice on 10.10..  I'm very happy with performace so far. 

Here's a guide to get that setup:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by quickk on 2011-06-02
I had the same problem.   For some reason, it looks like when openoffice tries to use the kde file manager to save, open, etc., things are extremely slow.   

What you have to do is this:

- In the options, go to the "General" section under the LibreOffice/Openoffice section.  

- Then select "Use LibreOffice/OpenOffice dialogs" (on the right panel). 

This should solve the slowness.    I hope this helps!

---

### Post by Mariane on 2011-06-03
Great! This made saving much faster! Thank you very much.

Note for others: 
At first I didn't see this option because I was looking in 
Tools/Options/Load-Save/General
It is not there, in my version it is in 
Tools/Options/OpenOffice.org/General

Mariane

---

