---
title: "Way to see all listed kernels installed?"
date: 2010-03-09
forum: General Help
---

### Post by sports fan Matt on 2010-03-09
Is there a way to see not just the most recent, but ALL kernels you have installed in Ubuntu?  I know there is a way through Symnaptic but is there any other way?  I keep thinking there is.

---

### Post by MasterNetra on 2010-03-09
Well the Grub Menu lists I think all your previous Kernel Installs until you clear them from the menu. Idk if Grub2 continues this or just keeps a two kernel list. Your current and your previous.

---

### Post by sports fan Matt on 2010-03-09
I thought for some strange reason you could access this through commands in the terminal.  I knew about grub.menu list as well, but unsure as you are if grub 2 continues this.

---

### Post by MasterNetra on 2010-03-09
> **sox fan Matt said:**
> I thought for some strange reason you could access this through commands in the terminal.  I knew about grub.menu list as well, but unsure as you are if grub 2 continues this.

Grub2 uses a different file to store it. 

See here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by RedSquirrel on 2010-03-09
I would start with:

```
dpkg -l linux-image*
```

---

### Post by sports fan Matt on 2010-03-09
There we go: | Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
un  linux-image-2. <none>         (no description available)
ii  linux-image-2. 2.6.32-16.25   Linux kernel image for version 2.6.32 on i38
un  linux-image-2. <none>         (no description available)
ii  linux-image-38 2.6.32.16.17   Generic Linux kernel image
un  linux-image-ge <none>         (no description available)

I have what appears to be .25 and .17.

---

### Post by bodhi.zazen on 2010-03-10
I always simply :

```
ls /boot | grep vmlinuz
```

---

