---
title: "Installing mysql-query-browser"
date: 2005-02-18
forum: General Help
---

### Post by JNewman on 2005-02-18
Hi all,

First message to these forums, though I've been happily using Ubuntu (warty) for several months now. 

Has anyone installed **mysql-query-browser**? It seems to have been packaged for hoary, but not for warty, and several of the libraries it depends on aren't available for warty.

They are:

libglib2.0-0 (>= 2.6.0)
libgnomevfs2-0 (>= 2.9.2)
libgtk2.0-0 (>= 2.5.6)
libice6
libpango1.0-0 (>= 1.8.0) 
libmysqlclient14
mysql-query-browser-common (= 1.1.4-1)

Am I safe downloading and installing these? I don't want to break what I've got and have to reinstall Ubuntu (been there, did that once, so I'm a bit wary of unstable and experimental). (And where can I find them?)

Thanks!

---

### Post by grj on 2005-02-18
I cannot say that it will definately not hurt anything, but if you enable the universe repositories you will be able to install mysql-query-browser.

---

### Post by JNewman on 2005-02-18
[QUOTE=grj]I cannot say that it will definately not hurt anything, but if you enable the universe repositories you will be able to install mysql-query-browser.[/QUOTE]
-----

I enabled hoary universe (warty does not include mysql-query-browser but hoary does) and tried to use Synaptic to install mysql-query-browser. Unfortunately it seems as if this won't work. There are unresolved dependencies including at least one library that Synaptic seems to say cannot be installed (I couldn't figure out why not).

Has anyone gotten this to run under warty?

---

