---
title: "libnss-ldap and schema  mapping  support"
date: 2011-12-26
forum: General Help
---

### Post by supremedalek on 2011-12-26
In [http://manpages.ubuntu.com/manpages/oneiric/man5/nss_ldap.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/nss_ldap.5.html) it is mentioned that some features require schema  mapping  support. Not knowing how to verify it, I tried to do something like

nss_override_attribute_value loginShell /usr/bin/tcsh

(tcsh is installed) but when I logged in my shell still matched what I had defined in ldap under loginShell. Is that to be expected or am I missing a step somewhere?

---

### Post by luvshines on 2012-01-04
> **supremedalek said:**
> In [http://manpages.ubuntu.com/manpages/oneiric/man5/nss_ldap.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/nss_ldap.5.html) it is mentioned that some features require schema  mapping  support. Not knowing how to verify it, I tried to do something like

nss_override_attribute_value loginShell /usr/bin/tcsh

(tcsh is installed) but when I logged in my shell still matched what I had defined in ldap under loginShell. Is that to be expected or am I missing a step somewhere?

This should work as expected, the shell should be one you are overriding with (tcsh)
Weird !! Which file did you put this config in ?

---

