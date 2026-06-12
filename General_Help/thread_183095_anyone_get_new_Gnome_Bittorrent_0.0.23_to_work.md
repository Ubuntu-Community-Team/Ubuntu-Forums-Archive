---
title: "anyone get new Gnome Bittorrent 0.0.23 to work?"
date: 2006-05-27
forum: General Help
---

### Post by rpesq on 2006-05-27
Hi,

Apparently there is a new release of Gnome bittorrent, ver 0.0.23.

See-
[http://sourceforge.net/project/showfiles.php?group_id=93129](http://sourceforge.net/project/showfiles.php?group_id=93129)

Has anyone managed to get this to actually work?  Thanks in advance.

---

### Post by npodges on 2006-05-27
yeah, i got it to work just fine.

download the deb from the sourceforge page and do "sudo dpkg -i dsfsdfsdfsdfsdf.deb"

then, it will probably tell you it depends on python-glade2, so do

sudo apt-get install python-glade2

it will probably tell you that also has dependencies problems, do:

sudo apt-get -f install

then, try reinstalling the deb. that worked fine for me.

---

