---
title: "Repository Update (Inkscape)"
date: 2009-11-28
forum: General Help
---

### Post by pepe_cz on 2009-11-28
[LEFT]Hello all,

I am just user of Ubuntu and I have curious question - I want to know how often and fast are ubuntu repositories updated? 
I use Inkscape - currently new version 0.47 is available - when is that version available for ubuntu users over deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main? There is still 0.47~pre4-0ubuntu1.
I see this with other packages as well....
Thanks!

Regards,
Peter
[/LEFT]

---

### Post by gslug79 on 2009-11-28
April?;) Package versions are not usually updated within an Ubuntu release - the updates you receive are only bug fixes or security updates. The only exception I can think of is that Hardy shipped with Firefox 3 beta, which was upgraded to the release version.

Unless you fancy compiling Inkscape or find a .deb somewhere, you will have to wait until the next Ubuntu release. Sorry!

---

### Post by pepe_cz on 2009-11-28
It means - in those repositories won't be any up-to-date software?

---

### Post by 3rdalbum on 2009-11-28
> **pepe_cz said:**
> It means - in those repositories won't be any up-to-date software?

Short answer: That's right.

Long answer:

If there are new MAJOR versions of the program released after Ubuntu's "feature freeze", then they won't make it into that version of Ubuntu. They might possibly be 'backported' to the Ubuntu Backports repository, or they might be available from the software developer's PPA, but they won't go into the main repository.

Minor versions that contain only bugfixes or security fixes: Might make it into Ubuntu's "updates" or "security" repositories, which are enabled by default.

If you're in a corporate situation, the last thing you want is to run updates across your entire network and find that it's changed your software versions. The next day you'd constantly be taking phone calls like "A button I use in this program has disappeared! It was there yesterday!". And that's just the least of it...

---

### Post by mbeach on 2009-11-28
> **3rdalbum said:**
> or they might be available from the software developer's PPA

That is likely the case with Inkscape. Once they have someone (remember these are volunteers) to keep the deb up to date you'll probably see some updates if you add their ppa to your software sources.

something like the following instructions might help.
[http://www.webupd8.org/2009/09/install-inkscape-047-pre3-in-ubuntu.html](http://www.webupd8.org/2009/09/install-inkscape-047-pre3-in-ubuntu.html)
or
[http://www.webupd8.org/2009/11/inkscape-047-final-version-released.html](http://www.webupd8.org/2009/11/inkscape-047-final-version-released.html)
But note that these are not Ubuntu repositories - they are maintained by third parties.

If you compile from source you are more than likely going to run into some dependency issues (that's my guess). But if you want the most recent version from last night or the night before, you are free to checkout the version from the svn repo and compile. Instructions are in the README available in the tarball download at:
[http://www.inkscape.org/download/](http://www.inkscape.org/download/)

If you go that route, I'd recommend you check out:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by pepe_cz on 2009-11-28
O.K. guys I got your point! Thanks very much for explaining it!

For time being I am running ubuntu for personal use only.

Please, can you point me where can I find "how to make deb packages for ubuntu."
Kind of user friendly approach? I mean - a really "user friendly" :-)

I want to make deb package of Inkscape 0.47.

Thanks!

Regards,
Pete

---

### Post by mbeach on 2009-11-28
there is one available here for karmic:
[http://www.webupd8.org/2009/11/inkscape-047-final-version-released.html](http://www.webupd8.org/2009/11/inkscape-047-final-version-released.html)

and for your request, this is the most thorough one I've read.
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

