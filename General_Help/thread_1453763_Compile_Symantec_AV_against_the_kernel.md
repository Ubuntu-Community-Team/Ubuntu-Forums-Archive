---
title: "Compile Symantec AV against the kernel?"
date: 2010-04-13
forum: General Help
---

### Post by jdysinger on 2010-04-13
Has anyone successfully compiled Symantec AV Autoprotect against the current Ubuntu Kernel? 

I am using the kernel 2.6.24-27-generic. I'm following these instructions for Symantec Autoprotect:[ http://service1.symantec.com/SUPPORT/ent-security.nsf/docid/2009081214270148]("http://service1.symantec.com/SUPPORT/ent-security.nsf/docid/2009081214270148")

and when I run the "build.sh" I receive the error message: 
> make -C /lib/modules/2.6.24-27-generic/build M=/home/infosec/SAV 1.0.9 Linux/CDLayout/sav-linux-1.0.9-13/ap-kernelmodule-1.0.9-13/symev MODVERDIR=/home/infosec/SAV 1.0.9 Linux/CDLayout/sav-linux-1.0.9-13/ap-kernelmodule-1.0.9-13/symev/../symev/.tmp_versions-custom-2.6.24-27-generic-i686 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-27-generic'
make[1]: *** No rule to make target `1.0.9'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-27-generic'
make: *** [custom] Error 2
~/SAV 1.0.9 Linux/CDLayout/sav-linux-1.0.9-13/ap-kernelmodule-1.0.9-13

Build was stopped due to error.Is there another option or really what am I doing wrong? 

Thanks!

---

### Post by J V on 2010-04-13
Yes you are doing something wrong: Trying to mess with the kernel, trying to install antivirus, trying to install software from a company that makes money off of viruses etc...

Google linux antivirus to get the idea...

---

### Post by jdysinger on 2010-04-14
> **J V said:**
> Yes you are doing something wrong: Trying to mess with the kernel, trying to install antivirus, trying to install software from a company that makes money off of viruses etc...

Google linux antivirus to get the idea...

My information security officer didn't like that answer. I am still required to install the business-approved AV (I did try to get away with ClamAV, but to no avail)

---

