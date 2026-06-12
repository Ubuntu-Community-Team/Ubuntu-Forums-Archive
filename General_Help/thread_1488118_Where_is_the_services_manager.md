---
title: "Where is the services manager?"
date: 2010-05-19
forum: General Help
---

### Post by ZequeZ on 2010-05-19
Well, I'm using Ubuntu 10.04 and the services manager, to activate and desactivate the services is missing in System->Administration->Services...

So, where is it?

---

### Post by wilee-nilee on 2010-05-19
> **ZequeZ said:**
> Well, I'm using Ubuntu 10.04 and the services manager, to activate and desactivate the services is missing in System->Administration->Services...

So, where is it?

So what is it your trying to do and what does the services manager do?

---

### Post by wojox on 2010-05-19
Did you try Start up Applications? You can also install:

```
sudo apt-get install rcconf
```

Which is a utility for configuring which services get started up at boot-time.

---

### Post by ZequeZ on 2010-05-19
> **wojox said:**
> Did you try Start up Applications? You can also install:

```
sudo apt-get install rcconf
```Which is a utility for configuring which services get started up at boot-time.

Thanks, that works. But, why do they deleted the original service manager in the first place? o.o

---

### Post by CompyTheInsane on 2010-05-19
I've been wondering why it was removed as well, so I found two bug reports - one requesting removal of the services manager (services-admin), and the other for modifying the services manager so that it would support Upstart and eventually be brought back into Ubuntu
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701)
[https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/435935](https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/435935)

---

### Post by josephdietrich on 2010-05-20
Yeah, this is incredibly annoying since when, for example, your CUPS print spooler is not running for some reason and you use the "Printing troubleshooter,"  first screen in the wizard tells you "To correct this, choose System->Administration->Services from the main menu ..."

Grr.

---

