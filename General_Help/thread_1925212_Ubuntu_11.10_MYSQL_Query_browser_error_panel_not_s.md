---
title: "Ubuntu 11.10 MYSQL Query browser error panel not showing"
date: 2012-02-14
forum: General Help
---

### Post by hamid.afshar on 2012-02-14
Hi people,

My mysql query browser error panel is not showing properly. It is really annoying me!

Please see attached screen shot where it says "error executing query". I can't toggle it open or anything like that.  :(

---

### Post by hamid.afshar on 2012-02-14
Okay I found a solution:

 echo export LIBOVERLAY_SCROLLBAR=0 | sudo tee /etc/X11/Xsession.d/80overlayscrollbars

you could do it specifically for mysql-query-browser by doing:

export LIBOVERLAY_SCROLLBAR=0; mysql-query-browser  ;) 

this will get rid of ubuntu's new scroll bar and fix the error panel in mysql query.

---

