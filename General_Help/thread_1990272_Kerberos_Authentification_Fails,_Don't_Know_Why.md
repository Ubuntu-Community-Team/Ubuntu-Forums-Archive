---
title: "Kerberos Authentification Fails, Don't Know Why"
date: 2012-05-29
forum: General Help
---

### Post by OpEn_SoUrCe_RoCkS on 2012-05-29
I'm running Ubuntu 11.10, using ```
mod_auth_kerb
``` from the package ```
libapache2-mod-auth-kerb
```.

When trying to access a page using SSO, i get errors. The killer is that it worked last week, and I don't remember changing anything that had to do with Kerberos. :-k

Here is the output in Apache's error.log when I try to view a page: 


```
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Tue May 29 14:04:39 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 478 to 322 : URL /
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1240): [client 172.16.0.139] Acquiring creds for HTTP@srv-monitor
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1385): [client 172.16.0.139] Verifying client data using KRB5 GSS-API
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1401): [client 172.16.0.139] Client didn't delegate us their credential
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1420): [client 172.16.0.139] GSS-API token of length 134 bytes will be sent back
[Tue May 29 14:04:39 2012] [debug] src/mod_auth_kerb.c(1101): [client 172.16.0.139] GSS-API major_status:000d0000, minor_status:000186a4
[Tue May 29 14:04:39 2012] [error] [client 172.16.0.139] gss_accept_sec_context() failed: Unspecified GSS failure.  Minor code may provide more information (, )
[Tue May 29 14:04:39 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 478 to 322 : URL /
```

I loosely followed the guide found [here]("http://acksyn.org/diary/?p=460").

The relevant part of my "000-default" configuration is the following:

```
 ServerAdmin webmaster@localhost
        DocumentRoot /usr/local/nagios/share/vshell/
        <Directory />
                Options  Indexes FollowSymLinks MultiViews
                Order allow,deny
                AllowOverride All
                Allow from all
                AuthName "Nagios Authentification"
                AuthType Kerberos
                KrbMethodNegotiate On
                KrbMethodK5Passwd On
                KrbAuthRealms COMPANY.COM
                Krb5KeyTab /etc/krb5.keytab
                require valid-user
        </Directory>

```

Can anybody PLEASE help me. I'm going nuts.

---

### Post by marksnelling on 2012-06-14
I'm also getting this error on 12.04. I have a 11.10 box that I'm sure is configured the same way that works perfectly. :mad:

---

### Post by OpEn_SoUrCe_RoCkS on 2012-06-14
I used an alternate route.

Add this to the bottom of your apache2.conf:

```
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule auth_pam_module modules/mod_auth_pam.so
```

Add this to your 000-default file:

 ```
AuthName "Nagios Authentification"

        NTLMAuth on
        NTLMAuthHelper "/usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp"
        NTLMBasicAuthoritative on
        AuthType NTLM

        require user DOMAIN\user1
        require user DOMAIN\user2
        require user DOMAIN\user3
        require user DOMAIN\userX
```

This works like a charm!!

---

