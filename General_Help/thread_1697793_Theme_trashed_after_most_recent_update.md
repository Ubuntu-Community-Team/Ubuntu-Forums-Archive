---
title: "Theme trashed after most recent update"
date: 2011-03-01
forum: General Help
---

### Post by twinspop on 2011-03-01
Fonts for the menus are huge, the elegant window decorations and buttons have been replaced with old school X ugliness. Colors have changed.

I've tried changing a few things, like font size, but the changes have no effect.

I'm running 10.04 and just ran the update this morning. 24 days since my last.

Halp?

---

### Post by searchfgold6789 on 2011-03-01
What did the update do (/var/log/dpkg)?

---

### Post by twinspop on 2011-03-01
> **searchfgold6789 said:**
> What did the update do (/var/log/dpkg)?

```
2011-03-01 06:20:58 startup archives unpack
2011-03-01 06:21:04 upgrade tzdata 2010o-0ubuntu0.10.04 2011b-0ubuntu0.10.04
2011-03-01 06:21:06 startup packages configure
2011-03-01 06:21:06 configure tzdata 2011b-0ubuntu0.10.04 2011b-0ubuntu0.10.04
2011-03-01 06:21:07 startup archives unpack
2011-03-01 06:21:08 upgrade xkb-data 1.8-1ubuntu8 1.8-1ubuntu8.1~10.04.1
2011-03-01 06:21:09 upgrade fuse-utils 2.8.1-1.1ubuntu2.2 2.8.1-1.1ubuntu3
2011-03-01 06:21:11 upgrade libfuse2 2.8.1-1.1ubuntu2.2 2.8.1-1.1ubuntu3
2011-03-01 06:21:12 upgrade brasero-common 2.30.2-0ubuntu1 2.30.2-0ubuntu1.1
2011-03-01 06:21:14 upgrade libbrasero-media0 2.30.2-0ubuntu1 2.30.2-0ubuntu1.1
2011-03-01 06:21:15 upgrade brasero 2.30.2-0ubuntu1 2.30.2-0ubuntu1.1
2011-03-01 06:21:16 upgrade gdm 2.30.2.is.2.30.0-0ubuntu4 2.30.2.is.2.30.0-0ubuntu5
2011-03-01 06:21:21 upgrade mysql-common 5.1.41-3ubuntu12.9 5.1.41-3ubuntu12.10
2011-03-01 06:21:22 upgrade libmysqlclient16 5.1.41-3ubuntu12.9 5.1.41-3ubuntu12.10
2011-03-01 06:21:23 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-03-01 06:21:26 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-03-01 06:21:30 trigproc shared-mime-info 0.71-1ubuntu2 0.71-1ubuntu2
2011-03-01 06:21:31 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-03-01 06:21:31 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-03-01 06:21:34 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-03-01 06:21:34 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2011-03-01 06:21:34 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-03-01 06:21:40 startup packages configure
2011-03-01 06:21:40 configure xkb-data 1.8-1ubuntu8.1~10.04.1 1.8-1ubuntu8.1~10.04.1
2011-03-01 06:21:40 configure libfuse2 2.8.1-1.1ubuntu3 2.8.1-1.1ubuntu3
2011-03-01 06:21:40 configure fuse-utils 2.8.1-1.1ubuntu3 2.8.1-1.1ubuntu3
2011-03-01 06:21:40 configure brasero-common 2.30.2-0ubuntu1.1 2.30.2-0ubuntu1.1
2011-03-01 06:21:41 configure libbrasero-media0 2.30.2-0ubuntu1.1 2.30.2-0ubuntu1.1
2011-03-01 06:21:41 configure brasero 2.30.2-0ubuntu1.1 2.30.2-0ubuntu1.1
2011-03-01 06:21:41 configure gdm 2.30.2.is.2.30.0-0ubuntu5 2.30.2.is.2.30.0-0ubuntu5
2011-03-01 06:21:42 configure mysql-common 5.1.41-3ubuntu12.10 5.1.41-3ubuntu12.10
2011-03-01 06:21:42 configure libmysqlclient16 5.1.41-3ubuntu12.10 5.1.41-3ubuntu12.10
2011-03-01 06:21:42 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-03-01 06:21:43 trigproc initramfs-tools 0.92bubuntu78 0.92bubuntu78
2011-03-01 06:21:52 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
```

---

### Post by twinspop on 2011-03-01
compiz base pkg was no longer installed. I reinstalled it, but haven't had time to restart gnome.

---

