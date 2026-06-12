---
title: "How to see how much of my hard disk is full?"
date: 2010-09-02
forum: General Help
---

### Post by Pondoro on 2010-09-02
I can't seem to fin the command that tells how much space is used/free.

---

### Post by llamabr on 2010-09-02
How about 

```
df -h
```

---

### Post by Pondoro on 2010-09-02
Thanks!

---

### Post by jerome1232 on 2010-09-02
Edited most of it out, just realized your on a different Desktop Environment than gnome

Yet another commandline tool (that I love) is du

---

### Post by llawwehttam on 2010-09-02
> **jerome1232 said:**
> Edited most of it out, just realized your on a different Desktop Environment than gnome

Yet another commandline tool (that I love) is du

```
du -hs 
```shows the total amount of files IIRC

---

### Post by mrinvader on 2010-09-02
in the main menu, under applications-accessories is a program called Disk Usage Analyzer.. this will give both free/used figures AND an analysis of each directory's usage. Very cool!

[http://www.marzocca.net/linux/baobab/]("http://www.marzocca.net/linux/baobab/")

[IMG]http://risto.kurppa.fi/blog/wp-content/uploads/2008/10/disk_analyzer.png[/IMG]

more such tools including du and df...

[http://risto.kurppa.fi/blog/2008/10/disk-space-analyzers/](http://risto.kurppa.fi/blog/2008/10/disk-space-analyzers/)

---

