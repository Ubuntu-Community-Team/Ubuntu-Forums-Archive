---
title: "Bibus Repository error"
date: 2009-10-11
forum: General Help
---

### Post by frogotronic on 2009-10-11
Hello,

   Need some help from the Ubuntu community regarding a project hosted at Sourceforge.  It's a free referencing software program called Bibus ( [http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page](http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page) )- an alternative to Endnote ( [http://www.endnote.com/](http://www.endnote.com/) ) or Refworks ( [http://www.refworks.com/](http://www.refworks.com/) ).

  Recently the repositories have been generating an error during updates ( see this forum post : [https://sourceforge.net/projects/bibus-biblio/forums/forum/380178/topic/3370164](https://sourceforge.net/projects/bibus-biblio/forums/forum/380178/topic/3370164) )

  Does anyone have a solution?  You could post to this thread, or to the original Bibus Forum thread at Sourceforge.

Many thanks in advance.

- CH

---

### Post by frogotronic on 2009-10-12
Here's the error:

W: Failed to fetch [http://superb-east.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz](http://superb-east.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz)  302 Found

W: Failed to fetch [http://superb-east.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz](http://superb-east.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by MelDJ on 2009-10-12
maybe this explains it: [http://www.checkupdown.com/status/E302.html](http://www.checkupdown.com/status/E302.html)

---

### Post by frogotronic on 2009-10-12
> **MelDJ said:**
> maybe this explains it: [http://www.checkupdown.com/status/E302.html](http://www.checkupdown.com/status/E302.html)

Hmmm.  Yes, its a redirect, but happens with every sourceforge mirror.

Don't know how to solve it.

- CH

---

### Post by MelDJ on 2009-10-12
as said there: 
If the Web server does not return an alternative URL with the 				  302 response, then either the Web server sofware itself is defective or your 				  Webmaster has not set up the URL redirection correctly.

---

### Post by frogotronic on 2009-10-12
I filed a ticket with Sourceforge.

- CH

---

### Post by MelDJ on 2009-10-12
may i ask, whats a ticket in sourceforge?

---

### Post by frogotronic on 2009-10-12
> **MelDJ said:**
> may i ask, whats a ticket in sourceforge?

A bug report to the webmaster

[http://sourceforge.net/apps/trac/sourceforge/ticket/5587#comment:1](http://sourceforge.net/apps/trac/sourceforge/ticket/5587#comment:1)

---

