---
title: "Problem installing BrettspielWelt.tar.gz"
date: 2011-08-09
forum: General Help
---

### Post by Anonymus666 on 2011-08-09
Hi Guys im having trouble installing this package from
[http://www.brettspielwelt.de/Hilfe/Client/Linux/](http://www.brettspielwelt.de/Hilfe/Client/Linux/)
I've done the unpack without any problems. But when i try to run the Application link ive made here's what happens


Here's the info im entering into the Laucher

[LIST]
[*]Type: Application
[*]Name: BSW
[*]Command: /home/anonymus/BrettspielWelt/start.sh
[*]Comment: none
[/LIST]

My BSW is unpack in my home/anonymus

What i did wrong ? 
Some can help me out ? 

Thanks for Helping ! :)

---

### Post by jerrrys on 2011-08-09
sounds like you need to change start.sh owner from root to user in  properties>permissions.

EDIT: go to advance when posting a pic and click on the paperclip

---

### Post by Anonymus666 on 2011-08-09
> **jerrrys said:**
> sounds like you need to change start.sh owner from root to user in  properties>permissions.

EDIT: go to advance when posting a pic and click on the paperclip

Ok here's a pic of my permissions setttings is there any thing wrong ?

I can't change root from user :S Why so ?

Btw Java6 is installed.

---

### Post by jerrrys on 2011-08-09
to change permissions, open a terminal and enter **gksudo nautilus**

---

### Post by Anonymus666 on 2011-08-09
> **jerrrys said:**
> to change permissions, open a terminal and enter **gksudo nautilus**

Ive done it ... This poped me a window with Root folder i did copy my BrettspielWelt folder and contents and changed the root to user and it doesn't work :S

---

### Post by jerrrys on 2011-08-09
double click on start.sh

do anything?

---

### Post by Anonymus666 on 2011-08-13
> **jerrrys said:**
> double click on start.sh

do anything?

Worked now :) I just changed to folder to another location and edit permission ! :) Worked like a charm ! :D

---

### Post by jerrrys on 2011-08-13
happy brettspielWelting

---

