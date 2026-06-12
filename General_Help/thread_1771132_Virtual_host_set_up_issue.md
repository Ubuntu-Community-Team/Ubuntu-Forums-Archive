---
title: "Virtual host set up issue"
date: 2011-05-30
forum: General Help
---

### Post by zanzibarwinds on 2011-05-30
Hi

Currently have uBuntu 11.4 installed

Have setup the LAMP server but have an issue with my sites showing with the 'public_html' within the url.

If I go to [http://john-virtualbox/mysite/](http://john-virtualbox/mysite/) I get a browser directory listing like

```

Index of /mysite
[ICO]    Name    Last modified    Size    Description
[DIR]    Parent Directory         -      
[DIR]    cgi-bin/    30-May-2011 08:03     -      
[DIR]    logs/    30-May-2011 08:24     -      
[DIR]    public_html/    13-Jan-2011 10:50     -      
Apache/2.2.17 (Ubuntu) Server at john-virtualbox Port 80

```the site will serve pages fine if I then click on public_html and the url becomes [http://john-virtualbox/mysite/public_html/]("http://john-virtualbox/supplyco/public_html/")

Any help in this regard would be outstanding. I've tried various changes within the configuration files within /etc/apache2/sites-available without success.

Below is the contents of the httpd.conf, apache2.conf and the mysite virtual host file if its relevent.

many thanks
John

/etc/apache2/conf.d

```

#
#  We're running multiple virtual hosts.
#
NameVirtualHost localhost:80

<VirtualHost localhost:80>

</VirtualHost>

```/etc/apache2/sites-enabled/ mysite file contents (Symbolicly linked files through a2ensite mysite)
```

<VirtualHost *:80>
    

    ServerAdmin john@mysite.com
        ServerName  mysite
        ServerAlias mysite

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/mysite/public_html

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/mysite/cgi-bin
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/mysite/logs/error.log
        CustomLog /var/www/mysite/logs/access.log combined
</VirtualHost>
```/etc/apache2/sites-available/ mysite file contents
```

<VirtualHost *:80>
    

    ServerAdmin john@mysite.com
        ServerName  mysite
        ServerAlias mysite

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/mysite/public_html

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/mysite/cgi-bin
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/mysite/logs/error.log
        CustomLog /var/www/mysite/logs/access.log combined
</VirtualHost>

```**httpd.conf** is blank

**apache2.conf**
```

#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

LockFile ${APACHE_LOCK_DIR}/accept.lock


PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

KeepAlive On

MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

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

# These need to be set in /etc/apache2/envvars
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

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

ServerName localhost
```

---

