---
title: "ATI drivers &amp; kernel update"
date: 2006-04-24
forum: General Help
---

### Post by buttari on 2006-04-24
Hi,
I installed the ATI drivers yesterday and everything was working fine. Today I had a kernel upgrade and ATI drivers are not working anymore.
I recompiled the module:
```

sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx

```

but still i get 
```

[drm] failed to load kernel module "fglrx"

```

in /var/log/Xorg.0.log
Help please!

Regards,
Alfredo Buttari

---

### Post by pitkali on 2006-04-24
I remember that you are supposed to remove the previous version of a driver with apt-get (or synaptic for that matter) before installing again. That doesn't seem to be necessary, if your 'uname -m' did change, but you could try.

Anyway, please post the actual error while attempt to load fglrx module (should be few lines before the one from Xorg.0.log, that you quoted).

---

### Post by buttari on 2006-04-24
[QUOTE=pitkali]I remember that you are supposed to remove the previous version of a driver with apt-get (or synaptic for that matter) before installing again. That doesn't seem to be necessary, if your 'uname -m' didn't change, but you could try.

Anyway, please post the actual error while attempt to load fglrx module (should be few lines before the one from Xorg.0.log, that you quoted).[/QUOTE]

It worked. Thank a lot.
BTW this issue should be better documented/explained in this howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Thanks again

Alfredo

---

