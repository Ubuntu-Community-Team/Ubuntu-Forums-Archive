---
title: "Kerberos SSO with Apache - Partly works"
date: 2012-02-10
forum: General Help
---

### Post by OpEn_SoUrCe_RoCkS on 2012-02-10
Ok...

I've got my Apache server running, and I have Kerberos configured to integrate with our primary domain controller (Windows 2003).

When I try to access my page, however, I get a login prompt... Which I shouldn't, since this is supposed to be a SSO...

When I manually enter my credentials, it works and takes me to the page. However, I'd like this to use Integrated Windows Authentication.

I had this working at one point, but it doesn't work anymore... :S

Here are my config files.

*/etc/apache/apache2.conf*

```
LockFile ${APACHE_LOCK_DIR}/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 5


<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType text/plain
HostnameLookups Off
ErrorLog ${APACHE_LOG_DIR}/error.log
LogLevel warn
Include mods-enabled/*.load
Include mods-enabled/*.conf
Include httpd.conf
Include ports.conf
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
Include conf.d/
Include sites-enabled/
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule auth_kerb_module modules/mod_auth_kerb.so
LoadModule auth_pam_module modules/mod_auth_pam.so
```


*/etc/apache2/sites-enabled/000-default*

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /usr/local/nagios/share/vshell
        <Directory />
                Options FollowSymLinks
                AllowOverride None


AuthType Kerberos
AuthName "Kerberos Auth"
KrbVerifyKDC off
KrbMethodNegotiate On
KrbMethodK5Passwd On
KrbAuthRealms COMPANY.COM
Krb5KeyTab /etc/krb5.keytab
KrbSaveCredentials on
require valid-user

        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/local/nagios/sbin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```


*/etc/krb5.conf*

```
[libdefaults]
 default_realm = COMPANY.COM
 default_tgs_enctypes = aes256-cts aes128-cts arcfour-hmac-md5 des-cbc-md5 des-cbc-crc
 default_tkt_enctypes = aes256-cts aes128-cts arcfour-hmac-md5 des-cbc-md5 des-cbc-crc
 permitted_enctypes = aes256-cts aes128-cts arcfour-hmac-md5 des-cbc-md5 des-cbc-crc
default_keytab_name = FILE:/etc/krb5.keytab
 dns_lookup_realm = true
 dns_lookup_kdc = true
 passwd_check_s_address = false
udp_preference_limit = 1
 ccache_type = 3
 kdc_timesync = 0
[domain_realm]
 pdc-2.company2.com = COMPANY2.COM
 .company.com = COMPANY.COM
 pdc-1.company.com = COMPANY.COM
 company.com = COMPANY.COM
 sdc-1.company.com = COMPANY.COM
 srv-monitor.company.com = COMPANY.COM
[realms]
COMPANY2.COM = {
 kdc = pdc-2.company2.com:88
 master_kdc = pdc-2.company2.com:88
 kpasswd = pdc-2.company2.com:464
 kpasswd_server = pdc-2.company2.com:464
}
COMPANY.COM = {
 kdc = pdc-1.company.com:88
 master_kdc = pdc-1.company.com:88
 kpasswd = pdc-1.company.com:464
 kpasswd_server = pdc-1.company.com:464
 kdc = sdc-1.company.com:88
 master_kdc = sdc-1.company.com:88
 kpasswd = sdc-1.company.com:464
 kpasswd_server = sdc-1.company.com:464
}
```

*Output of ktutil, rkt /etc/krb5.keytab, l*

```
slot KVNO Principal
---- ---- ---------------------------------------------------------------------
ktutil:  rkt /etc/krb5.keytab
ktutil:  l
slot KVNO Principal
---- ---- ---------------------------------------------------------------------
   1    3 HTTP/srv-monitor.company.com@COMPANY.COM
   2    3 HTTP/srv-monitor.company.com@COMPANY.COM
   3    3 HTTP/srv-monitor.company.com@COMPANY.COM
   4    3             HTTP/srv-monitor@COMPANY.COM
   5    3             HTTP/srv-monitor@COMPANY.COM
   6    3             HTTP/srv-monitor@COMPANY.COM
```

WHAT AM I MISSING!!! I'm this close to getting it, I can feel it! All I need is to make to login prompt disappear, and for the credentials to be passed automatically.

Thank very much for your time. (:

---

