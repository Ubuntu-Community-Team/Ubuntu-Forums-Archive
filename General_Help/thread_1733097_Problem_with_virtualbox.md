---
title: "Problem with virtualbox"
date: 2011-04-18
forum: General Help
---

### Post by stakhouse on 2011-04-18
Hello,
I have a Dell Studio 14z, BIOS version A04 and my processor is a Intel P8600 witch support VT-X. I have both Ubuntu 10.10 and Windows 7 64bit on dualboot.

My problem is that when i try to guest Windows 7 64bit on Ubuntu 10.10 64bit as host with virtualbox, it tells me that my processor doesn't support 64bit. My vt-x is enable in the bios.

But when i try to guest Windows 7 on Windows 7 as host, everything works fine.

The problem might come from linux. Any idea?
Thanks

---

### Post by lmarmisa on 2011-04-18
Did you install Ubuntu 10.10 32 or 64 bits?.

---

### Post by stakhouse on 2011-04-18
Ubuntu 64bit

---

### Post by lmarmisa on 2011-04-18
You can verify your Ubuntu version typing the command:

```

luis@JAVEAUB1010:~$ uname -a
Linux JAVEAUB1010 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux
luis@JAVEAUB1010:~$ 


```This version is 64 bits (x86_64).

Maybe you downloaded the VirtualBox 32 bits version from Oracle. This could explain your problem:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by stakhouse on 2011-04-18
```
alex@alex-Studio-1440:~$ uname -a
Linux alex-Studio-1440 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
alex@alex-Studio-1440:~$ 

```

Does this mean my ubuntu isn't 64bit ?
I thought it was.

---

### Post by lmarmisa on 2011-04-18
No. Your version is 32 bit. 

Try to re-install Ubuntu using the file ubuntu-10.10-desktop-amd64.iso.

Best regards,

Luis

P. S. If your Ubuntu version supports PAE, I am not sure if that version would be able to run VirtualBox 64 bits.

---

### Post by stakhouse on 2011-04-18
Thanks a lot I will try that!

---

