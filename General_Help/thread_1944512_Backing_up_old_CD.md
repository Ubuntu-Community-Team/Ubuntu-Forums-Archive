---
title: "Backing up old CD"
date: 2012-03-21
forum: General Help
---

### Post by J V on 2012-03-21
I'm backing an old CD (1992) up to an ISO, cause it's getting fairly scratched and I don't have a backup, however this CD when inserted shows up as one audio CD and one data CD.

`dd if=/dev/sr0` doesn't work, and mount doesn't show anything mounted as the audio disc.

How do I correctly image the whole disc, including the audio?

---

### Post by winh8r on 2012-03-21
If it is an "Enhanced CD" type medium then you might consider using : EAC which you can find here:

[http://www.exactaudiocopy.de/en/index.php/]("http://www.exactaudiocopy.de/en/index.php/")

It will allow you to select how the content is ripped in order to prevent clashes between the audio and data portions of the disc.

Another option is to use K3B which is available in the repositories/Software Centre, the only disadvantage is that if you are not using the KDE desktop environment , it will pull in a large amount of KDE packages when you install it (possibly up to 200MB)

Hope this helps you in some way.

---

### Post by ksa618 on 2012-03-21
'dd' stops when it encounters read errors.
Your best bet to recover scratched CD's is probably the GNU data recovery tool. It's called gddrescue in the repositories.
Its usage is explained here:
[http://onubuntu.blogspot.com/2010/06/command-line-hard-disk-cloning-with.html](http://onubuntu.blogspot.com/2010/06/command-line-hard-disk-cloning-with.html)

I've succesfully used it to create ISO's from unplayable DVD's before.

---

### Post by J V on 2012-03-21
It doesn't matter, apparently my disc is scratched and I'll have to find a new source for it's contents. Thanks anyway.

---

