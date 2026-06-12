---
title: "Installed newest 10.4 CCC for ATI card and now I have error"
date: 2010-04-28
forum: General Help
---

### Post by aeubz on 2010-04-28
Hi guys,

I installed the newest 10.4 catalyst control center from the ati website.  I had 10.3 installed before with fglrx and everything was working no problem.  But when I installed 10.4 and rebooted, my fan ran really loud.  I solved it before by installing fglrx.  So I tried to reinstall fglrx and now it produced a broken message and says "SystemError: installArchives() failed"  So I don't know what to do now..  Linux won't recognize my GPU again, so the fan still runs at max.

This is for Ubuntu 10.04 64 bit

---

### Post by aeubz on 2010-04-28
When trying to uninstall through synpatic package manager the package "fglrx" (its row is red) I get met with the error : "E: fglrx: subprocess installed post-removal script returned error exit status 2"

So I tried running ```
"sudo dpkg -P fglrx"
```

and I get the result:

```
(Reading database ... 304555 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
```

I really don't want to but is there a way to reinstall without losing all my programs?  Like creating a backup so once I reinstall tonight (new ubuntu release!!) I can just put all the programs back..  Without having to reinstall all the programs.

---

### Post by jaycee23 on 2010-04-29
Similar probs here - unable to reinstall 10.3 drivers!!!
Run aticonfig --initial and get error

---

### Post by jaycee23 on 2010-04-29
Managed to scramble back to ATI 10.3!!!!

---

### Post by aeubz on 2010-04-29
Ok then, guess I will do a fresh install

---

### Post by Torqumada286 on 2010-04-29
I've got the same error after upgrading to 10.4.  10.3 works?

Torqumada

---

### Post by Torqumada286 on 2010-04-29
After I installed the 10.3 drivers, it now says that I have no supported screen sections.

Torqumada

---

### Post by jaycee23 on 2010-04-30
I have both Lucid and Karmic on a triple boot with Win 7.

Karmic working fine with 10.3 ATI driver - tried to install 10.4 driver but kept getting errors. Will just leave it alone for now.

Lucid wouldn't work with 10.4 driver either BUT restricted driver from synaptic works perfectly - got my cube and wobbly windows back!

The 10.4 driver on the ATI website seems like a dud to me.

Would be keen to hear from anyone who has got it working on Karmic / Lucid

---

### Post by dino99 on 2010-04-30
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

