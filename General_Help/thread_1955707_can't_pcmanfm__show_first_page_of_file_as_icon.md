---
title: "can't pcmanfm  show first page of file as icon ?"
date: 2012-04-10
forum: General Help
---

### Post by bilol on 2012-04-10
hi,
In gnome, when I open the file manager, icons of pdf,doc or text files shows first page of those documents. This is very helpful. However, in lxde when I open the file manager pcmanfm the icons of those file arises , showing default image for all pdf text or doc files. 
How can I see the first page of the document, as in gnome nautilus , in pcmanfm ?
Any help will be appreciated.....

---

### Post by ridetheteapot on 2012-04-10
hey pcmanfm doesn't support this by default (last time I tried at least).
there is a patch that works though :
[http://sourceforge.net/tracker/?func=detail&aid=3424000&group_id=156956&atid=801866](http://sourceforge.net/tracker/?func=detail&aid=3424000&group_id=156956&atid=801866) (uses poppler for pdf thumbs)

dunno if someone has a build with that patch on a ppa, but you may want to check it out. otherwise you'll need to recompile with that patch.

---

### Post by bilol on 2012-04-11
thanks ridetheteapot ...
still I can't enable thumbnails in pcmanfm. 
[This page]("http://wiki.lxde.org/en/PCManFM_Roadmap#Thumbnail") states **"Apparently, current thumbnail support has some serious bugs and it suffers from racing condition."**

---

### Post by bilol on 2012-04-11
I found the same problem [here]("http://ubuntuforums.org/showthread.php?t=1877100") .
But....recommended "tumbler" and its plug-in did not work.

---

### Post by ridetheteapot on 2012-04-11
i dunno soz bibol
[IMG]http://ubuntuforums.org/picture.php?albumid=921&pictureid=8387[/IMG]

can you see it? its a bad pdf for example -- just only on there at the time --- but point being that patch is working for me :-\

pcmanfm ver 0.9.10 w that patch

---

