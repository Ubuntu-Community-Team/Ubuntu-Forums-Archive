---
title: "umount cdrom from non-root account"
date: 2006-03-20
forum: General Help
---

### Post by man_stupendous on 2006-03-20
hi,

i am using hoary hedgehog 5.04. i logged into my friend's machine using guest account he had given me, inserted my cd into cdrom-drive ( ubuntu automounted it ), then when i tried eject , it say's only root ( my friend who has sudo privileges ) can unmount. Result : My cd is locked into the drive. i dont want to reboot the machine as my friend may be running some simulations. now is there no way to eject it other than calling him ( he is away the whole night ! ) . now i have to return the cd back in a few hours !!!!

why give me mount privileges when it is not going to allow me to unmount !!!

---

### Post by gerbman on 2006-03-20
[QUOTE=man_stupendous]hi,

i am using hoary hedgehog 5.04. i logged into my friend's machine using guest account he had given me, inserted my cd into cdrom-drive ( ubuntu automounted it ), then when i tried eject , it say's only root ( my friend who has sudo privileges ) can unmount. Result : My cd is locked into the drive. i dont want to reboot the machine as my friend may be running some simulations. now is there no way to eject it other than calling him ( he is away the whole night ! ) . now i have to return the cd back in a few hours !!!!

why give me mount privileges when it is not going to allow me to unmount !!![/QUOTE]

You can stick a paperclip (or even a mechanical pencil if you're good) in the manual ejection hole, as diagrammed [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-42471") (item number 5). The site says to turn off the power, but I have done it many times without doing so.

---

### Post by dcstar on 2006-03-21
[QUOTE=man_stupendous]hi,

i am using hoary hedgehog 5.04. i logged into my friend's machine using guest account he had given me, inserted my cd into cdrom-drive ( ubuntu automounted it ), then when i tried eject , it say's only root ( my friend who has sudo privileges ) can unmount. Result : My cd is locked into the drive. i dont want to reboot the machine as my friend may be running some simulations. now is there no way to eject it other than calling him ( he is away the whole night ! ) . now i have to return the cd back in a few hours !!!!

why give me mount privileges when it is not going to allow me to unmount !!![/QUOTE]
Ask you friend, he's probably changed the /etc/fstab file to make it behave exactly this way.

---

