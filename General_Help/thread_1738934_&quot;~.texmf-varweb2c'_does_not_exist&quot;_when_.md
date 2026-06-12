---
title: "&quot;~/.texmf-var/web2c' does not exist&quot; when running MPost under Texmaker"
date: 2011-04-25
forum: General Help
---

### Post by opipa on 2011-04-25
I created a test.mp, and then I try to start "METAPOST" using tools->MPost, in the Messages box, I got the following:

```
Process started

kpathsea: Running mktexfmt mpost.mem

fmtutil: format directory `/home/username/.texmf-var/web2c' does not exist.

kpathsea: Running mktexfmt plain.mem

fmtutil: format directory `/home/username/.texmf-var/web2c' does not exist.

Process exited with error(s)
```

With the problem occured, I found this:
[HTML]http://www.gentoo.org/proj/en/tex/texlive-migration-guide.xml[/HTML]
My settings are the same to what he said,
```
$ kpsewhich --var-value=TEXMFMAIN
/usr/share/texmf
```
Now I am puzzled and appeal to your help.

---

### Post by opipa on 2011-04-25
I fixed this problem(install metapost!):
```
sudo apt-get install texlive-metapost
```

:D I thought it was installed automatically when installing texmaker.

---

