---
title: "How to install pgfplots??"
date: 2009-12-09
forum: General Help
---

### Post by peter_kint on 2009-12-09
Hi,
I'm trying to install the pgplots manually, since I could not find it in synaptic.

The documentation says:
2.4.5   Installation Into a Local texmf-Directory
Copy pgfplots to a local texmf directory like ~/texmf in your home directory. Then, install pgfplots into the subdirectory texmf/tex/generic/pgfplots and run texhash.

I downloaded the package, extracted it to my desktop, it's called 'pgfplots' (with no extension)
 
How do I go from there?

PS. I read the general installing guidelines but I still can't manage
([http://amitech.50webs.com/installing/index.php.html#installing_with_terminal](http://amitech.50webs.com/installing/index.php.html#installing_with_terminal))

---

### Post by rafita on 2009-12-15
You have to create a directory texmf under your home directory, and extract the .zip
file there, so that, for example, the file pgfplots.sty is in  ~/texmf/tex/latex/pgfplots/pgfplots.sty.

After running texhash in a terminal, you can check if tex finds the file by running the command 

kpsewhich pgfplots.sty

---

### Post by skulda on 2010-02-19
You can also add the line
```
deb http://ppa.launchpad.net/johannes-reinhardt/ppa/ubuntu lucid main
```
to /etc/apt/sources.list (The developers of pgfplot recommend that, [http://sourceforge.net/projects/pgfplots/files/pgfplots/1.3/pgfplots_in_ubuntu.readme.txt/download](http://sourceforge.net/projects/pgfplots/files/pgfplots/1.3/pgfplots_in_ubuntu.readme.txt/download) )

There are no files for karmic in the repository, but for me (I'm using karmic) the lucid ones work fine...

---

