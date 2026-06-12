---
title: "apache virtual hosts"
date: 2006-04-12
forum: General Help
---

### Post by chocolatetoothpaste on 2006-04-12
I am running apache web server for development.  I have defined a virtual host, but when I type it in to my browser, it does a google search instead, and sends me to a website.  Has anyone had issues with virtual hosts?  Does someone know how to fix this issue?
here are my config files.
httpd.conf:
```

##
## httpd.conf -- Apache HTTP server configuration file
##



ServerType standalone

ServerRoot /etc/apache


LockFile /var/lock/apache.lock


PidFile /var/run/apache.pid

ScoreBoardFile /var/run/apache.scoreboard

Timeout 300


KeepAlive On

MaxKeepAliveRequests 100


KeepAliveTimeout 15

MinSpareServers 5
MaxSpareServers 10

StartServers 5

MaxClients 150

MaxRequestsPerChild 100

Include /etc/apache/modules.conf


<IfModule mod_status.c>
  ExtendedStatus On
</IfModule>


Port 80

User www-data
Group www-data

ServerAdmin webmaster@localhost

ServerName localhost

DocumentRoot /var/www

<Directory />
    Options SymLinksIfOwnerMatch
    AllowOverride None
</Directory>

<Directory /var/www/>


    Options Indexes Includes FollowSymLinks MultiViews


    AllowOverride None

    Order allow,deny
    Allow from all
</Directory>

<IfModule mod_userdir.c>
    UserDir public_html

    <Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        <Limit GET POST OPTIONS PROPFIND>
            Order allow,deny
            Allow from all
        </Limit>
        <Limit PUT DELETE PATCH PROPPATCH MKCOL COPY MOVE LOCK UNLOCK>
            Order deny,allow
            Deny from all
        </Limit>
    </Directory>
</IfModule>


<IfModule mod_dir.c>
    DirectoryIndex index.html index.htm index.shtml index.cgi index.php
</IfModule>

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

UseCanonicalName Off

TypesConfig /etc/mime.types

DefaultType text/plain

<IfModule mod_mime_magic.c>
    MIMEMagicFile /usr/share/misc/file/magic.mime
</IfModule>


HostnameLookups Off

ErrorLog /var/log/apache/error.log

LogLevel warn

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\" %T %v" full
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\" %P %T" debug
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{forensic-id}n\"" forensic
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

CustomLog /var/log/apache/access.log combined

<IfModule mod_log_forensic.c>
 ForensicLog /var/log/apache/forensic.log
</IfModule>

<IfModule mod_backtrace.c>
 EnableExceptionHook On

</IfModule>

<IfModule mod_whatkilledus.c>
 EnableExceptionHook On

</IfModule>

ServerSignature On

<IfModule mod_alias.c>
    Alias /icons/ /usr/share/apache/icons/

    <Directory /usr/share/apache/icons>
         Options Indexes MultiViews
         AllowOverride None
         Order allow,deny
         Allow from all
    </Directory>

    Alias /images/ /usr/share/images/

    <Directory /usr/share/images>
         Options MultiViews
         AllowOverride None
         Order allow,deny
         Allow from all
    </Directory>
</IfModule>

<IfModule mod_alias.c>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

    <Directory /usr/lib/cgi-bin/>
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
</IfModule>

<IfModule mod_autoindex.c>

    IndexOptions FancyIndexing NameWidth=*

    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

    AddIcon /icons/binary.gif .bin .exe
    AddIcon /icons/binhex.gif .hqx
    AddIcon /icons/tar.gif .tar
    AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
    AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
    AddIcon /icons/a.gif .ps .ai .eps
    AddIcon /icons/layout.gif .html .shtml .htm .pdf
    AddIcon /icons/text.gif .txt
    AddIcon /icons/c.gif .c
    AddIcon /icons/p.gif .pl .py
    AddIcon /icons/f.gif .for
    AddIcon /icons/dvi.gif .dvi
    AddIcon /icons/uuencoded.gif .uu
    AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
    AddIcon /icons/tex.gif .tex
    AddIcon /icons/bomb.gif core
    AddIcon /icons/deb.gif .deb

    AddIcon /icons/back.gif ..
    AddIcon /icons/hand.right.gif README
    AddIcon /icons/folder.gif ^^DIRECTORY^^
    AddIcon /icons/blank.gif ^^BLANKICON^^

    DefaultIcon /icons/unknown.gif

    ReadmeName README.html
    HeaderName HEADER.html

    IndexIgnore .??* *~ *# HEADER.html HEADER.txt RCS CVS *,v *,t

</IfModule>

<IfModule mod_mime.c>

    AddEncoding x-compress Z
    AddEncoding x-gzip gz tgz

    AddLanguage da .dk
    AddLanguage nl .nl
    AddLanguage en .en
    AddLanguage et .ee
    AddLanguage fr .fr
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage it .it
    AddLanguage ja .ja
    AddCharset ISO-2022-JP .jis
    AddLanguage pl .po
    AddCharset ISO-8859-2 .iso-pl
    AddLanguage pt .pt
    AddLanguage pt-br .pt-br
    AddLanguage lb .lu
    AddLanguage ca .ca
    AddLanguage es .es
    AddLanguage sv .se
    AddLanguage cs .cz

    <IfModule mod_negotiation.c>
        LanguagePriority en da nl et fr de el it ja pl pt pt-br lb ca es sv
    </IfModule>


    AddType application/x-tar .tgz
    AddType image/bmp .bmp

    # hdml
    AddType text/x-hdml .hdml


    <IfModule mod_include.c>
     AddType text/html .shtml
     AddHandler server-parsed .shtml
    </IfModule>

</IfModule>

AddDefaultCharset on

<IfModule mod_setenvif.c>

    BrowserMatch "Mozilla/2" nokeepalive
    BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0

    BrowserMatch "RealPlayer 4\.0" force-response-1.0
    BrowserMatch "Java/1\.0" force-response-1.0
    BrowserMatch "JDK/1\.0" force-response-1.0
</IfModule>


# If the perl module is installed, this will be enabled.
<IfModule mod_perl.c>
  <IfModule mod_alias.c>
   Alias /perl/ /var/www/perl/
  </IfModule>
  <Location /perl>
    SetHandler perl-script
    PerlHandler Apache::Registry
    Options +ExecCGI
  </Location>
</IfModule>

http://servername/server-status


# Allow access to local system documentation from localhost.
# (Debian Policy assumes /usr/share/doc is "/doc/", at least from the localhost.)
<IfModule mod_alias.c>
 Alias /doc/ /usr/share/doc/
</IfModule>

<Location /doc>
  order deny,allow
  deny from all
  allow from 127.0.0.0/255.0.0.0
  Options Indexes FollowSymLinks MultiViews
</Location>

<IfModule mod_proxy.c>

</IfModule>
# End of proxy directives.

### Section 3: Virtual Hosts
#
# VirtualHost: If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them.
# Please see the documentation at <URL:http://www.apache.org/docs/vhosts/>
# for further details before you try to setup virtual hosts.
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# If you want to use name-based virtual hosts you need to define at
# least one IP address (and port number) for them.
#
#NameVirtualHost 12.34.56.78:80
#NameVirtualHost 12.34.56.78

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
#
#<VirtualHost ip.address.of.host.some_domain.com>
#    ServerAdmin webmaster@host.some_domain.com
#    DocumentRoot /www/docs/host.some_domain.com
#    ServerName host.some_domain.com
#    ErrorLog logs/host.some_domain.com-error.log
#    CustomLog logs/host.some_domain.com-access.log common
#</VirtualHost>

#<VirtualHost _default_:*>
#</VirtualHost>

# Automatically added by the post-installation script
# as part of the transition to a config directory layout
# similar to apache2, and that will help users to migrate
# from apache to apache2 or revert back easily
Include /etc/apache/conf.d



```

and vhosts.conf
```

NameVirtualHost *
<VirtualHost *>
  ServerName      percus
  DocumentRoot    /home/ross/www/perc_us
  DirectoryIndex  info.php index.php index.htm
</VirtualHost>

```

---

### Post by motionsiren on 2006-05-22
you will probably want to edit your /etc/hosts file with a 

```
1.2.3.4   percus
```


where 1.2.3.4 is the IP address you virtualhost is serving from.

---

