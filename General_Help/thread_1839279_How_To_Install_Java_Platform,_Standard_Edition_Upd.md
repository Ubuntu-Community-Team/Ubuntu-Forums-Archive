---
title: "How To Install Java Platform, Standard Edition Update 7 On 11.04"
date: 2011-09-05
forum: General Help
---

### Post by TheMidnightWings on 2011-09-05
Okay. if anyone can help me out on this, it'd be really helpful. This is mainly for testing purposes but I'm a moron when it comes to using certain files :lolflag:. This is a perfect example. 

**_[http://jdk7.java.net/download.html](http://jdk7.java.net/download.html)_**

I have **[FONT="Impact"]NO clue how to use the tar.gz extension[/FONT]** :confused:, how to install it or unpack it. Whatever you must do, if you guys could gimme a hand it'd be really appreciated since I can't seem to find any tuts on how to do this elsewhere. Thank you guys! :smile:

---

### Post by TheMidnightWings on 2011-09-05
Bump :KS

---

### Post by gmargo on 2011-09-05
The "gz" part indicates a particular type of compression (specifically "[gzip]("http://en.wikipedia.org/wiki/Gzip")" compression).
The "tar" part indicates that the files are grouped in the [tar]("http://en.wikipedia.org/wiki/Tar_%28file_format%29") format.  If you're familiar with .zip files, the concept is similar, except that tar does not compress files like zip does.

To get the table of contents of abc.tar.gz:
```

tar tzfv abc.tar.gz
-or-
gzip -dc abc.tar.gz | tar tfv -

```To extract the files, once you've decided what directory they go in:
```

tar xzfv abc.tar.gz
-or-
gzip -dc abc.tar.gz | tar xfv -

```I don't know about the rest of the installation - you'll probably have to extract the files to find a README or other installation instructions.  Since there don't seem to be any useful instructions on the web site.

---

