---
title: "Glade-2.6.8 Install problem"
date: 2005-02-05
forum: General Help
---

### Post by apoc on 2005-02-05
I've learned that apt-get rarely gets the latest version of a particular piece of software, and if you want the cutting edge you often have to download a tarball and compile the software yourself.

I found first glade 1 by useing apt-get, but it seemed "old" compared to the screenshots I saw on the homepage [http://glade.gnome.org/](http://glade.gnome.org/) so seeing that the later versions are called -2xxx I could get version -2 by apt-get, more particular -2.6.0.

The reson I would like to install 2.6.8 is that it mentiones in the tarball readfile that there should be a help menu in that version, I think that could help me get startet, so I went forth trying to install it. but even at the first step I run into a problem.

./configure seems to halt prematurely, since step 2 (make) does nothing at all.

The line I think is causeing it when running ./configure is  
> apoc@lypse-01:~/download/glade-2.6.8 $ ./configurechecking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

On a side question, It seems like quite a few programing languages can be used with the GUI that you make with Glade, the only other programing experience i have is with VB studio by makeing a small calculater after a guide, and starting to work with iFIX that uses VB language aswell.

---

### Post by DJ_Max on 2005-02-05
You need the Perl XML Parser module. You can install it via apt-get. do a search for it with apt-cache searc. Right now I'm not booted in Linux.

---

### Post by apoc on 2005-02-05
I got futher now :) I searched with synaptic for 'xml perl' and installed the one with the tiny ubuntu symbol.. I got futher this time.

> Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found

configure: error: Library requirements (libxml-2.0 >= 2.4.1 gtk+-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Is seems odd, the libxml-2.0 was already installed does anyone know if its not in a so called standard path, and if not can I ajust this?

---

### Post by DJ_Max on 2005-02-06
[QUOTE=apoc]I got futher now :) I searched with synaptic for 'xml perl' and installed the one with the tiny ubuntu symbol.. I got futher this time.



Is seems odd, the libxml-2.0 was already installed does anyone know if its not in a so called standard path, and if not can I ajust this?[/QUOTE]

You might need the libxml-2.0 development packages. It will be named something like libxml-2.0-dev. I'm not sure of the name as I'm not booted in Ubuntu.

---

