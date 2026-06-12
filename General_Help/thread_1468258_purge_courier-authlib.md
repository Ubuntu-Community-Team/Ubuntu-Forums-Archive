---
title: "purge courier-authlib"
date: 2010-05-01
forum: General Help
---

### Post by bluethundr on 2010-05-01
I need to purge courier-authdaemon so I can rebuild it from source so I can work around an incompatibility in an old packaged version. but when I try to do that I get this error:


```

 * ERR: /usr/lib/courier-imap/bin/couriertls missing
invoke-rc.d: initscript courier-pop-ssl, action "start" failed.
dpkg: error processing courier-pop-ssl (--configure):
 subprocess post-installation script returned error exit status 1
 * ERR: /usr/lib/courier-imap/bin/couriertls missing
invoke-rc.d: initscript courier-imap-ssl, action "start" failed.
dpkg: error processing courier-imap-ssl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-pop-ssl
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
 * ERR: /usr/lib/courier-imap/bin/couriertls missing
invoke-rc.d: initscript courier-pop-ssl, action "start" failed.
dpkg: error processing courier-pop-ssl (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-pop-ssl

```

any help would be appreiated

---

