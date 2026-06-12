---
title: "how to stop rc.local from running"
date: 2011-01-19
forum: General Help
---

### Post by johnnash on 2011-01-19
I put something that crashes the system in rc.local. How do I stop it from running and edit it?

---

### Post by lithopsian on 2011-01-19
If you boot to the command line session you probably won't execute rc.local.  Depends on your setup though.  It gets executed any time there is a symlink in the rcn.d directory for runlevel n that you are entering.  I don't have a link in rc1.d but then I've changed all sorts of stuff.

Can also use the infamous Live CD and fix it without booting the broken system.

---

### Post by lithopsian on 2011-01-19
If you boot to the command line session you probably won't execute rc.local.  Depends on your setup though.  It gets executed any time there is a symlink in the rcn.d directory for runlevel n that you are entering.  I don't have a link in rc1.d but then I've changed all sorts of stuff.

Can also use the infamous Live CD and fix it without booting the broken system.

---

### Post by matt_symes on 2011-01-19
Hi

```
sudo chmod -x /etc/rc.local
```

Make it non executable.

Kind regards

---

### Post by uyulala on 2011-01-19
Hi,

have you tried to boot in single user mode? I think the "recovery" options on yhe boot menu is single user mode. Otherwise you can choose edit in grub and add the word "single" to the end of the boot command.

Or, you could boot from a live cd, and edit the rc.local from there?

Hope this is to some help!

---

### Post by matt_symes on 2011-01-19
Hi

```
sudo chmod -x /etc/rc.local
```

Make it non executable.

Kind regards

---

