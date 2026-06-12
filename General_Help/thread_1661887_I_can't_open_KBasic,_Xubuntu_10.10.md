---
title: "I can't open KBasic, Xubuntu 10.10"
date: 2011-01-07
forum: General Help
---

### Post by Superpelican12 on 2011-01-07
Hello,

Everybody. I've some problems with opening KBasic. I downloaded the .tar.gz file from the KBasic website. I extracted it. And now when I double click on "kbide" the program doesn't start. First ,when I was using Lubuntu, it just started. But not with my new Xubuntu 10.10.

Thanks for any help,

Superpelican

---

### Post by Wtower on 2011-01-07
I've got no idea about KBasic, but from their web site it seems like it depends on Qt v4 library. I believe it is not included by default in Xubuntu so you can try:

```
sudo apt-get install libqtcore4
```

I suppose you have to rebuild KBasic after that.

---

### Post by Superpelican12 on 2011-01-07
I checked in Synaptic but I saw a lot of QT 4 packages already installed. But I'm gone a try it!

Thanks for the help,

Superpelican :)

---

### Post by Superpelican12 on 2011-01-07
Hello,

The terminal says the Library is already installed. :confused:

Anyway thanks for your reaction,

Superpelican

---

### Post by Superpelican12 on 2011-01-22
I've it working after a while. I installed the whole Qt4 software, including Qt4 Designer.

Thank for all the help,

Superpelican :D

---

### Post by Wtower on 2011-01-22
Nice! Don't forget to mark the thread solved.

---

