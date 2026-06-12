---
title: "Cannot apply emblems to folders"
date: 2009-11-20
forum: General Help
---

### Post by kennedyjch on 2009-11-20
Installed a fresh (save for /home folder) of ubuntu 9.10. But now I cannot apply emblems to folders. I click and the check mark appears adjacent to the selected emblem, but when I "close", nothing happens.

Also noticed that I cannot change folder icons using /usr/share/pixmaps - whatever icon I specify, it remains the same.

Any clues?

---

### Post by kennedyjch on 2009-11-22
Update: One of the other userid's on the system can change their icons and emblems - so it appears to NOT be a software problem per se... rather one of configuration...

However, on my ID I still can't. I checked and I'm the owner of the /home/john directory as well as all the files within. 

Puzzled

---

### Post by kennedyjch on 2009-11-28
Bump?

---

### Post by jimfuture12345 on 2009-11-28
HI , I HAVE ABIT SAME PROBLEM WILL YOU BE IN TOUCH WITH ME UNTILL FIND WHY .
 
I WANT TO MODIFY .CONF FOLDER FROM MY NORMAL USER , (WHICH CAN'T BE ) AND FROM SUDO CCOMMAND HE ASK FOR CODE PASSWORD 
 
ANY IDEA 
 
:-k:-k:-k:-k:-k:-k:-k

---

### Post by kennedyjch on 2010-03-07
Update: I can apply emblems on other user account on my workstation. I can also add them to external hard disk files.

Still cannot add emblems to files in my /home/myname home folder. What configuration settings / permissions could I have messed up???

TIA

---

### Post by kennedyjch on 2011-04-25
Problem of not being able to change emblem associations with files on my userID solved by logging out from Gnome graphic interface, pressing Ctrl+Alt+F1 and logging into your account and entering the following:
> rm ~/.local/share/gvfs-metadata/*

Logout and re-login through the graphic interface Ctrl+Alt+F7 or F8 or F9...

Thanks to Krytarik for this solution.

---

