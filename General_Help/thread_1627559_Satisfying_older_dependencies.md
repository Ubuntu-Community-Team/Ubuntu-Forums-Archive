---
title: "Satisfying older dependencies"
date: 2010-11-21
forum: General Help
---

### Post by psyphen on 2010-11-21
I'm trying to install sphinxsearch, and I'm getting a missing dependency "libmysqlclient.so.15". Now, I have libmysqlclient.so.16, the newer version of the library, but even when I make a link in the same folder to the newer library from libmysqlclient.so.15 I still get this same dependency error. What else do I have to do to make the computer believe I have the *.15 version of the library as well? I tried search around, and I couldn't find a useful answer. Everyone always says just to link the library from whatever version you need to the one you have.

Thanks for your potential insight! It's much appreciated.

---

### Post by mc4man on 2010-11-21
sphinxsearch is available in repo for 10.04 and 10.10 using the 16 lib.
What release are you running? (and where is your sphinxsearch coming from?

I'd try using a repo version 1st.

You could probably install the [older libmysqlclient]("http://packages.ubuntu.com/karmic/libmysqlclient15off") without issue though above is better solution, if applicable. (or re-build to use the 16 lib

---

