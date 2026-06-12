---
title: "Screenshot Gnome-shell how to"
date: 2011-12-01
forum: General Help
---

### Post by joplass on 2011-12-01
How do you take a screenshot in gnome-shell while in preview mode?  I tried PrtScrn on the keyboard.  I get "Gnome Screenshot failed: Command not found.
Cheers

---

### Post by Bobhuber on 2011-12-01
> **joplass said:**
> How do you take a screenshot in gnome-shell while in preview mode?  I tried PrtScrn on the keyboard.  I get "Gnome Screenshot failed: Command not found.
Cheers
Yes it's a known bug in gnome3. Install a program called scrot from the package manager. Works great.

---

### Post by joplass on 2011-12-01
> **Bobhuber said:**
> Yes it's a known bug in gnome3. Install a program called scrot from the package manager. Works great.

I have been using scrot and I am very familiar with the program. I wonder if there is another way of running scrot.  
I did Alt+F2 to launch the command popl up while in preview mode. Typing "scrot -d 5" gave me command not recognized.  How do you use scrot in preview mode?
Thanks

---

### Post by Bobhuber on 2011-12-01
> **joplass said:**
> I have been using scrot and I am very familiar with the program. I wonder if there is another way of running scrot.  
I did Alt+F2 to launch the command popl up while in preview mode. Typing "scrot -d 5" gave me command not recognized.  How do you use scrot in preview mode?
Thanks
 Remove the space in your command and tell it what kind of file you want to create..
I wrote a simple bash file that I run from Cairo dock. You could run it ALT+F2 also.
screenshot.sh
```
#!/bin/bash
scrot -d5 temp.png
convert temp.png -resize '50%' desktop.jpg
rm temp.png
eog desktop.jpg
```Change the delay to suit your needs and it will give you plenty of time to do whatever with the desktop. This takes the shot,resizes it and displays it for preview. Save the file in /usr/local/bin and mark it executable.To run it just type screenshot.sh from a terminal or ALT+F2.
Please note you will need ImageMagick installed for the convert command to work.

---

### Post by joplass on 2011-12-02
> **Bobhuber said:**
> Remove the space in your command and tell it what kind of file you want to create..
I wrote a simple bash file that I run from Cairo dock. You could run it ALT+F2 also.
screenshot.sh
```
#!/bin/bash
scrot -d5 temp.png
convert temp.png -resize '50%' desktop.jpg
rm temp.png
eog desktop.jpg
```Change the delay to suit your needs and it will give you plenty of time to do whatever with the desktop. This takes the shot,resizes it and displays it for preview. Save the file in /usr/local/bin and mark it executable.To run it just type screenshot.sh from a terminal or ALT+F2.
Please note you will need ImageMagick installed for the convert command to work.

That did the trick.
Thanks

---

### Post by digithal on 2011-12-02
```
sudo apt-get install gnome-screenshot
```
:)

---

