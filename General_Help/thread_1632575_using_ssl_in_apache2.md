---
title: "using ssl in apache2"
date: 2010-11-28
forum: General Help
---

### Post by oren tal on 2010-11-28
I am running apache2 in my local network and I am learning  about the ssl.
I found this [document]("http://www.debian-administration.org/articles/349").
It tell me to run the following command (down) in order to generate SSL certificate:
apache2-ssl-certificate

However when I run the command I get the message that there is no such command.
I have installed apache2, but maybe I need to install other package.

---

### Post by iNsOmNiOuS on 2010-11-28
Openssl is required to have SSL with Apache, along with it's plugin for apache2.

Just do 

sudo apt-get install openssl <-- Install OpenSSL
a2enmod openssl <-- Activate Plugin

---

### Post by oren tal on 2010-11-28
> **iNsOmNiOuS said:**
> Openssl is required to have SSL with Apache, along with it's plugin for apache2.

Just do 

sudo apt-get install openssl <-- Install OpenSSL
a2enmod openssl <-- Activate Plugin

well the first command worked for me, the second however gave me the following message:
ERROR: Module openssl does not exist!

the first gave me:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  openssl-doc
The following packages will be upgraded:
  openssl
1 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 400kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) lucid-updates/main openssl 0.9.8k-7ubuntu8.4 [400kB]
Fetched 400kB in 1s (300kB/s)  
(Reading database ... 151813 files and directories currently installed.)
Preparing to replace openssl 0.9.8k-7ubuntu8 (using .../openssl_0.9.8k-7ubuntu8.4_i386.deb) ...
Unpacking replacement openssl ...
Processing triggers for man-db ...
Setting up openssl (0.9.8k-7ubuntu8.4) ...


---

### Post by iNsOmNiOuS on 2010-11-28
Try and do :

a2enmod ssl

---

### Post by oren tal on 2010-11-28
> **iNsOmNiOuS said:**
> Try and do :

a2enmod ssl

I did: sudo a2enmod ssl 
And I got:
> Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http proxy_scgi reqtimeout rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?
I typed: y 
And I got:
ERROR: Module y does not exist!

I really don't know what models it does talking about.

---

### Post by iNsOmNiOuS on 2010-11-28
I get this output on that command

# a2enmod
Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?

As you can see I have ssl in there.

Have a look at this tutorial : [http://www.modssl.org/example/](http://www.modssl.org/example/)

---

### Post by oren tal on 2010-11-28
> **iNsOmNiOuS said:**
> I get this output on that command

# a2enmod
Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?

As you can see I have ssl in there.

Have a look at this tutorial : [http://www.modssl.org/example/](http://www.modssl.org/example/)

I installed the ssl model, however when I try to run the command:
apache2-ssl-certificate
I still get the message:
apache2-ssl-certificate: command not found

---

