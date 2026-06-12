---
title: "AVG Problem"
date: 2010-02-06
forum: General Help
---

### Post by rocket16 on 2010-02-06
Hello all. I just installed avg85flx-r732-a3168.i386.deb, but I can't start AVG from any menu or command. (Not even in System Menu). So, how can I start it?

---

### Post by rocket16 on 2010-02-06
I tried the guide "[B]Making a launcher to start AVG

Code

sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop

add:
Code:

[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

save and exit.

You can now start AVG by going to Applications tab ---> System Tools.[/B]".

But this failed.

---

### Post by mushwars on 2010-02-06
```
sudo updatedb
locate -name avg
```-name should make it non-casesensitive.

that should locate it in the bin...

even easier do this

avg <tab> <tab> that will list the avalible names.


EDIT: saw your new post, looks like it is
```
avggui
```

EDIT2: hit alt+f2 then type avggui

---

### Post by rocket16 on 2010-02-06
Still, nothing happens. On "avggui" command, result comes "Command not found". And on issuing "locate -name avg" result is "invalid value `ame' of --limit".

---

### Post by mushwars on 2010-02-06
> **rocket16 said:**
> Still, nothing happens. On "avggui" command, result comes "Command not found". And on issuing "locate -name avg" result is "invalid value `ame' of --limit".
try just 
```
locate avg
```
dont have a debian os infront of me, so I couldnt test it.

---

### Post by typos1 on 2010-02-07
I ve had avg on my 64bit system since I first installed ubuntu (9.04) last July. 

The only time I have anything to do with it is that a minor error occurs whenever I install something-cant remember what it is but it doesnt effect anything.

I kind of assumed avg ran in the background and would tell me if there was a securtiy prob.

Anyway if I type "locate avg" in a terminal I get the following, if its any help:

```
desktop:~$ locate avg
/etc/avg.conf
/etc/init.d/avgd
/etc/rc0.d/K20avgd
/etc/rc1.d/K20avgd
/etc/rc2.d/S20avgd
/etc/rc3.d/S20avgd
/etc/rc4.d/S20avgd
/etc/rc5.d/S20avgd
/etc/rc6.d/K20avgd
/opt/avg
/opt/avg/avg8
/opt/avg/avg8/bin
/opt/avg/avg8/cfg
/opt/avg/avg8/doc
/opt/avg/avg8/etc
/opt/avg/avg8/lib
/opt/avg/avg8/log
/opt/avg/avg8/man
/opt/avg/avg8/update
/opt/avg/avg8/var
/opt/avg/avg8/bin/avgavid
/opt/avg/avg8/bin/avgcfgctl
/opt/avg/avg8/bin/avgctl
/opt/avg/avg8/bin/avgd
/opt/avg/avg8/bin/avgdump
/opt/avg/avg8/bin/avgoad
/opt/avg/avg8/bin/avgscan
/opt/avg/avg8/bin/avgscand
/opt/avg/avg8/bin/avgsched
/opt/avg/avg8/bin/avgspamd
/opt/avg/avg8/bin/avgtcpd
/opt/avg/avg8/bin/avgupd
/opt/avg/avg8/bin/avgupdate
/opt/avg/avg8/bin/avgwrapper.sh
/opt/avg/avg8/cfg/dfncfg.dat
/opt/avg/avg8/cfg/dump.ini
/opt/avg/avg8/doc/ChangeLog
/opt/avg/avg8/doc/README
/opt/avg/avg8/doc/README.amavis
/opt/avg/avg8/doc/README.exim
/opt/avg/avg8/doc/README.postfix
/opt/avg/avg8/doc/README.qmail
/opt/avg/avg8/doc/README.qmailscanner
/opt/avg/avg8/doc/README.sendmail
/opt/avg/avg8/doc/license_cz_utf8.txt
/opt/avg/avg8/doc/license_us.txt
/opt/avg/avg8/etc/avg.conf
/opt/avg/avg8/etc/init.d
/opt/avg/avg8/etc/init.d/avgd.all
/opt/avg/avg8/etc/init.d/avgd.gentoo
/opt/avg/avg8/etc/init.d/avgdinit.conf
/opt/avg/avg8/etc/init.d/functions.common
/opt/avg/avg8/etc/init.d/functions.deb
/opt/avg/avg8/etc/init.d/functions.freebsd
/opt/avg/avg8/etc/init.d/functions.gentoo
/opt/avg/avg8/etc/init.d/functions.mdk
/opt/avg/avg8/etc/init.d/functions.rh
/opt/avg/avg8/etc/init.d/functions.slack
/opt/avg/avg8/etc/init.d/functions.suse
/opt/avg/avg8/etc/init.d/functions.ubuntu
/opt/avg/avg8/lib/libavgaspam.so
/opt/avg/avg8/lib/libavgcfg.so
/opt/avg/avg8/lib/libavgcore.so
/opt/avg/avg8/lib/libavginet.so
/opt/avg/avg8/lib/libavglng.so
/opt/avg/avg8/lib/libavglogd.so
/opt/avg/avg8/lib/libavgupd.so
/opt/avg/avg8/lib/libdazukofs.so
/opt/avg/avg8/lib/libgcc_s.so.1
/opt/avg/avg8/lib/libspamcatcher.so
/opt/avg/avg8/lib/libstdc++.so.6
/opt/avg/avg8/log/0
/opt/avg/avg8/log/0/common.priv.rollog
/opt/avg/avg8/log/0/common.priv.rollog.lock
/opt/avg/avg8/man/man1
/opt/avg/avg8/man/man5
/opt/avg/avg8/man/man1/avgavid.1.gz
/opt/avg/avg8/man/man1/avgcfgctl.1.gz
/opt/avg/avg8/man/man1/avgctl.1.gz
/opt/avg/avg8/man/man1/avgd.1.gz
/opt/avg/avg8/man/man1/avgdump.1.gz
/opt/avg/avg8/man/man1/avgoad.1.gz
/opt/avg/avg8/man/man1/avgscan.1.gz
/opt/avg/avg8/man/man1/avgscand.1.gz
/opt/avg/avg8/man/man1/avgsched.1.gz
/opt/avg/avg8/man/man1/avgspamd.1.gz
/opt/avg/avg8/man/man1/avgtcpd.1.gz
/opt/avg/avg8/man/man1/avgupd.1.gz
/opt/avg/avg8/man/man1/avgupdate.1.gz
/opt/avg/avg8/var/antispam
/opt/avg/avg8/var/data
/opt/avg/avg8/var/run
/opt/avg/avg8/var/antispam/approvedsenders
/opt/avg/avg8/var/antispam/blockedsenders
/opt/avg/avg8/var/antispam/sc1.bin.full
/opt/avg/avg8/var/antispam/sc10.bin.full
/opt/avg/avg8/var/antispam/sc11.bin.full
/opt/avg/avg8/var/antispam/sc12.bin.full
/opt/avg/avg8/var/antispam/sc14.bin.full
/opt/avg/avg8/var/antispam/sc2.bin.full
/opt/avg/avg8/var/antispam/sc5.bin.full
/opt/avg/avg8/var/antispam/sc6.bin.full
/opt/avg/avg8/var/antispam/sc9.bin.full
/opt/avg/avg8/var/antispam/scbin.txt
/opt/avg/avg8/var/antispam/spamcatcher.conf
/opt/avg/avg8/var/data/avg8us.lng
/opt/avg/avg8/var/data/avi7.avg
/opt/avg/avg8/var/data/incavi.avm
/opt/avg/avg8/var/data/microavi.avg
/opt/avg/avg8/var/data/miniavi.avg
/usr/bin/avgcfgctl
/usr/bin/avgctl
/usr/bin/avgdump
/usr/bin/avgscan
/usr/bin/avgupdate
/usr/share/man/man1/avgavid.1.gz
/usr/share/man/man1/avgcfgctl.1.gz
/usr/share/man/man1/avgctl.1.gz
/usr/share/man/man1/avgd.1.gz
/usr/share/man/man1/avgdump.1.gz
/usr/share/man/man1/avgoad.1.gz
/usr/share/man/man1/avgscan.1.gz
/usr/share/man/man1/avgscand.1.gz
/usr/share/man/man1/avgsched.1.gz
/usr/share/man/man1/avgspamd.1.gz
/usr/share/man/man1/avgtcpd.1.gz
/usr/share/man/man1/avgupd.1.gz
/usr/share/man/man1/avgupdate.1.gz
/var/lib/dpkg/info/avg85flx.conffiles
/var/lib/dpkg/info/avg85flx.list
/var/lib/dpkg/info/avg85flx.postinst
/var/lib/dpkg/info/avg85flx.postrm
/var/lib/dpkg/info/avg85flx.preinst
/var/lib/dpkg/info/avg85flx.prerm

```

---

