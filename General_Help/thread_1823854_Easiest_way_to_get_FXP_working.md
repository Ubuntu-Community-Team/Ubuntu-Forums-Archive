---
title: "Easiest way to get FXP working?"
date: 2011-08-12
forum: General Help
---

### Post by Phixion on 2011-08-12
I have 2 servers that I'd like to set up FXP on, I'm running ProFTPD on both but have been unable to get it working so far.

I've googled, found results, tried em, failed repeatedly.

I tried adding

<Global>
AllowForeignAddress on
</Global>

to proftpd.conf, restarted the daemon... still no go.

Any help appreciated.

---

### Post by psusi on 2011-08-12
FXP is a windows program.  You will need WINE to run it.

---

### Post by Phixion on 2011-08-12
You've misunderstood me, I want FXP ability on my 2 remote servers, they are both running Ubuntu server with ProFTPD... it is possible to enable it on them so that I can transfer files between them using FlashFXP (on my Windows machine).

---

