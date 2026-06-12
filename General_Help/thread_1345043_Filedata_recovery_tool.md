---
title: "File/data recovery tool"
date: 2009-12-03
forum: General Help
---

### Post by nomko on 2009-12-03
Hi there,

I'm curious, is there a file/data recovery tool for Ubuntu Linux available? I'm looking for a free tool which can repair lost data/files or erased data/files from any kind of drives i.e. flash cards, usb sticks, external drives, etc. Does anyone know a very good program who can fix the job properly? Many thanks! Nomko

---

### Post by HunterThomson on 2009-12-03
I like to use tar

You can make a backup of your whole /root parition by doing this

```
sudo tar pczvf root.tar.gz /*
```

Then to restore to a empty partiton you can do.

```
sudo tar pxvf root.tar.gz
```

The    p    flag is the important one. That "preserves" all the Meta-data like ownership and stuff. the    z   flag compresses it to a gzip tar.gz. With out the   z   it will not compress it.


There are a lot of other option. Like only extracting certen files from the   tar   arcive and everything you could need.

Check out the man page

```
man tar
```

I have used Loads of other application and I have been unable to use my backups may time. But with   tar  you will NEVER have a problem.

---

### Post by nomko on 2009-12-03
> **HunterThomson said:**
> I like to use tar

You can make a backup of your whole /root parition by doing this

```
sudo tar pczvf root.tar.gz /*
```Then to restore to a empty partiton you can do.

```
sudo tar pxvf root.tar.gz
```The    p    flag is the important one. That "preserves" all the Meta-data like ownership and stuff. the    z   flag compresses it to a gzip tar.gz. With out the   z   it will not compress it.


There are a lot of other option. Like only extracting certen files from the   tar   arcive and everything you could need.

Check out the man page

```
man tar
```I have used Loads of other application and I have been unable to use my backups may time. But with   tar  you will NEVER have a problem.

Thanks for your response, but this is not what i'm looking for. I'm asking for a tool which can restore/recover data/files from any kind of drives and you give me a command for making backups.

---

### Post by SeattleOtaku on 2009-12-03
A few places to start may be (wiki'd as open alternatives to the commercial "SpinRite"):

ddrescue (GNU): [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

dd_rescue: [http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)
dd_rhelp: [http://www.kalysto.org/utilities/dd_rhelp/index.en.html](http://www.kalysto.org/utilities/dd_rhelp/index.en.html)
(script+app possibly superceded by ddrescue now, but still maintained "in case")

ext3grep: [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/%7Ecarlo17/howto/undelete_ext3.html")
source at the end hosted on google groups: [http://groups.google.com/group/ext3grep/web/ext3grep-source-code-and-overview](http://groups.google.com/group/ext3grep/web/ext3grep-source-code-and-overview)
(theory and app for an ext3 undelete)

---

