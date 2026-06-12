---
title: "php5 + ldap ??"
date: 2011-02-23
forum: General Help
---

### Post by djmohr on 2011-02-23
Hey all

first time here so I apologize if this has been posted before.

I have 8.04 desktop running as a Guest OS on 2008 R2 Hyper-V; this VM is suppose to run Open-Audit so we can keep track of all software licenses and hardware.
I have installed and configured all i need to do to get Open-Audit up and running but i can't get ldap working. I've installed the php5-ldap package and restarted apache2, also restarted the VM. Now for Open_audit to use ldap I have been instructed to edit the php.ini file and make sure that extension=php_ldap.dll is uncommented in php.ini but I can find no reference to ldap in this file.

What am I missing?

---

### Post by djmohr on 2011-02-23
No worries, got it sorted out, just added the extension to the end of the file.

---

### Post by Monotoko on 2011-02-23
Are you sure? Linux does not use dll files, instead it uses .so for future ref. 

Daniel

---

