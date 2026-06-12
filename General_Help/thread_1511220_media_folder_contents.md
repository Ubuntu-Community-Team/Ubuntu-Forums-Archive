---
title: "/media folder contents"
date: 2010-06-16
forum: General Help
---

### Post by nemiux on 2010-06-16
Hello,

Once I tried to open my USB stick on ubuntu, but it didn't work, and I found some guide to create folders in /media so it might work. However, I don't need it anymore, and I don't know how to remove them. It looks displayed in thumbnail. Is there any way I could remove usb1, usb2, usb3, ubuntu8 and ubuntu-8.10-desktop-i386.iso?

TY

---

### Post by michaelgilch on 2010-06-16
Yes you can.

If you go to a Terminal (Applications | Accessories | Terminal) and navigate to the media directory:

```
cd /media
```

then remove the folders with su permissions:

```
sudo rmdir usb1 usb2 usb3
```

It will prompt for a password and you should be all set.

---

### Post by ThesaurusRex on 2010-06-16
If there are "files" inside the "directories," you may need to resort to: ```
rm -rf usb1 usb2 usb3
```

---

### Post by KeyserSoze93 on 2010-06-16
> **ThesaurusRex said:**
> If there are "files" inside the "directories," you may need to resort to: ```
rm -rf usb1 usb2 usb3
```

Though not if your USB disk is mounted.

Try:

```

for i in /media/usb*; do mountpoint $i || sudo rm -rv $i; done

```

Just remember to be careful with rm -rv when running as root.

---

### Post by jerome1232 on 2010-06-16
That's why you should just use rmdir, I don't think the op wants to remove them if they have files in them. safer is always better.

---

