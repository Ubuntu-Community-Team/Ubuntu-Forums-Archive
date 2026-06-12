---
title: "Opening .r00 formats"
date: 2009-07-27
forum: General Help
---

### Post by Toliot on 2009-07-27
Hey,
I was wondering if it is possible to extract .r00 formats with ubuntu,
and what programs i need and what to do :P

thanks in advance (running ubuntu jaunty if that matters)

---

### Post by jocko on 2009-07-27
First you probably need to install the package unrar:
```
sudo apt-get install unrar
```
Then, just right click the file and choose "extract here" or "open with archive manager".

---

### Post by dicairo on 2009-07-27
u can use also hjsplit written in java : 
just open a terminal and this : 
**wget [http://www.freebyte.com/download/hjsplit/hjsplit_g.jar](http://www.freebyte.com/download/hjsplit/hjsplit_g.jar)** (to download hjsplit in the home folder)
**java -jar hjsplit_g.jar **(to run the program ).
have funnnnnnnn :popcorn:

---

### Post by michy99 on 2009-07-27
.r00 is a multiple volume rar archive. HJsplit is something different. And by the way, all you need to join files split with HJsplit is the built-in cat command.

---

### Post by Toliot on 2009-07-27
Thanks a lot guys :)
(i had unrar installed bfor but then i reformated so i forgot about it hehe)

idk if im alowd to do this but i have another question relating another topic, i am trying to boot win7 and ubuntu i had ubuntu previously then i installed win7 then i decided to delete ubuntu and reinstall (too many packages and i didnt know how to delete...for some reason i couldnt install anything anymore) so now i can load grub and when i choose <windows 7 (loader)> i get an error "Bootmgr missing" ctrl-alt-dlt to restart... idk what to do  :P any help is appreciated once again thanks for the previous answers :)

---

