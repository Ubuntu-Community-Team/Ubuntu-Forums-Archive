---
title: "/boot wont mount"
date: 2010-04-06
forum: General Help
---

### Post by evilnone on 2010-04-06
I installed the beta today from the image found on the website.  Everything was working fine until I did the updates when they came up.  I was using kernel 2.6.32-16 and it worked fine, when the new kernel 2.6.32-19 installed it stopped working.

I get the following message when trying to boot in to the system after the update.
"The disk drive for /boot is not ready yet or not present"

When i boot back to 2.6.32-16 it works fine after a few weird warning on the ubuntu splash screen.

Any thoughts on what I can do?  Also I included a pic for reference.


[IMG]http://img542.imageshack.us/img542/8571/photos.jpg[/IMG]

[IMG]http://img56.imageshack.us/img56/6229/photobp.jpg[/IMG]

---

### Post by -humanaut- on 2010-04-06
This sounds reminisce of a problem Fedora was having If its the same bug you'll need a atleast a 300mb /boot partition.

---

### Post by evilnone on 2010-04-06
that did it, works fine when i changed from 128mb /boot to 500mb

---

