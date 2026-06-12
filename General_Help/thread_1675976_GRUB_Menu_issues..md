---
title: "GRUB Menu issues."
date: 2011-01-26
forum: General Help
---

### Post by skarloeyleopard on 2011-01-26
Hello all, I'm having a few issues with changing my GRUB menu I know how to do it and everything, but sadly it seems protected. I can't edit it at all.

Here's a screenshot of my issue:

[IMG]http://i1096.photobucket.com/albums/g334/skarloeyforty/Screenshot.png[/IMG]

Could anybody help? I want Windows 7 at the top, followed by all of the Ubuntu options.

Thanks :)

---

### Post by maghoxfr on 2011-01-26
I downloaded Grub Customizer and it solver all my problems, it's really easy and I had no problems with it so far.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by Cavsfan on 2011-01-26
Try the tutorial in my sig. and put windows as the first entry in 06_custom and make the default 0. 
That will do exactly what you want.

---

### Post by rocthrttle on 2011-01-26
an alternative option if the customizer doesn't work:

if you want windows 7 to be the default and not mess around with the list order.

use "startup-manager" found in the ubuntu software center to change the default and most any other options that you want. the benefit is that it is a canonical supported program that you can trust.

---

### Post by skarloeyleopard on 2011-01-26
> **maghoxfr said:**
> I downloaded Grub Customizer and it solver all my problems, it's really easy and I had no problems with it so far.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

That worked fine, thanks :)

---

### Post by Cavsfan on 2011-01-26
Here is what my GRUB2 menu currently looks like. You would just put the windows 7 part on top.

[[img]http://ompldr.org/tNzV0cQ[/img]](http://ompldr.org/vNzV0cQ)

---

### Post by maghoxfr on 2011-01-26
> **skarloeyleopard said:**
> That worked fine, thanks :)

I'm glad it helped!

---

