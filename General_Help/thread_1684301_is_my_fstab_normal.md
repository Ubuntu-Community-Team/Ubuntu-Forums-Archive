---
title: "is my fstab normal?"
date: 2011-02-08
forum: General Help
---

### Post by war.ace on 2011-02-08
Hi, I have been recently browsing the forum about editing write permissions and I saw people posting their fstabs and I decided to compare theirs from mine. well, mine looked very different and it looks like this:
> root@christopher-VGN-BX565B:/home/christopher# cat /etc/fstab
UUID=5c328e52-b977-4c3e-badb-cc6c49b3b348 / ext4 remount 0 1
UUID=6019fb7c-fdfd-49a2-a9b8-44b9cc1a2e10 swap swap sw 0 0

---

### Post by dcstar on 2011-02-08
> **war.ace said:**
> Hi, I have been recently browsing the forum about editing write permissions and I saw people posting their fstabs and I decided to compare theirs from mine. well, mine looked very different and it looks like this:

Considering that Ubuntu systems do not allow root command shells by default, and that is not a "standard" Ubuntu fstab file, then I can only assume that you are not using an Ubuntu system so the question cannot be answered.

---

### Post by war.ace on 2011-02-08
what do you mean I'm not using an ubuntu system?

edit: I typed su then my sudo password before I entered ```
cat /etc/fstab
```

---

### Post by wojox on 2011-02-08
It's a pretty normal Linux fstab. You have a /root partition which holds you entire OS and a Swap partition.

Like dcstar said you shouldn't really be monkeying around in root. ;)

Mine has been edited for Dropbox:

```

UUID=cdff9b24-f17d-4ab9-85cf-f097f06fc0ab none            swap    sw              0       0
UUID=d9f8a807-d220-4b48-bde5-d8a1d7b52c4b / ext4 errors=remount-ro,user_xattr 0 1


```

---

### Post by war.ace on 2011-02-08
> **wojox said:**
> It's a pretty normal Linux fstab. You have a /root partition which holds you entire OS and a Swap partition.

Like dcstar said you shouldn't really be monkeying around in root. ;)

Mine has been edited for Dropbox:

```

UUID=cdff9b24-f17d-4ab9-85cf-f097f06fc0ab none            swap    sw              0       0
UUID=d9f8a807-d220-4b48-bde5-d8a1d7b52c4b / ext4 errors=remount-ro,user_xattr 0 1


```
thank you for clearing that up for me :)
and I'll **try** not mess with root again. :P

---

