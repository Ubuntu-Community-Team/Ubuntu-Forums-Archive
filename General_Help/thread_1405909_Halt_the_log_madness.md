---
title: "Halt the log madness"
date: 2010-02-13
forum: General Help
---

### Post by SpinningAround on 2010-02-13
I have a feeling that there is something wrong with my logs, problem is that I don't know how to fix it. The logs are basically filled with line after line with this message or something almost identical in very short sequences of about 10 very second.


```

desktop pptp[2147]: nm-pptp-service-2140 log[decaps_gre:pptp_gre.c:414]: buffering packet 970710 (expecting 970640, lost or reordered)
desktop pptp[2147]: nm-pptp-service-2140 log[decaps_gre:pptp_gre.c:414]: buffering packet 970711 (expecting 970640, lost or reordered)

```

```

ls -lahS /var/log/
totalt 2,0G
-rw-r-----  1 syslog            adm  1,1G 2010-02-13 14:12 daemon.log
-rw-r-----  1 syslog            adm  749M 2010-02-13 10:45 syslog.1
-rw-r-----  1 syslog            adm   95M 2010-02-13 14:12 syslog
-rw-r-----  1 syslog            adm   29M 2010-02-09 09:41 daemon.log.1
-rw-r-----  1 syslog            adm  1,2M 2010-02-09 09:35 kern.log.1
-rw-r-----  1 syslog            adm  970K 2010-02-09 09:45 messages.1
-rw-r-----  1 syslog            adm  586K 2010-02-13 14:08 kern.log

```

---

### Post by iponeverything on 2010-02-13
I think that its an MTU problem. Should be easy for you to address.

See:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/292799](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/292799)

---

