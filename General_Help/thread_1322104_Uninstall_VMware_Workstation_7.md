---
title: "Uninstall VMware Workstation 7"
date: 2009-11-10
forum: General Help
---

### Post by afroman10496 on 2009-11-10
How can I do that?

---

### Post by alphaniner on 2009-11-10
Look in /usr/bin for vmware executables.  This is what it looks like for VMware server:

```
$ ls /usr/bin |grep -i vm
/usr/bin/vmnet-bridge   /usr/bin/vmware-config.pl
/usr/bin/vmnet-dhcpd    /usr/bin/vmware-mount
/usr/bin/vmnet-natd     /usr/bin/vmware-ping
/usr/bin/vmnet-netifup  **[COLOR="Red"]/usr/bin/vmware-uninstall.pl[/COLOR]**
/usr/bin/vmnet-sniffer  /usr/bin/vmware-uninstall-vix.pl
/usr/bin/vmrun          /usr/bin/vmware-vdiskmanager
/usr/bin/vmstat         /usr/bin/vmware-vim-cmd
/usr/bin/vm-support     /usr/bin/vmware-vimsh
/usr/bin/vmware         /usr/bin/vmware-watchdog
$ 

```

If that doesn't return anything useful, try

```
sudo find / -iname vmware 2> /dev/null
```

---

### Post by afroman10496 on 2009-11-10
Thanks for the quick response.
Just for everyone else, here is what I did:
```
sudo sh /usr/bin/vmware-installer --uninstall-product=vmware-workstation
```

---

### Post by Gi0tis on 2009-12-17
> **Afroman10496 said:**
> Thanks for the quick response.
Just for everyone else, here is what I did:
```
sudo sh /usr/bin/vmware-installer --uninstall-product=vmware-workstation
```
Thanx for that,worked like a charm.

---

### Post by FernandoEscher on 2010-09-24
> **afroman10496 said:**
> Thanks for the quick response.
Just for everyone else, here is what I did:
```
sudo sh /usr/bin/vmware-installer --uninstall-product=vmware-workstation
```

Thanks! That worked. :)

---

