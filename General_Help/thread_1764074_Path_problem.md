---
title: "Path problem"
date: 2011-05-21
forum: General Help
---

### Post by Nick Hopton on 2011-05-21
I've just installed a software package, GDAL 1.8, from source on 11.04 (amd64). The install instructions tell me this:

"In order to run GDAL after installing it is necessary for the shared library to be findable. This can often be accomplished by setting LD_LIBRARY_PATH to include /usr/local/lib."

I'm not sure how I do this, it appears that 'LD_LIBRARY_PATH cannot be set in $HOME/.profile' any more. Apparently, I must use '/etc/ld.so.conf.d/*.conf configuration files' instead.

The files I have in '/etc/ld.so.conf.d/' are as follows:

```

biarch-compat.conf
lib32asound2.conf
libc.conf
GL.conf
libasound2.conf
x86_64-linux-gnu.conf
```

Do I add the path specification to one of these files, or do I make a new *.conf file? What form would the line that I have to add take?

I've been using Linux off-and-on for years, but have never had cause to delve into its internals much; any help would be greatly appreciated.

Regards, Nick.

---

### Post by Nick Hopton on 2011-05-22
Forgive me for bumping this, but I'm really in trouble here.

Regards, Nick.

---

