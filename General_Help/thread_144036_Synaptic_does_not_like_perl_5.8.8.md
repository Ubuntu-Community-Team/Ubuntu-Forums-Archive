---
title: "Synaptic does not like perl 5.8.8"
date: 2006-03-13
forum: General Help
---

### Post by ked on 2006-03-13
I tried installing some software from synaptic after upgrading to perl 5.8.8, but synaptic did not like that at all. 

Synaptic wants two perlmodules 'Debconf/Log.pm' and 'Unicode/string.pm', otherwise synaptic will crash

Does really Ubuntu require it's own perl version???????

Ked

---

### Post by #foobar on 2006-05-01
[QUOTE=ked]I tried installing some software from synaptic after upgrading to perl 5.8.8, but synaptic did not like that at all. 

Synaptic wants two perlmodules 'Debconf/Log.pm' and 'Unicode/string.pm', otherwise synaptic will crash

Does really Ubuntu require it's own perl version???????

Ked[/QUOTE]
I found this thread from a search, so if there is a newer one, or this has already been asnwered, I apologize. I recently had to deal with this and it was fixed like so:
```

cd /usr/local/lib/perl5/5.8.8/<arch name from install>/
sudo cp -r /usr/share/perl5/Debconf/* ./Debconf/
```
Obviously those dirs may not pertain to you, but if you compiled perl 5.8.8 from source yourself, you should know the right dirs (and the error message from apt will help with the dir things should be in).

---

