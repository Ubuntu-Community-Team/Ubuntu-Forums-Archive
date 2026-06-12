---
title: "ddrescue audio cd failure"
date: 2006-05-02
forum: General Help
---

### Post by chaumurky on 2006-05-02
I've used ddrescue for data discs before but with an audio cd I get 100% errors and a zero size image. It's not copy protected so what can I be doing wrong? It mounts fine as an audio disc but I'm trying to get past a small scratch. I entered "**ddrescue /dev/cdrom /media/edit/iOTA-Live.iso**" - that should be correct, shouldn't it? I tried "**dd if=/dev/cdrom of=/media/edit/iOTA-Live.iso**" and I immediately get:

```
dd: reading `/dev/hdd': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.254652 seconds, 0.0 kB/s

```

Substituting 'cdrom' with 'hdd' makes no difference. Strange huh?

---

