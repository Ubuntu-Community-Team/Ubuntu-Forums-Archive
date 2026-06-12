---
title: "libjpeg.so.62 problem"
date: 2011-09-18
forum: General Help
---

### Post by shaw_dave on 2011-09-18
Hi there, 
I am using ubuntu 10.10
not sure how i managed it, but rhythmbox and ubuntu software centre wouldnt open, no reason was given.
Upon trying to run them from the terminal, i got errors about libjpeg.so.62 not being available

software centre:
ImportError: libjpeg.so.62: cannot open shared object file: No such file or directory

Rhythmbox:
rhythmbox: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

Anyone know what has happened and how i can fix it??

cheers in advance

---

### Post by debd on 2011-09-18
the file libjpeg.so.62(in /usr/lib/libjpeg.so.62)
 belongs to the package libjpeg62
so try to reinstall(that shoud've already been installed) the package
```
sudo apt-get install libjpeg62
```

---

### Post by Glutanimate on 2012-08-06
> **debd said:**
> the file libjpeg.so.62(in /usr/lib/libjpeg.so.62)
 belongs to the package libjpeg62
so try to reinstall(that shoud've already been installed) the package
```
sudo apt-get install libjpeg62
```

Thank you very much. This worked great for executing [ITK-SNAP]("http://www.itksnap.org/pmwiki/pmwiki.php") on Precise.

---

