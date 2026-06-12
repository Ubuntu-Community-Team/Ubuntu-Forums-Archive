---
title: "cssh not reading cluster tags from .csshrc file?"
date: 2010-02-08
forum: General Help
---

### Post by lylex on 2010-02-08
When using cssh, I define some cluster tags in my local .csshrc file.  Other parameters seem to be picked up by cssh, but the tags are not.

I have no /etc/clusters or /etc/csshrc files.  I create a fresh, default .csshrc file and append a line like:
      myhost = frodo

When executing "cssh myhost", I get: Can't call method "name" on an undefined value at /usr/bin/cssh line 988

This is the same message I get if I make up some destination, like: "cssh doesnotexist".  So it looks like rather than picking up the tag "myhost" from .csshrc, and translating the command to "cssh frodo", it does a dns lookup on myhost.

I've tried making a /etc/csshrc file like this (but without the equal sign), but that doesn't work either.  This is all on Ubuntu 9.10 with cssh version 273.

Thanks for any help....Lyle

---

### Post by tfejos on 2010-04-08
I had the same problem until discovered /etc/clusters file.
Should used without equal signs ie. cluster1 host1 host2. It works for me.

---

