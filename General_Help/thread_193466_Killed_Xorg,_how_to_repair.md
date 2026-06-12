---
title: "Killed Xorg, how to repair?"
date: 2006-06-10
forum: General Help
---

### Post by Trab on 2006-06-10
hello,
i killed my xorg.conf.
not badly, im still running X (Even after rebooting it) but its not as good as it was before.
i tried messing around with XGL and compiz (or w/e they are) got tired of it, and quit halfway through.
everything worked fine.
now, i had to reinstall cedega on a different issue.
during the test, the first 2 tests fail, they are
openGL direct rendering
3d accelerations

i got 3d accelerations to work again, but now its broken...
also when trying to run steam, i get this terminal error (dunno if its related, its new tho...)
```

X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3730
  Current serial number in output stream:  3738
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x3c0037d
  Serial number of failed request:  3733
  Current serial number in output stream:  3738

```

could someone tell me how to repair Xorg.conf?
i know i should have backups, but none of them seem to work either...

any way to just get it to config itself?

i have an Nvidia card.
thanks
-Trab

---

### Post by Ragazzo on 2006-06-10
Try "sudo dpkg-reconfigure xserver-xorg".

---

### Post by Trab on 2006-06-10
half repaired it, got openGL direct rendering working (which is wat i used to have)
would like to get 3d acceleration too tho... and ideas?
ill try the dpkg command soon
latz
-Trab

---

### Post by _simon_ on 2006-06-10
it's probably the driver. 

Look for the section in xorg.conf for your video card and make sure the driver is "nvidia" and not "nv".

If all you did was mess up xorg.conf the correct driver should still be installed so that should.... just work...

---

### Post by Trab on 2006-06-15
it is not the driver,  driver is set to nvidia.
ugh, this is so annoying, if i run
```
 sudo dpkg-reconfigure xserver-xorg 
```
then restart x, it fails.... so then i go to a shell ( ctrl + F1) edit one thing (i forget wat it is...) then type startx and openGL Direct Rendering then works.
but if i restart the machine, and X loads normally, it doesnt work!
this is VERY annoying!

help?
thanks
-Trab

---

