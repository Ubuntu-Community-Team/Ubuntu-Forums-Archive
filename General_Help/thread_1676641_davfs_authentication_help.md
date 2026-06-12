---
title: "davfs authentication help"
date: 2011-01-27
forum: General Help
---

### Post by domzz on 2011-01-27
When I run:

> mount -t davfs [http://xxxx/webdav](http://xxxx/webdav) /home/USER1

I get:

> Please enter the username to authenticate with server
[http://xxxx/webdav](http://xxxx/webdav) or hit enter for none.
  Username: USER1
Please enter the password to authenticate user USER1 with server
[http://xxxx/webdav](http://xxxx/webdav) or hit enter for none.
  Password:
/sbin/mount.davfs: Mounting failed.
Could not authenticate to server: rejected Digest challenge

I know the password/username are correct because I tried to use another user.

I can connect to [http://xxxx/webdav](http://xxxx/webdav) with that User/pass just fine.

My apache2.conf:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
 
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
 
        ErrorLog /var/log/apache2/error.log
 
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
 
        CustomLog /var/log/apache2/access.log combined
 
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
 
    <Location />
        AuthType Digest
        AuthName "gods"
        AuthDigestDomain /var/www/ http://xxxx
 
        AuthDigestProvider file
        AuthUserFile /etc/apache2/passwords
        Require valid-user
        SetEnv R_ENV "/var/www"
    </Location>

 
</VirtualHost>
 
<VirtualHost *:443>
        ServerAdmin webmaster@localhost
 
        SSLEngine on
        SSLCertificateFile /etc/apache2/apache.pem
 
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
 
        ErrorLog /var/log/apache2/error.log
 
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
 
        CustomLog /var/log/apache2/access.log combined
 
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
    <Location />
        AuthType Digest
        AuthName "gods"
        AuthDigestDomain /var/www/ http://xxxx
 
        AuthDigestProvider file
        AuthUserFile /etc/apache2/passwords
        Require valid-user
        SetEnv R_ENV "/var/www"
     </Location>
</VirtualHost>


```

```
#apache2ctl -M
[Thu Jan 27 19:10:22 2011] [warn] _default_ VirtualHost overlap on port 443, the first has precedence
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 scgi_module (shared)
 setenvif_module (shared)
 ssl_module (shared)
 status_module (shared)
Syntax OK
```

---

### Post by domzz on 2011-01-27
bump

---

### Post by domzz on 2011-01-28
bump

---

