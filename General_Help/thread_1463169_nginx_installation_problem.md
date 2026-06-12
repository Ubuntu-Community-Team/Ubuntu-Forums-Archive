---
title: "nginx installation problem"
date: 2010-04-26
forum: General Help
---

### Post by DBA on 2010-04-26
When I attempt to install the latest nginx release with the following commands:
```

sudo apt-get install libpcre3 libpcre3-dev libssl0.9.8 libssl-dev openssl libopenssl-ruby
./configure --sbin-path=/usr/local/sbin --with-http_ssl_module
sudo make
sudo checkinstall

```

The checkinstall command gives me the following error:

```

========================= Installation results ===========================
/usr/bin/installwatch: /var/tmp/tmp.yP1C62rRXs/installscript.sh: /bin/sh: bad interpreter: Permission denied

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

This used to work great on my ubuntu 9.04 server @ webbynode. I've just rented a 9.10 server @ mediatemple and I seem to be getting this permissions issue.

Could someone point me on the right direction? I've tried issuing these commands as root but got the same result :/

Best regards,
DBA

---

### Post by DBA on 2010-04-27
I've restored the VM from MediaTemple's backups but the issue remains. Anyone has any suggestions?

Thanks.

---

