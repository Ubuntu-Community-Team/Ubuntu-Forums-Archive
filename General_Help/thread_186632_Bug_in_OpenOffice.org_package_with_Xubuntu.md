---
title: "Bug in OpenOffice.org package with Xubuntu?"
date: 2006-06-02
forum: General Help
---

### Post by e_liming on 2006-06-02
Hi,

I have the latest OpenOffice.org installed in Xubuntu but I find that the OpenOffice shortcuts in the Xfce menu is not opening the program correctly.

It opens a blank OpenOffice, not a writer, not a calc.. etc.

And I notice that the cause of this problem is in the *.desktop entries in /usr/share/applications. If I remove the "%U" argument in the program exec it all works correctly.

Possible bug?

---

### Post by norman_ on 2006-06-09
I replicated the problem here. Might be worth it to file a bug report?

---

### Post by TuxCrafter on 2006-07-18
I have the problem too and the solutions

first i dont now yet how to edit things in the menu of xfce.

Not al the links are in the menu editor. Links to openoffice are indicated in externel menu i dont now how to change them. Does someone know it?

Tho make a working link.

Step 1:
Right klik on the pannel and add a shortcut item
dont change anyting. Keep the dialog open

Step 2:
Open the appfinder tool and searce for openoffice writer app.
Select and drag it to the by step 1 opened shortcut dialog. You will notice a black box if you drag it to the right place.

Step 3:
Change the command ooffice to oowriter

Done

---

### Post by CombatGod on 2006-08-07
I've been having the same exact problem and I FINALLY figured it out.

1. go to /usr/share/applications in terminal
2. sudo nano ooo-writer.desktop
3. change oooffice -writer to oowriter
4. save and repeat for the other programs
In case you don't know what the commands are to open calc and stuff just do 

oo and press <tab>

---

### Post by shaulreznik on 2006-10-18
Another question: every time when I try to change default languages in Tools > Language Settings > Languages, I see that For the current document only checkbox is grey (e. g. disabled). How it's possible to enable it?

---

