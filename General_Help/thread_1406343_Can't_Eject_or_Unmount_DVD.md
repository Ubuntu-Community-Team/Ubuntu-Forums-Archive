---
title: "Can't Eject or Unmount DVD"
date: 2010-02-13
forum: General Help
---

### Post by nothingface1 on 2010-02-13
I am in the middle of copying a dvd with k9copy and it is asking me to insert a recordable dvd... so i try to eject and it won't let me, it says failed to eject media one or more volumes are in use. There is nothing else using the disc so I don't get it? Can anyone help?

---

### Post by Miljet on 2010-02-13
Are you using a desktop or laptop? Most laptop DVD drives have a small hole in the face. You can use a straightened paper clip or similar device to trip the drive open.

---

### Post by flippo on 2010-02-13
You can also force it to unmount ```
sudo umount -fl <mounted device>
```

then eject it```
sudo eject <device>
```

---

### Post by old fert on 2010-02-14
Thanks, amazing how often I find answers to my problems.  "sudo eject dvd" worked great.  sudo unmount command wasn't even necessary..Thanks again.

---

