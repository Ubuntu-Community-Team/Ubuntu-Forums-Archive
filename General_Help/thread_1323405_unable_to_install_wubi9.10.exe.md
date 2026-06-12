---
title: "unable to install wubi9.10.exe"
date: 2009-11-11
forum: General Help
---

### Post by Naughtyboynag on 2009-11-11
i've downloaded both wubi9.10.exe and ubantu9.10 32 bit ISO and saved it in same partation(NTFS). when i launch wubi9.10.exe with out any progress it throws an error like - "application has corrupted, reinstalling the application may fix the problem". downloaded wubi9.10.exe several times but of no use. has 5GB free disk space and 512 MB RAM. AMD atlon 2g hz CPU.
eagerly waiting to try Wubi.
any idea what could be the cause?
 
Thanks,
~Nags

---

### Post by FornhamFred on 2009-11-19
Sorry I do not understand why you downloaded both wubi and 9.10. The iso in 9.10 has wubi included, and if you have downloaded the iso simply burn it to a CD as an image ( burn as slowly as possible ) and then run the CD in windows, If it does not autostart then look at the disc and you will see wubi.exe. Running wubi allows you to either install it or run as a live cd.:popcorn::popcorn:

---

### Post by Naughtyboynag on 2009-12-04
Hey FornhamFred,
i think u'r not aware of the use of WUBI. as per my understanding with the help of WUBI we can Ubantu from windows as an windows application and we can uninstall it from add/rem prog.
just excited try this  but unable to run WUBI9.10.exe.
 
any other suggestions?
 
~Nags

---

### Post by 3rdalbum on 2009-12-04
> **Naughtyboynag said:**
> Hey FornhamFred,
i think u'r not aware of the use of WUBI. as per my understanding with the help of WUBI we can Ubantu from windows as an windows application and we can uninstall it from add/rem prog.

I think FornhamFred probably has a better idea of it than you do. You can install Ubuntu from within this Windows program. It still runs **directly on the hardware** as a dual-boot system.

There are limitations to Wubi - it uses the Windows filesystem, so if Windows won't successfully boot/shut down, then Ubuntu won't be able to boot either. (this happened to a friend of mine). You are also limited to 30 gigabytes of space for Ubuntu which is not a lot if you work with media files.

I'd recommend doing a proper dual-boot of Ubuntu by booting up from the disc.

If you really want to give Wubi another shot, burn the ISO to a CD, insert the CD while Windows is running, and then run the Wubi program **from the CD**.

---

