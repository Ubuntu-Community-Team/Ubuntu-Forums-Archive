---
title: "Update Manager Ports"
date: 2010-02-26
forum: General Help
---

### Post by e24ohm on 2010-02-26
Folks:
I did a Wireshark capture, but I am unsure what I am looking for. Does the Update Manager use any specify ports? I want to run Firestarter, but only allow a few pots to be open.

Thanks.
J

---

### Post by dvlchd3 on 2010-02-26
Depends, if you kept the repositories to the default, they use http which is port 80.  Some repositories offer FTP or Rsycn protocols (21 & 873) but this is rather rare for people to actually use.  (I prefer Rsync, but maybe I'm an exception, and rsync isn't all that useful for getting updates...)

Great way to tell precisely, type this in a console
```

cat /etc/apt/sources.list | grep ^deb

```

If all the lines start with
**deb http://**
and
**deb-src http://**

Then its HTTP, thus port 80.  If its ftp:// or rsync:// instead of http, then update manager uses ftp or rsync respectively.

---

### Post by dvlchd3 on 2010-02-26
Sorry, just realised I gave you an answer as if you were a n00b, then saw your post count.  Guess you should know how to use the terminal, and what http, ftp, and rsync mean.  I apologise if I may have insulted your intelligence.

---

### Post by e24ohm on 2010-02-26
> **dvlchd3 said:**
> Sorry, just realised I gave you an answer as if you were a n00b, then saw your post count.  Guess you should know how to use the terminal, and what http, ftp, and rsync mean.  I apologise if I may have insulted your intelligence.Hey no problem, and no apology is needed....In tech...any points are good. 

I was blown away by my Wireshark results, and to be honest was lazy to check all the IP address out to find the one i was looking for.





thansk for the help...

IN Maryland my self...

thanks...

---

### Post by e24ohm on 2010-02-26
> **dvlchd3 said:**
> Depends, if you kept the repositories to the default, they use http which is port 80.  Some repositories offer FTP or Rsycn protocols (21 & 873) but this is rather rare for people to actually use.  (I prefer Rsync, but maybe I'm an exception, and rsync isn't all that useful for getting updates...)

Great way to tell precisely, type this in a console
```

cat /etc/apt/sources.list | grep ^deb

```

If all the lines start with
**deb http://**
and
**deb-src http://**

Then its HTTP, thus port 80.  If its ftp:// or rsync:// instead of http, then update manager uses ftp or rsync respectively.
Thank for the command...nice little trick...to now...thanks again mate...cheers!!!

---

