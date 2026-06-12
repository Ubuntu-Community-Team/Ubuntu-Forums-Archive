---
title: "I want a libexpat.so.1"
date: 2011-10-30
forum: General Help
---

### Post by &#20064;&#24815;&#20102;&#36828;&#31163; on 2011-10-30
Well, I want to install a software
and find that I need a libexpat.so.1 or libexpat.so.0
it's in /usr/lib
so, who can tell me where to get it?
I google it but no result
or, maybe you could just copy one from your pc and give me……
Thank you!

---

### Post by Script Warlock on 2011-10-30
> **&#20064 said:**
> Well, I want to install a software
and find that I need a libexpat.so.1 or libexpat.so.0
it's in /usr/lib
so, who can tell me where to get it?
I google it but no result
or, maybe you could just copy one from your pc and give me……
Thank you!

what software is that?

---

### Post by &#20064;&#24815;&#20102;&#36828;&#31163; on 2011-10-30
flashget

---

### Post by &#20064;&#24815;&#20102;&#36828;&#31163; on 2011-10-30
hmm,maybe you can mail to [email]snip[/email]
thank you

---

### Post by Lars Noodén on 2011-10-30
You can search [http://packages.ubuntu.com/](http://packages.ubuntu.com/search?searchon=contents&keywords=libexpat.so.1&mode=exactfilename&suite=oneiric&arch=any) for "packages that contain files named like this"  or you can use [dpkg -S */path/to/file*](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html) to do the same thing.

```

dpkg -S /lib/i386-linux-gnu/libexpat.so.1

```

---

### Post by gordintoronto on 2011-10-30
What version of Ubuntu?

libexpat1 contains the file you want.

---

### Post by oldos2er on 2011-10-30
```
apt-cache search libexpat
libexpat1 - XML parsing C library - runtime library
libexpat1-dev - XML parsing C library - development kit
libexpat-ocaml - OCaml expat bindings
libexpat-ocaml-dev - OCaml expat bindings
liblua5.1-expat-dev - libexpat development files for the Lua language version 5.1
```
liblua5.1-expat0 - libexpat bindings for the Lua language version 5.1

---

