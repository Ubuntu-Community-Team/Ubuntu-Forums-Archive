---
title: "Polkit authentication fails"
date: 2010-06-25
forum: General Help
---

### Post by bjorgein on 2010-06-25
For some reason, whenever I want to add users or change device drivers and the window pops up to authenticate with user credentials, it fails. I can install updates and change root files by entering my password but whenever i get the Authenticate window it fails. here is a snippet from my auth.log

polkit-agent-helper-1[6535]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=USER rhost=  user=USER

polkit-agent-helper-1[6535]: pam_ldap: error trying to bind as user "uid=USER,ou=people,dc=OMITTED,dc=com" (Invalid credentials)

polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.59 [users-admin] (owned by unix-user:USER)


Is there anywhere to update polkit to either properly use LDAP for credentials or change it back to use local accounts? I can't think anything on this online!!! :mad:

---

### Post by bjorgein on 2010-06-25
Anyone? This is driving me crazy

---

### Post by bjorgein on 2010-06-29
Still haven't figured this out. Anyone help? :confused::confused:

---

### Post by bjorgein on 2010-08-11
I still have this problem. Ill give someone a cookie for helping!

---

