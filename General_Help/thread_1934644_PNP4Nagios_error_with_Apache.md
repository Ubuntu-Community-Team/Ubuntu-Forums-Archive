---
title: "PNP4Nagios error with Apache"
date: 2012-03-02
forum: General Help
---

### Post by OpEn_SoUrCe_RoCkS on 2012-03-02
Hey,

I had a working setup with PNP4Nagios and Nagios. Everything was great.

Today,  I installed NagiosQL.

Since then, PNP4Nagios's web UI doesn't work anymore!

I get this error when trying to access it:

```
The requested URL /pnp4nagios/index.php/graph was not found on this server.
```

Here is the relevant output of *error.log*:

```
[Fri Mar 02 15:06:43 2012] [error] [client 172.16.0.139] File does not exist: /usr/local/pnp4nagios/share/index.php/graph

```

*/etc/apache2/conf.d/pnp4nagios.conf*

```
Alias /pnp4nagios "/usr/local/pnp4nagios/share"

<Directory "/usr/local/pnp4nagios/share">
        AllowOverride None
        Order allow,deny
        Allow from all
        #
        # Use the same value as defined in nagios.conf
        #
        #AuthName "Nagios Access"
        #AuthType Basic
        #AuthUserFile /usr/local/nagios/etc/htpasswd.users
        Require valid-user
        <IfModule mod_rewrite.c>
                # Turn on URL rewriting
                RewriteEngine On
                Options FollowSymLinks
                # Installation directory
                RewriteBase /pnp4nagios/
                # Protect application and system files from being viewed
                RewriteRule ^(application|modules|system) - [F,L]
                # Allow any files or directories that exist to be displayed directly
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteCond %{REQUEST_FILENAME} !-d
                # Rewrite all other URLs to index.php/URL
                RewriteRule .* index.php/$0 [PT,L]
        </IfModule>
</Directory>
```


*/etc/apache2/sites-available/default*
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /usr/local/nagios/share/vshell
        <Directory />
                Options Indexes FollowSymLinks
                AllowOverride None
                Allow from all
                AuthType Kerberos
                AuthName "Nagios Authentification"
                KrbMethodNegotiate On
                KrbMethodK5Passwd On
                KrbAuthRealms 1234.COM
                Krb5KeyTab /etc/1234.keytab
                require user xxx@1234.COM
                require user yyy@1234.COM
                require user aaa@1234.COM
                require user bbb@1234.COM
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

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
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


I'm really lost here. Help!!
Thanks.

---

### Post by OpEn_SoUrCe_RoCkS on 2012-03-08
Bump...

I'm still lost, guys!!

---

### Post by Habitual on 2012-03-08
What does /var/log/apache2/error.log say?

---

### Post by OpEn_SoUrCe_RoCkS on 2012-03-08
Here you go!

```
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 478 to 322 : URL /pnp4nagios/index.php/graph, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1240): [client 172.16.0.139] Acquiring creds for HTTP@srv-monitor, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1385): [client 172.16.0.139] Verifying client data using KRB5 GSS-API , referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1401): [client 172.16.0.139] Client didn't delegate us their credential, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] src/mod_auth_kerb.c(1420): [client 172.16.0.139] GSS-API token of length 163 bytes will be sent back, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [error] [client 172.16.0.139] File does not exist: /usr/local/pnp4nagios/share/index.php/graph, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:20 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 301 to 229 : URL /pnp4nagios/index.php/graph, referer: http://srv-monitor/index.php?type=services&state_filter=ACKNOWLEDGED
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Thu Mar 08 11:13:21 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 478 to 322 : URL /favicon.ico
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1628): [client 172.16.0.139] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1240): [client 172.16.0.139] Acquiring creds for HTTP@srv-monitor
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1385): [client 172.16.0.139] Verifying client data using KRB5 GSS-API
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1401): [client 172.16.0.139] Client didn't delegate us their credential
[Thu Mar 08 11:13:21 2012] [debug] src/mod_auth_kerb.c(1420): [client 172.16.0.139] GSS-API token of length 163 bytes will be sent back
[Thu Mar 08 11:13:21 2012] [error] [client 172.16.0.139] File does not exist: /usr/local/nagios/share/vshell/favicon.ico
[Thu Mar 08 11:13:21 2012] [debug] mod_deflate.c(615): [client 172.16.0.139] Zlib: Compressed 286 to 219 : URL /favicon.ico

```


And here is the output of /tmp/rewrite.log:

```
172.16.0.139 - me@COMPANY.COM [08/Mar/2012:11:11:58 --0500] [srv-monitor/sid#b77ba560][rid#b74c1058/initial] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/graph
172.16.0.139 - me@COMPANY.COM [08/Mar/2012:11:11:58 --0500] [srv-monitor/sid#b77ba560][rid#b74c1058/initial] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/graph -> index.php/graph
172.16.0.139 - me@COMPANY.COM [08/Mar/2012:11:11:58 --0500] [srv-monitor/sid#b77ba560][rid#b74c1058/initial] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/graph'
172.16.0.139 - me@COMPANY.COM [08/Mar/2012:11:11:58 --0500] [srv-monitor/sid#b77ba560][rid#b74c1058/initial] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-f' => not-matched
172.16.0.139 - me@COMPANY.COM [08/Mar/2012:11:11:58 --0500] [srv-monitor/sid#b77ba560][rid#b74c1058/initial] (1) [perdir /usr/local/pnp4nagios/share/] pass through /usr/local/pnp4nagios/share/index.php
```

---

### Post by Habitual on 2012-03-08
Error suggests "pattern='!-f" so I'd rem this line out of your /etc/apache2/conf.d/pnp4nagios.conf...
```
RewriteCond %{REQUEST_FILENAME} !-f
```

and try again...

---

### Post by OpEn_SoUrCe_RoCkS on 2012-03-09
That gives me a 500 error an lots and lots of log output!

```
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/graph -> graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/graph -> graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/graph' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'graph' -> 'index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/graph -> /usr/local/pnp4nagios/share/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/graph -> index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (4) add subst prefix: index.php/graph -> /pnp4nagios/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7455058/initial] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/graph -> index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/graph -> index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/graph' -> 'index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/graph -> index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (4) add subst prefix: index.php/index.php/graph -> /pnp4nagios/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7446a28/initial/redir#1] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/graph -> index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/graph -> index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/graph' -> 'index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph -> index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (4) add subst prefix: index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7445760/initial/redir#2] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph -> index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/graph -> index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (4) add subst prefix: index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b74406d8/initial/redir#3] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743f8c0/initial/redir#4] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b743ad90/initial/redir#5] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7436410/initial/redir#6] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7435d90/initial/redir#7] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b7431838/initial/redir#8] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498f730/initial/redir#9] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '^(application|modules|system)' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] add path info postfix: /usr/local/pnp4nagios/share/index.php -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] strip per-dir prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] applying pattern '.*' to uri 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (4) [perdir /usr/local/pnp4nagios/share/] RewriteCond: input='/usr/local/pnp4nagios/share/index.php' pattern='!-d' => matched
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (2) [perdir /usr/local/pnp4nagios/share/] rewrite 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' -> 'index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph'
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (3) [perdir /usr/local/pnp4nagios/share/] add per-dir prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (2) [perdir /usr/local/pnp4nagios/share/] forcing '/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph' to get passed through to next API URI-to-filename handler
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (2) [perdir /usr/local/pnp4nagios/share/] trying to replace prefix /usr/local/pnp4nagios/share/ with /pnp4nagios
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (5) strip matching prefix: /usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (4) add subst prefix: index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph -> /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph
172.16.0.139 - me@COMPANY.COM [09/Mar/2012:08:53:43 --0500] [srv-monitor/sid#b774c648][rid#b498b730/initial/redir#10] (1) [perdir /usr/local/pnp4nagios/share/] internal redirect with /pnp4nagios/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph [INTERNAL REDIRECT]

```

This is after one page load only..

---

### Post by Habitual on 2012-03-09
REM out all the reqwrites then.
Look at this /path...

/usr/local/pnp4nagios/share/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/index.php/graph

CLEARLY a rewrite issue.

---

### Post by OpEn_SoUrCe_RoCkS on 2012-03-09
If I do that, PNP4Nagios doesn't work, and I get a 404.. 

PNP4Nagios depends on mod_rewrite to show its web UI.
What has me confused is why the heck it stopped working randomly, for no apparent reason!

---

