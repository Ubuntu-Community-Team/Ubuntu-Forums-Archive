---
title: "login takes very long if connected to a network but ldap-server is not reachable"
date: 2011-01-24
forum: General Help
---

### Post by klamu on 2011-01-24
Hello all 

I'm having the following situation: 

we have an internal LDAP-server in our company.
we use PAM-authentication on our Ubuntu -setups  (ubuntu 10.04)

everything is running fine as long as I'm connected to our internal network (ldap-server is reachable) or if I do not have any network-connections at all. (login succeeds in seconds)

once I try to login to my ubuntu-workstation while I'm connected to my home-network (ldap-server not reachable) it takes more then 1 minute to log me in. (with  cashed credentials) 

same happens when ubuntu is resuming form hibernate when on home-network .

I think - i searched all config-files for this timeout, but could not find anything .

my nsswitch.conf:

[FONT=Courier New]passwd:         files ldap [NOTFOUND=return] db
group:          files ldap [NOTFOUND=return] db
shadow:         files ldap
sudoers:        files ldap

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis[/FONT]

 
my /etc/pam.d/common-auth

[FONT=Courier New]
auth        required      pam_env.so
auth        optional      pam_mount.so
auth        [success=done default=ignore]    pam_unix.so nullok_secure try_first_pass
auth        requisite     pam_succeed_if.so uid >= 500 quiet
auth    [success=3 default=ignore]    pam_krb5.so minimum_uid=1000 use_first_pass
auth    [success=2 default=ignore]      pam_krb5.so realm=mydomain.b use_first_pass
auth    [success=1 default=ignore]      pam_krb5.so realm=mydomain.a use_first_pass
auth        [default=done]    pam_ccreds.so action=validate use_first_pass
auth        [default=done]    pam_ccreds.so action=store
auth        [default=bad]    pam_ccreds.so action=update
auth        required      pam_deny.so[/FONT]


any one having the same issue, and found a solution ?

thanks

---

