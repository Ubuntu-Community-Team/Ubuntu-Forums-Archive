---
title: "Please Help me someone in this package manager problem"
date: 2012-06-16
forum: General Help
---

### Post by prismctg on 2012-06-16
When i try to install or remove any package is gives me this output ```
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So the problem is bandwidthd ; i try to remove bandwidthd package ; i m fail to do that;how can i solve this ?

---

### Post by Shadius on 2012-06-16
It says you should reinstall it before removing it, have you tried reinstalling it?

---

### Post by sandyd on 2012-06-16
> **prismctg said:**
> When i try to install or remove any package is gives me this output ```
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So the problem is bandwidthd ; i try to remove bandwidthd package ; i m fail to do that;how can i solve this ?

Typical postrm script problem. Neutralize the postrm script before removing the package.

Perhaps, something like
```

sudo mv /var/lib/dpkg/info/bandwidthd.prerm /opt/bandwidthd.prerm
sudo dpkg-reconfigure bandwidthd --force
sudo dpkg --purge --force-all bandwidthd

```

---

### Post by prismctg on 2012-06-16
> **Shadius said:**
> It says you should reinstall it before removing it, have you tried reinstalling it?
yea i tried this also; but same problem

---

### Post by prismctg on 2012-06-16
> **sandyd said:**
> Typical postrm script problem. Neutralize the postrm script before removing the package.

Perhaps, something like
```

sudo mv /var/lib/dpkg/info/bandwidthd.prerm /opt/bandwidthd.prerm
sudo dpkg-reconfigure bandwidthd --force
sudo dpkg --purge --force-all bandwidthd

```


now it gives me this :  ```
sudo dpkg-reconfigure bandwidthd --force
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: /etc/init.d/bandwidthd: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
```

---

### Post by prismctg on 2012-06-16
thank you every one ; i solve this  :)

---

