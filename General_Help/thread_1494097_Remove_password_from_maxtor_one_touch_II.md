---
title: "Remove password from maxtor one touch II"
date: 2010-05-26
forum: General Help
---

### Post by lavinog on 2010-05-26
I have a Maxtor One Touch II external drive that was locked with a password using a utility that maxtor provided.  I have the password.  Does anyone know how to unlock the drive from ubuntu?

Worst case, I can find a XP machine, install the maxtor program, and remove the password.  I would prefer to not have to install anything though.

---

### Post by NT4usB on 2010-05-26
I'm assuming from your bean count, you know what you're doing...
What happens when you mount it? I don't know about hard drives and passwords... encryption or ?
Will the Maxtor ap run in wine?

ED: run XP in a VM?

---

### Post by lavinog on 2010-05-26
dmesg gave a bunch of errors like this:
```

May 25 13:29:33 rocksteady kernel: [  346.015112] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 25 13:29:33 rocksteady kernel: [  346.015121] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
May 25 13:29:33 rocksteady kernel: [  346.015126] sd 2:0:0:0: [sdb] <<vendor>> ASC=0xf0 ASCQ=0x1ASC=0xf0 ASCQ=0x1
May 25 13:29:33 rocksteady kernel: [  346.015134] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00

```
I couldn't find a driver on the maxtor (now seagate)website.  The one they had was for win98. (I wonder if it would have worked in wine)
I did find the cd though, and I tried it in wine...it installed, but it threw a bunch of errors when I tried to run it.
I eventually installed it on a winxp machine and it gave me an option to remove the password lock.  Afterwards the drive works in windows and ubuntu.

---

