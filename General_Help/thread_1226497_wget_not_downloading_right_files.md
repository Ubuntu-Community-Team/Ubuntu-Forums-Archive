---
title: "wget not downloading right files"
date: 2009-07-29
forum: General Help
---

### Post by kronicle on 2009-07-29
how do i get wget to download files fof me?
when i run 
sudo wget [http://www.cakephp.org/download/cake_1.2.3.8166.tar.gz](http://www.cakephp.org/download/cake_1.2.3.8166.tar.gz)

it downloads the file alright and i can see it with "ls"
but when i check the file with file command what it downloads
is an html file and i cant even untar it.
what am i doing wrong?

---

### Post by j.bell730 on 2009-07-29
You're not doing anything wrong. The file does not exist on the server, click the link and see for yourself.

---

### Post by credobyte on 2009-07-29
I can't get even a html file :-k

```
dainis@ubuntu:~/Desktop$ wget http://www.cakephp.org/download/cake_1.2.3.8166.tar.gz
--2009-07-29 23:58:49--  http://www.cakephp.org/download/cake_1.2.3.8166.tar.gz
Resolving www.cakephp.org... 209.62.120.20
Connecting to www.cakephp.org|209.62.120.20|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://cakephp.org/download/cake_1.2.3.8166.tar.gz [following]
--2009-07-29 23:58:49--  http://cakephp.org/download/cake_1.2.3.8166.tar.gz
Resolving cakephp.org... 209.62.120.20
Reusing existing connection to www.cakephp.org:80.
HTTP request sent, awaiting response... 404 Not Found
[COLOR=Red]2009-07-29 23:58:50 ERROR 404: Not Found.[/COLOR]

```

---

### Post by kronicle on 2009-07-29
ok, thank you, so how do i download the file named hotcakes located here?

[http://cakeforge.org/projects/hotcakes/](http://cakeforge.org/projects/hotcakes/)

---

### Post by credobyte on 2009-07-29
This one seems to be available:
```
wget http://cakeforge.org/frs/download.php/596/cake_1.1.18.5850.tar.gz

```

---

### Post by kronicle on 2009-07-29
thanks once again.
[LEFT]why did you add the following

/frs/download.php/596

into the url, an must i add it anytime i want to download, even from other sites?


[/LEFT]

---

### Post by credobyte on 2009-07-29
> **kronicle said:**
> thanks once again.
[LEFT]why did you add the following

/frs/download.php/596

into the url, an must i add it anytime i want to download, even from other sites?


[/LEFT]


I didn't added anything - just went to their website & copied download link :p

---

### Post by kronicle on 2009-07-29
oh ok, thanks very much for the help.
would have been lost without ur help.:D

---

