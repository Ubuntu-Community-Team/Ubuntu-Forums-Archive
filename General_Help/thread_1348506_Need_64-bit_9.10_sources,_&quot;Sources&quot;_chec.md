---
title: "Need 64-bit 9.10 sources, &quot;Sources&quot; check box not staying checked."
date: 2009-12-07
forum: General Help
---

### Post by wkulecz on 2009-12-07
I managed to post this just before the 64-bit forum was shutdown :(

[http://ubuntuforums.org/showthread.php?t=1336508](http://ubuntuforums.org/showthread.php?t=1336508)

So I'm asking again here.  How do I get the Ubuntu 9.10 64-bit sources?  The "Sources" check box doesn't stay checked in "software sources" and synaptic shows no source package options.

I need the sources used to build the 9.10 version of gstreamer.

Also, why no Glade3 for 9.10 64-bit?

--wally.

---

### Post by mc4man on 2009-12-07
Can't remember when I've last seen the source box "checked" other than on a live cd.
'Colored in' means it's enabled, you can d. check your sources.list for deb-src entries
```
cat /etc/apt/sources.list
```

If you want a source then apt-get it ( no sudo

apt-get source [COLOR="Blue"]whatever[/COLOR]

or search packages.ubuntu.com and dl the source and .diff, dsc. if desired

[http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gstreamer](http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gstreamer)

---

### Post by wkulecz on 2009-12-10
deb-src is uncommented in my apt/sources.list.

Still can't see any source packages in Synaptic.

apt-get source gstreamer gives:
E unable to find source package for gstreamer


Without being able to browse the source packages in Synaptic, how am I to figure out the names of the bits and pieces?

---

