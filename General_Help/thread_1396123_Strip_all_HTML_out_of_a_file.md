---
title: "Strip all HTML out of a file"
date: 2010-02-01
forum: General Help
---

### Post by benuski on 2010-02-01
Hi everybody,

I'm working on a masters paper and I'm analyzing the text in a lot of websites.  To download all the websites, I'm using wget, but that leaves me with HTML files.  I'm wondering if there's a quick way to strip all the html tags out of these files, leaving only the text.  If there's a way this could work over all the files in a directory, even better.

Thanks!

---

### Post by falconindy on 2010-02-01
[html2text](http://www.mbayer.de/html2text/) will do what you ask. There's a link to a .deb file on the homepage, but it's probably in the repos as well.

---

### Post by gnack on 2010-02-01
In addition, a couple of perl modules provide this functionality:

```

HTML::Strip
HTML::Parser

```

---

### Post by Johnny B on 2010-02-01
whenever i want to download text from a website i use 
$ lynx -dump
or 
$ links2 -dump

---

