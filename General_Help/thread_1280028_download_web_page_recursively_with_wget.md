---
title: "download web page recursively with wget"
date: 2009-10-01
forum: General Help
---

### Post by pythonscript on 2009-10-01
How can I download a web page recursively with wget? For example, if I want to download:

[http://www.mywebpage.com/](http://www.mywebpage.com/)*firstlevel/secondlevel*

that contains a whole list of folders/files. How can I download that entire directory structure, without including the top level domain? I tried this with 

```
wget -R http://www.mywebpage.com/*firstlevel/secondlevel*
```

but it started downloading [http://www.mywebpage.com](http://www.mywebpage.com), starting from the top level, which I don't want. Any ideas? Thanks!

---

### Post by diesch on 2009-10-01
Use -np to make wget to not ascend to the parent directory:
```

wget -R -np http://www.mywebpage.com/firstlevel/secondlevel

```

---

### Post by pythonscript on 2009-10-01
I don't know... that still isn't downloading all the files. It just downloads index.html and stops. It doesn't move to the parent directory, but it won't download any of the child directories. Thanks!

---

### Post by varkey on 2010-03-27
Even I have the same issue. It just downloads the index.html file and doesn't actually recurse into the directories.

---

### Post by mIXpRo on 2010-03-27
this will help you :
 
[http://www.computerhope.com/unix/wget.htm](http://www.computerhope.com/unix/wget.htm)

---

### Post by fragos on 2010-03-27
Excuse me but isn't recursive a small "r". "wget -r [domain URL]" downloads all files referenced in the HTML but not images referenced in the CSS file. It also downloads PHP files as their HTML output with a PHP extension.

---

