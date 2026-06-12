---
title: "How do shared libraries work?"
date: 2011-02-28
forum: General Help
---

### Post by LBoksha on 2011-02-28
Some quick background: I need a newer (and, very likely, customized) version of GStreamer and its plugins that isn't provided in Maverick Meerkat's packages, so I've tried installing it (as well as the base plugins and The Good plugins) from source. Not all plugins compiled due to dependencies, but a good portion of them (including the one I want to modify) ended up just fine in /usr/local/lib. The problem: they're not being used. Even my freshly compiled gst-launch-0.10 binary (which sits in /usr/local/bin, as opposed to the old one which is in /usr/bin) seems to load the old shared libraries (which sit in /usr/lib)

I don't want to delete the old libraries, if only because I want to be able to revert to how everything was before I installed the new ones by removing all traces of it from /usr/local, but also because the set in /usr/local is not complete. (optimally, I want GStreamer to use the old libraries if a new one is not available)

However, as it is, the newly compiled libraries aren't used at all. So, since I can't seem to find anything about how shared libraries are used in Ubuntu, I was wondering: how does Ubuntu decide what library gets used when you start a program? How can you change this? How can I get Totem to use the newly compiled version of GStreamer along with the new plugins? (preferably without deleting the old ones)

Thanks!

---

### Post by LBoksha on 2011-03-01
I caved and simply replaced the offending library file completely (i.e. rename old one, copy in new one), but I'd still like to know if there's a more elegant way to override libraries without simply replacing them.

---

