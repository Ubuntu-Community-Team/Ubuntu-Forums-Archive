---
title: "NTFS Drives blank after apt-get upgrade"
date: 2010-05-30
forum: General Help
---

### Post by jameyc on 2010-05-30
Two ntfs partitions appear to be blank, after an apt-get upgrade in Kubuntu Lucid.

The partitions are on two separate drives, so I doubt this is a hardware issue.

Main drive (sata):
/dev/sdb1 - NTFS - Main Win7 partition, appears blank
/dev/sdb5 - EXT4 - Linux root partition, functioning normally.
/dev/sdb6 - swap - functioning normally

Extra drive (pata):
/dev/sda5 - NTFS - Backup/multimedia, appears blank.

I don't see anything drive related in the upgrade, other than mountall (which I doubt is the problem.)

The apt log for the particular upgrade shows the following:

```
Start-Date: 2010-05-22  01:30:58
Upgrade: plasma-widget-kimpanel-backend-ibus (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), apt-transport-https (0.7.25.3ubuntu8, 0.7.25.3ubuntu9), libglib2.0-data (2.24.0-0ubuntu4, 2.24.1-0ubuntu1), plasma-wallpapers-addons (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), libpangomm-1.4-1 (2.26.1-1, 2.26.2-0ubuntu1), mysql-server (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), chromium-browser (6.0.404.0~svn20100514r47231-0ubuntu1~ucd1~lucid, 6.0.412.0~svn20100521r47875-0ubuntu1~ucd1~lucid), php5 (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), plasma-widget-kimpanel (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), kdeplasma-addons (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), libapache2-mod-php5 (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), mysql-server-core-5.1 (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), php5-snmp (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), php5-gd (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), libglib2.0-0
(2.24.0-0ubuntu4, 2.24.1-0ubuntu1), libmysqlclient16 (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), plasma-dataengines-addons (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), libglibmm-2.4-1c2a (2.24.1-1, 2.24.2-0ubuntu1), apt-utils (0.7.25.3ubuntu8, 0.7.25.3ubuntu9), apt (0.7.25.3ubuntu8, 0.7.25.3ubuntu9), php5-curl (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), mysql-client-core-5.1 (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), libglib2.0-dev (2.24.0-0ubuntu4, 2.24.1-0ubuntu1), plasma-widgets-addons (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), plasma-widget-lancelot (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), plasma-runners-addons (4.4.2-0ubuntu1,
4.4.2-0ubuntu2), liblancelot0 (4.4.2-0ubuntu1, 4.4.2-0ubuntu2), libpq5 (8.4.3-1, 8.4.4-0ubuntu10.04), chromium-browser-inspector (6.0.404.0~svn20100514r47231-0ubuntu1~ucd1~lucid, 6.0.412.0~svn20100521r47875-0ubuntu1~ucd1~lucid), php5-mysql
(5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), php5-cli (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), mountall (2.14, 2.15), mysql-common (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), php5-common (5.3.2-1ubuntu4.1, 5.3.2-1ubuntu4.2), mysql-server-5.1 (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1), mysql-client-5.1 (5.1.41-3ubuntu12, 5.1.41-3ubuntu12.1)
End-Date: 2010-05-22  01:34:36
```

I'm not convinced that the upgrade did it, though it was one of the only changes to the system in recent weeks, so it's one of the few things I have to go on.

Win7 won't boot, with "BOOTMGR is missing" as one would expect.

More curious, the windows partition still seems to have a couple directories still, in program data and user/local/appdata, "Game Explorer" in both. I swear when the problem began these didn't exist, it's as though they came back in the meantime. I may be mistaken.

Doubtful that Windows caused the issue, it's rarely ever used, though kept fairly well updated. I'd last booted to it about 3 days prior, for around 15 minutes to compile something.

I don't see any recent bugs in Fuse that would seem to cause this behavior, so I'm a bit stumped.

I'm assuming that somehow recovering or undeleting might be possible, hoping someone can point me in the right direction. I've avoided writing the drives, and left them unmounted. Most of the repair tools I've found so far require extra space to undelete to, which isn't an option here (though since the drives appear to not be damaged, I hope I can do so in place.)

Thanks,
Jamey

---

### Post by dino99 on 2010-05-30
[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by jameyc on 2010-05-30
I've had decent luck with testdisk seeming to see my old files when using it's undelete but there's no way to restore them in place.

I'm hoping maybe there's some sort of mft rebuild tool that can rebuild the table in place.

---

