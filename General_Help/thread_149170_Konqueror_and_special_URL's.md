---
title: "Konqueror and special URL's"
date: 2006-03-23
forum: General Help
---

### Post by dartmusic on 2006-03-23
Or whatever they're called (heh...)!  

How can I get Konqueror to NOT use the "media:/" style urls?  This continually causes problems and I have to manually redirect to "/media/whatever_drive_I'm_looking for."

Not the end of the world, just inconvenient.

Speaking of these/this/etc.: I don't really mind using the "ipod:/" one, but I can't really do anything with it.  Whenever I make a change and then go to Utilities and try to save (or whatever it's called...again, I'm at work and at an XP box...sigh) I just get an error saying that it failed.  I had this same problem in SuSE.  Any ideas?

Thanks in advance.

---

### Post by ltmon on 2006-03-23
It's a pain for some.  I'm sure it can be configured to work as advertised, but I haven't seen it work flawlessly yet.

The Dapper release has been patched from the normal KDE release to use "/home/[username]" rather than "system:/home" or anything like that, so it's an improvement.

As for ipods, I wouldn't use ipod:/ anymore.  The better options available are gtkpod (available in the repositories), and recent (i.e. bleeding edge, beta) versions of Amarok which use the same backend as gtkpod.

L.

---

### Post by Jucato on 2006-03-23
those "special urls" you mention are called kioslaves. In the KDE manual there's a description about them (or you can type help:/kioslaves). They're basically like shortcuts. media:/ displays the contents of /media, Trash:/ displays the contents of the trash folder, and http:/ displays the contents of web pages.

I'd like to share an old article that somehow gives you a glimpse of this (IMHO, wonderful) not well documented feature: (this is old, 2004) [http://osdir.com/Article2159.phtml](http://osdir.com/Article2159.phtml)

Btw, as to your first question, what specific instance are you having trouble with media:/ ?

---

### Post by ltmon on 2006-03-23
A known bug with ioslaves on kubuntu breezy is that non-kde apps are not configured to recognize some of them.

That is, if you have your default office document viewer set to openoffice.org, and you double-click on a *.osx document whilst in "system:/home" then openoffice will start with no document loaded... the URL of the document is not passed correctly to OO.

This can be fixed by modifying the .desktop launcher files for open office, but in breezy it is broken at install (unless it's been fixed... I've been using dapper for a while).

I'm pretty sure the same issue exists with any "media:/" uri.

L.

---

