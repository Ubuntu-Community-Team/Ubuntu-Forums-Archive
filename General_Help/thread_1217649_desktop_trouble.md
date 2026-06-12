---
title: "desktop trouble"
date: 2009-07-19
forum: General Help
---

### Post by dmaxx on 2009-07-19
After i have downloadet a tar.bz2 file, i accidently open it in desktop (btw the file is a bit big and all files get uzippet on the desktop so the desktop get overflow with files -_-) and after that evrytime i have open file browser i can go 2 other folders and files as usal but everytime i try 2 go to the desktop folder, the file browser is exit itself,and no folders,driver or files is showing on desktop,thinking the files that have been uzippet there may cause the problem i try 2 access the desktop using other way but with no luck,but i have taken notice that when i try 2 use the search engine on the desktop(thinking i could search the files up and then delete they from the search engine)something that was going fine until i start searching for the j2c files and then the same thing happen 2 the search engine that i happen 2 file browser,it exit itself and its happen everytime i try,,,so the question is how do i get stuff back 2 how it was before it happen....

PS:I may have say 2 much nonsense and write more that i sould -_- so if something is unclear and wanna more info about something please ask....

PSS:And yeah i know it may be some spelling that is wrong so no need 2 say that....

PSSS:i din't know for sure where 2 post this thread so i postet it here,sorry if it's wrong place...

---

### Post by earthpigg on 2009-07-19
show us the output of this command, please:

> ls -a ~/Desktop/


and in the future please break up your post into a few paragraphs to make it easier to read.

---

### Post by dmaxx on 2009-07-19
> **earthpigg said:**
> show us the output of this command, please:




and in the future please break up your post into a few paragraphs to make it easier to read.



i only get > ls: cannot access ~/Desktop/: No such file or directory 

im sure i have done someting wrong, xD i always do..........

btw i can't right click on desktop either just so u know...

and sorry for the tight writing but i is use 2 most write so much i can on few pages as posib so i wasn't thinking so much about it,but will try better next time -_-

---

### Post by earthpigg on 2009-07-19
looks like you deleted your desktop folder on accident. whoops!

> mkdir ~/Desktop

see if that clears things up.

edit: that's _***D***_esktop, not ***_d_***esktop.

---

### Post by dmaxx on 2009-07-19
> **earthpigg said:**
> looks like you deleted your desktop folder on accident. whoops!



see if that clears things up.

edit: that's _***D***_esktop, not ***_d_***esktop.
only get > mkdir: cannot create directory `~/Desktop': No such file or directory

and just so u know,i can see the Desktop folder in file browser but if i try 2 access it in the file browser it just exit itself and the files that is in Desktop folder i show when i go there using other software and using open file,so the files is there i just can't access it

---

### Post by earthpigg on 2009-07-19
try this, just for kicks:

> sudo ls -a ~/Desktop/ 

---

### Post by dmaxx on 2009-07-19
That have i already try and other combination 2 xD i have had linux long enough 2 know a thing or 2 about it,but this is just weird,have it been windows i could always fix it,but then again linux and windows is 2 totally diff planets xD

---

### Post by dmaxx on 2009-07-20
BTW is j2c files know 2 make any trouble in the 9.04 ver of ubuntu(jaunty)?? and if so how do i fix it??because since i don't get access 2 the desktop i can't just open and delete the files from the syst..

---

### Post by earthpigg on 2009-07-20
this is beyond my experience/knowledge, sorry :\

people often ignore threads that have a bunch of replies on the assumption that the solution has already been found... i suggest making a new thread and putting 'expert' or 'guru' or some word like that so the super-smart volunteers will feel challenged and rush to your aid. :D

good luck.

---

### Post by dmaxx on 2009-07-20
thx will try (later)

---

