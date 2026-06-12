---
title: "Remove File Type"
date: 2011-06-09
forum: General Help
---

### Post by Jdogzz on 2011-06-09
I was toying around with Wine and seeing if some programs I use on Windows were usable on Linux. I installed this program: [http://cycling74.com/products/maxmspjitter/](http://cycling74.com/products/maxmspjitter/) and it didn't work when I ran it. So I uninstalled it and thought it was all gone. Turns out that it caused all .txt files on my computer to be listed as "Max 5 Patcher" files, as shown in the attached picture. Can anyone help me get the text files to their normal type?

---

### Post by howefield on 2011-06-15
Try right clicking one of the files and select "Open With Other Application" and scroll down and choose Text Editor. Ensure the check box at the bottom is selected, Remember this application for....

---

### Post by Jdogzz on 2011-07-27
I had tried that before, and I did try it again at your suggestion, but it still didn't work. Is there something else I should try?

---

### Post by WorMzy on 2011-07-27
Open up ~/.local/share/applications/mimeapps.list, and edit it until your heart's content.

---

### Post by CatKiller on 2011-07-28
Right-click on a file. Select Properties. Select the Open With tab. Select Text Editor from the list. Optionally remove "Max 5 Patcher" from the list.

---

