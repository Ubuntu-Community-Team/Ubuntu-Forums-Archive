---
title: "LDAP not working"
date: 2011-01-12
forum: General Help
---

### Post by ejames on 2011-01-12
I've been trying to get LDAP working on Ubuntu Server for users and groups. It works fine on redhat desktops but I just can't get it to work in Ubuntu.
I gave up trying to do it manually and used Webmin to do it. From within webmin I'm able to broswe the LDAP server so the setup seemd fine.
Whenever I try to ssh in i get the following in /var/log/auth.log....
[FONT=Courier New]
Jan 12 16:01:02 neutrino sshd[4263]: nss-ldap: do_open: do_start_tls failed:stat=-1
Jan 12 16:01:02 neutrino sshd[4263]: nss_ldap: reconnecting to LDAP server...
Jan 12 16:01:03 neutrino sshd[4263]: nss-ldap: do_open: do_start_tls failed:stat=-1
Jan 12 16:01:03 neutrino sshd[4263]: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan 12 16:01:04 neutrino sshd[4263]: nss-ldap: do_open: do_start_tls failed:stat=-1
Jan 12 16:01:04 neutrino sshd[4263]: nss_ldap: could not search LDAP server - Server is unavailable
Jan 12 16:01:04 neutrino sshd[4263]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 16:01:04 neutrino sshd[4263]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<blah>
Jan 12 16:01:04 neutrino sshd[4263]: pam_ldap: ldap_starttls_s: Can't contact LDAP server
Jan 12 16:01:05 neutrino sshd[4263]: Failed password for invalid user <blah> from <blah> port 34214 ssh2[/FONT]

It seems odd that I can search and find users without any problems using the webmin interface but get the above when I try to login.  Any ideas why do_start_tls would fail? Any fixes for this ?

Cheers,
Emyr

---

