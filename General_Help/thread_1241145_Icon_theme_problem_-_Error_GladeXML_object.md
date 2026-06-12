---
title: "Icon theme problem - Error GladeXML object"
date: 2009-08-15
forum: General Help
---

### Post by mCion on 2009-08-15
So I've looked for an Icon Theme creator and this one looks pretty good (and also the only one I've found)

tango-generator [http://mejogid.ohallwebservices.com/site/index.php?q=node/1]("http://mejogid.ohallwebservices.com/site/index.php?q=node/1")

The .deb link for installation is broken so I had to compile it (first time doing this

Unpack
#make
#make install

I got an error on this line:8 of the makefile

```
print TEST
```

So I put a # to bypass that line

```
#print TEST
```

Now finally (I've been trying this for a while) I got the icon on Applications>System Tools>Tango Generator

When I run it I get this error message

> RuntimeError: could not create GladeXML object


I've reached my current limit.  NO idea what that means...

Help anybody

I'm on Jaunty

THANKS!

---

