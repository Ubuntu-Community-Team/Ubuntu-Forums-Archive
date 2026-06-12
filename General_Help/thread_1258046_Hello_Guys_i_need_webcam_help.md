---
title: "Hello Guys i need webcam help"
date: 2009-09-04
forum: General Help
---

### Post by Japjeev on 2009-09-04
OK hello guys.

i need help adjusting my web cam. so i just bought Hercules optical web cam. and i put the usb in. nothing comes up... i need to install it so i can use the Mic. anyone know how i can install it? thanx in advance

---

### Post by hockeytux on 2009-09-04
Thats because there is no driver for it installed.

You can download the driver [here]("http://kiwilinux.org/public/gspca_sonixj.ko") (Its for a different Hercules cam but it should work).

Then go to Places > Computer > Filesystem /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca/ 

and place the downloaded driver file in there. Hope this does the trick...

---

### Post by P4man on 2009-09-04
Google gave me this:

[http://zzompp.hosting.mbar.fi/gregarius/feed.php?channel=15&iid=48977&y=2009&m=05&d=15](http://zzompp.hosting.mbar.fi/gregarius/feed.php?channel=15&iid=48977&y=2009&m=05&d=15)

---

### Post by Japjeev on 2009-09-04
> **hockeytux said:**
> Thats because there is no driver for it installed.

You can download the driver [here]("http://kiwilinux.org/public/gspca_sonixj.ko") (Its for a different Hercules cam but it should work).

Then go to Places > Computer > Filesystem /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca/ 

and place the downloaded driver file in there. Hope this does the trick...

sorry for the dumness so i put it this comes up There was an error moving the file into /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca.

---

