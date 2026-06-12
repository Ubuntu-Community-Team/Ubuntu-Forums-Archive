---
title: "&quot;dd | 7z/gzip/bzip&quot; and &quot;7z/gzip/bzip | dd&quot;"
date: 2012-06-01
forum: General Help
---

### Post by Browser_ice on 2012-06-01
In case you have not guessed it, I am looking at a one line command to do :

1) DD or DCFLDD the whold drive into an ISO file
2) compress that output ISO file


Isn't there a way to do it all in one line like :
dd if=xxxxx bs=999 | 7z ....  drive.iso.7z

and then to restore :

7z ... drive.iso.7z | dd bs=999 of=/dev/sda

In the example I use 7z because I like it. I would prefer using it over gzip, bzip, ...

---

### Post by Browser_ice on 2012-07-05
Is my question too complicated or that no one knows how to do this ?

---

### Post by Redblade20XX on 2012-07-05
You should post this in the programming section thats where all the bash programmers are. I would love to help you but my bash skills are kind of rusty.

:p

- Red

---

