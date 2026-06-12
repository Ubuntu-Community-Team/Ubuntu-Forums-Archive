---
title: "The terminal commant for 'safely remove drive'"
date: 2011-03-06
forum: General Help
---

### Post by oldmankit on 2011-03-06
If I click right-click on a drive in nautlius and do 'safely remove drive', the external hard-drive stops spinning.

What is the terminal equivalent?  If I do 'pumount' it is unmounted, but the hard-drive continues spinning.

---

### Post by jocko on 2011-03-06
I think "eject" will do it:
```
sudo eject /dev/sd[COLOR=Blue]X[/COLOR]
```

---

### Post by HermanAB on 2011-03-06
Lazy unmount:
$ sudo umount -l /media/whatever

---

### Post by oldmankit on 2011-03-11
Thanks, that's done the trick!

---

