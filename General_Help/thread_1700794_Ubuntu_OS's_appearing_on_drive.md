---
title: "Ubuntu OS's appearing on drive"
date: 2011-03-05
forum: General Help
---

### Post by sp176 on 2011-03-05
I have a dual-booting operating system with Ubuntu 10.04 and Windows 7.  I have had this for a year, and during my choice on startup of which to pick I have developed this:

Ubuntu, with Linux 2.6.32-29-Generic
Ubuntu, with Linux 2.6.32-29-Generic (recovery mode)
Ubuntu, with Linux 2.6.32-29-Generic
Ubuntu, with Linux 2.6.32-29-Generic (recovery mode)
Ubuntu, with Linux 2.6.32-29-Generic
Ubuntu, with Linux 2.6.32-29-Generic (recovery mode)
Ubuntu, with Linux 2.6.32-29-Generic
Ubuntu, with Linux 2.6.32-29-Generic (recovery mode)
Windows 

It appears as if I am gathering extra Ubuntu OS's.  Can I get rid of these?

---

### Post by dabl on 2011-03-05
If you copied those kernel versions correctly, then you have some kind of corruption in your Grub boot menu.  They should not be identical -- the top version should be the newest, and the ones below it should be earlier versions.  Your list shows all of them being the same kernel version.

That being said, you can open synaptic with root privileges and browse down to the linux-kernel-xxx files, and delete _older/earlier_ kernel versions.  Be very careful not to delete the version of your current running kernel, which you can ascertain by running

```
uname -a
```

in a terminal window.

---

### Post by sp176 on 2011-03-05
You are correct.  I simply copied and pasted the first line.  
Thanks

---

