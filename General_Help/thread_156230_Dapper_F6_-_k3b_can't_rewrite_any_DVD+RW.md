---
title: "Dapper F6 - k3b can't rewrite any DVD+RW"
date: 2006-04-06
forum: General Help
---

### Post by kshitij on 2006-04-06
System Details:
---------------
I have Dapper Flight 6 on AMD sempron 2400, 1GB RAM. m/c with BenQ DQ60 DVD writer. I have not installed KDE but have just the k3b and required dependencies.
I also have breezy. Currently testing Dapper on spare partition.

Problem:
--------
I cannot rewrite any DVD+RW (Memorex 4x) using k3b. It always gives me this error in debug output:

```
growisofs
-----------------------
WARNING: /dev/hdc already carries isofs!
About to execute 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: restarting DVD+RW format...
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

```

However, I could write onto a fresh blank DVD+RW.
Even strange thing is that I can rewrite on DVD+RWs from breezy
In fact I burnt the Dapper iso from breezy.

I also tried running k3b as root. 
I am sure we don't need ide-scsci emulation as in Breezy k3b works without it.

One thing:
When k3b is preparing write process, Gnome's automounter comes up with dialog saying

Choose Disc type
You have inserted a blank disc.
What would you like to do?
Ignore     Make DVD

Is there any known issue with k3b and Gnome automounter in dapper?
(Breezy had similar behaviour but it never created any problem for k3b)

Do I have to install KDE for k3b to work. (Breezy has KDE installed)

anybody any ideas on issue?

Thanks
-Kshitij

---

### Post by kshitij on 2006-04-07
Anybody any clues?

---

### Post by kshitij on 2006-04-07
Gnomebaker seems to work fine. But I would like to use k3b. The interface and features are way better in k3b

---

### Post by aum11 on 2006-04-07
I also cannot erase cd-RW with K3b, however it works fine with nautilus burner.

I am running with all of the latest updates for Dapper.

---

