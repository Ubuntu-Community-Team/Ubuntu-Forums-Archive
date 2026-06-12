---
title: "Trouble with Oracle 11G installation"
date: 2011-02-18
forum: General Help
---

### Post by Mrich1976 on 2011-02-18
I'm having trouble installing Oracle 11G on Ubuntu 10.10. I've attached a screenshot. It's asking me for various packages, and basically telling me parameters aren't correct.

I thought all I needed to do was run the installer, but I guess not.

So if there's a good guide for installing Oracle 11G on Ubuntu 10.10 please let me know...

Screenshot attached.

---

### Post by Habitual on 2011-02-18
[OracleOnLinux]("http://www.puschitz.com/TuningLinuxForOracle.shtml")

It's NOT specific to Ubuntu, but VERY specific to Linux.
Do not dismiss this link just because it says "Oracle 9i and 10g Databases"

---

### Post by Mrich1976 on 2011-03-04
My setup:

Ubuntu 10.10

I tried your suggestion, and it didn't really help.

The problem I'm having is that when the Installer starts (using runInstaller), I can get to the Typical Installation screen, but I get a notification that there is an error with the Database File Location.

The error states: 

Database File Location:[INS-32012] Unable to create directory.

The problem is, the directory is there.

Under the directory permissions, the directory has the owner as oracle, and the group as oinstall (which I think is correct).

I can't continue past this screen.

I'm doing this through NX Client. I don't know if that matters.

Anyone, any advice on this would be extremely halpful.

I've even tried the instructions here:

[http://forums.oracle.com/forums/thread.jspa?threadID=1115155&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=1115155&tstart=0)

But with no luck.

Thanks in advance...

---

