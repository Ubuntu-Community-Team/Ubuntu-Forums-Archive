---
title: "How do I setup LaTeXila as my default tex editor?"
date: 2012-07-04
forum: General Help
---

### Post by Randy Schilling on 2012-07-04
Hello -

I would like to setup LateXila as the default editor to open when I click on a tex file.
As it is, I have to do menu-click to open a file under LateXila and LateXiLa is not listed
among the options when I try to set it up as default editor.  I try this from Properties
of any tex file.  
Thanks and many kind regard  - Randy

---

### Post by matt_symes on 2012-07-04
Hi

What *buntu are you using Randy  and what version of *buntu ?

I am not quite with you when you talk about the menu click, so please can you post a screen shot.

Kind regards

---

### Post by Randy Schilling on 2012-07-04
Hello - 

I've attached a screenshot (see next post below this one) showing some of the programs available to me as default programs for opening a tex file.  The problem is that LaTeXila, which is my favorite 
editor for texxing under Linux, is not on this list.  Neither is Kile.

I run the Unity desktop under Ubuntu 12.04.
RIght-hand people do a "left mouse click" to bring up a menu of options associated with whatever it is they clicked on.  I've reversed the settings on my mouse and I get confused, so I call it a "menu click".

Thanks so much and many kind regards - Randy

---

### Post by Randy Schilling on 2012-07-04
Here is the screenshot.

---

### Post by Vaphell on 2012-07-04
care to show the contents of /usr/share/applications/latexila.desktop (or whatever the file name is)?

afaik apps that lack the parameter placeholder for file name in Exec line refuse to be shown in lists of candidates for a default program.

---

### Post by Randy Schilling on 2012-07-04
Vaphell:
No such file under /usr/share/applications.
I don't understand the rest of your post.
Please try to keep in mind that I don't have your technical skills.
-Randy

---

### Post by Randy Schilling on 2012-07-04
There is a file named latexila in /usr/share/applications.
Under its properties you find that its type is
desktop configuration file (application/x-desktop)
but when you click on the file it opens the the latexila program.

---

### Post by Vaphell on 2012-07-04
it's a text file but system uses it as a launcher. Try in terminal:
```
cat /usr/share/applications/latexila.desktop
```

or run a text editor (gedit or whatever), 'open file' and browse to /usr/share/applications to open that .desktop file

---

### Post by Randy Schilling on 2012-07-04
Attached is the latexila.desktop.

Sorry about the delay.  I don't get it - the file does not show up in nautilus (even as a hidden file) but it shows up when you use Open from an editor and it shows up when you use ls -l. 

Hope this helps - Thanks so much - Randy

---

### Post by Vaphell on 2012-07-05
just as i thought Exec line doesn't have a placeholder for opened file

to compare with gedit:
```
Exec=gedit **%U**
```

in terminal
```
gksu gedit /usr/share/applications/latexila.desktop
```
type the password (gksu grants admin rights so you can make changes outside your $HOME), add %U in proper place, save and exit
try opening the default application dialog again and see if latexila is on the list.

---

### Post by Randy Schilling on 2012-07-05
Thanks thanks and thanks again - Randy

---

