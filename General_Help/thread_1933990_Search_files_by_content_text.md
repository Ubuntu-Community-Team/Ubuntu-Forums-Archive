---
title: "Search files by content text"
date: 2012-03-01
forum: General Help
---

### Post by cmani on 2012-03-01
Hi,

How to search files which containing some specified text in gui.

similar to grep -l -R "text" *

In gnome/nautils "Search files" has that option.  In unity how to do,

Pl. advice.

Thanks.

---

### Post by cortman on 2012-03-01
> **cmani said:**
> Hi,

How to search files which containing some specified text in gui.

similar to grep -l -R "text" *

In gnome/nautils "Search files" has that option.  In unity how to do,

Pl. advice.

Thanks.

Unity uses nautlius too. If grepesque searches are still available in recent versions of nautilus, you can use it in Unity as well.
Otherwise I just always use the command line...

---

### Post by philinux on 2012-03-01
> **cmani said:**
> Hi,

How to search files which containing some specified text in gui.

similar to grep -l -R "text" *

In gnome/nautils "Search files" has that option.  In unity how to do,

Pl. advice.

Thanks.

Click on home folder then Global menu Go>search for files.

---

### Post by cmani on 2012-03-05
> **philinux said:**
> Click on home folder then Global menu Go>search for files.


Still can't search by content text.  It can able to search only by Location / File Type.

[http://library.gnome.org/users/user-guide/stable/nautilus-searching.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-searching.html.en)

The containing text search feature available many of us need that now and then, its removal is really doesn't make anything good.

---

### Post by dragonfly41 on 2012-03-05
Solutions depend on the scope of content searching ..

[https://help.ubuntu.com/community/FindingFiles](https://help.ubuntu.com/community/FindingFiles)

Start with these ..

Places > search for files > select more options > contains the text

Applications > Accessories > search for files > select more options > contains the text

If these aren't good enough there are a few advanced tools available for content search.

Install** recoll **via Synaptics Package Manager

[http://www.lesbonscomptes.com/recoll/usermanual/rcl.install.html](http://www.lesbonscomptes.com/recoll/usermanual/rcl.install.html)


[http://brainstorm.ubuntu.com/idea/17165](http://brainstorm.ubuntu.com/idea/17165)

If more sophisticated searching of content is required ..

**TextSTAT**
[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

You need to install python-tk. 
Then, run the command "python TextSTAT.pyw" in the TEXTStat folder.

also try ..
[B][COLOR=black]
AntConc3.2 and AntWord Profiler[/COLOR][/B]
[http://www.antlab.sci.waseda.ac.jp/software.html](http://www.antlab.sci.waseda.ac.jp/software.html)

but these latter tools are very advanced .. offering concordance searching, word frequency analysis etc.

e.g. scanning through a large corpus of documents.

---

### Post by cmani on 2012-03-11
Thanks dragonfly.  It works

---

