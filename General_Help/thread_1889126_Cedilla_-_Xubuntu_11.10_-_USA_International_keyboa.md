---
title: "Cedilla - Xubuntu 11.10 - USA International keyboard"
date: 2011-11-30
forum: General Help
---

### Post by leandromartinez98 on 2011-11-30
Until Ubuntu 10.04 (which I use), I could use the 'c combination in the USA international with dead keys keyboard layout by changing the

/usr/lib/gtk-2.0/2.10.0/gtk.immodules

(adding "en" to the cedilla line, as described here:
[http://wiki.ubuntu-br.org/RodrigoLima/Cedilha](http://wiki.ubuntu-br.org/RodrigoLima/Cedilha)).

Now on 11.10, that files does not exist anymore. The file to be modified is

/usr/lib/gtk-3.0/3.0.0/immodules.cache

However, doing that does not work on LibreOffice (it worked before), although it works for most other applications, as firefox, the terminal, etc. That is, libreoffice keeps displaying an accented "c" instead of the ç letter.

Any help is appreciated. This cedilla problem is a recurrent issue for Brazilian users of Linux, and should be added as a standard keyboard layout configuration option for USA-international keyboards, at least.

---

### Post by Geremia on 2012-03-27
> **leandromartinez98 said:**
> However, doing that does not work on LibreOffice (it worked before), although it works for most other applications, as firefox, the terminal, etc. That is, libreoffice keeps displaying an accented "c" instead of the ç letter.I have the same problem: the compose key (multi_key) only works in certain applications. See [this thread]("http://www.linuxquestions.org/questions/showthread.php?p=4621294"), which unfortunately doesn't have any responses yet.

---

