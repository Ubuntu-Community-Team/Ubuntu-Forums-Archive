---
title: "I want to create a link to a system service"
date: 2011-01-20
forum: General Help
---

### Post by MIH1406 on 2011-01-20
Hi,

I want to create a link to start apache2 service:
```
sudo /etc/init.d/apache2 start
```

I tried creating a launcher but it did not work at all

---

### Post by lithopsian on 2011-01-20
Do you want to start it every time you boot?  That would be done by creating a symlink in /etc/rc2.d:
```
ln -s ../etc/init.d/apache2
```

The start parameter will be supplied automatically when the script is called during boot.  These links are typically created when the service is installed although I haven't installed apache to know if this happens.

Often you will want to also add a link in rc0.d for shutdown and rc6.d for reboot.  In these cases the parameter stop will be supplied when the script is called.

---

### Post by lithopsian on 2011-01-20
Do you want to start it every time you boot?  That would be done by creating a symlink in /etc/rc2.d:
```
ln -s ../etc/init.d/apache2 S42apache2
```

The number you put in determines the order that scripts are run at startup.  The start parameter will be supplied automatically when the script is called during boot.  These links are typically created when the service is installed although I haven't installed apache to know if this happens.

Often you will want to also add a link in rc0.d for shutdown and rc6.d for reboot.  In these cases the parameter stop will be supplied when the script is called.

---

### Post by lithopsian on 2011-01-20
Do you want to start it every time you boot?  That would be done by creating a symlink in /etc/rc2.d:
```
ln -s ../etc/init.d/apache2 S42apache2
```

The number you put in determines the order that scripts are run at startup.  The start parameter will be supplied automatically when the script is called during boot.  These links are typically created when the service is installed although I haven't installed apache to know if this happens.

Often you will want to also add a link in rc0.d for shutdown and rc6.d for reboot.  In these cases the parameter stop will be supplied when the script is called.

---

