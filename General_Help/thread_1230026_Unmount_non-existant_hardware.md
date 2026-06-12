---
title: "Unmount non-existant hardware"
date: 2009-08-02
forum: General Help
---

### Post by emeraldgirl08 on 2009-08-02
I have an icon on my desktop that refers to a cdrom0.

I had just gotten done watching a DVD and when I exited the Totem player there were two DVD icons.

I got rid of one by ejecting the DVD but now the other one won't go. I tried dismounting the drive- no go.

Any ideas?

---

### Post by yabbadabbadont on 2009-08-02
Logout and back in and see if it goes away.

---

### Post by HermanAB on 2009-08-02
To fix it the proper way, run 'mount' to see what is mounted, then do a 'lazy unmount' of the non-existent device:
$ mount
$ sudo umount -l /dev/cdrom0

---

