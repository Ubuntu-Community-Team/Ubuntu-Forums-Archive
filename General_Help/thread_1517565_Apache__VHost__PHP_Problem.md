---
title: "Apache / VHost / PHP Problem"
date: 2010-06-25
forum: General Help
---

### Post by 4thfloorstudios on 2010-06-25
Hi,
after Ubuntu autoupgraded my Apache, some VHosts are nor working anymore and PHP Code is not oarsed any longer.

I think the apache2.conf was overwritten.

I do not have a clue how ti fix that, I tried some things but now I am stuck.

I have only three hosts: the default, an svn (over port 443) and one called "imcar" which has PHP scripts to be parsed.

So, in my apache2.conf I have this:

```

DocumentRoot /var/www
ServerName localhost
```

The imcar host is set up like this:

```

<VirtualHost *:80>
        ServerName imcar
        ServerAdmin webmaster@imcar
        DocumentRoot /var/www/imcar

        <Directory /var/www/imcar>
                Options FollowSymLinks Indexes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/imcar-error.log

        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

        ServerSignature On
</VirtualHost>
```

If I go to imcar in the browser, the default DocumentRoot is shown. If I remove the default DocumentRoot, I get a 404 on imcar.

Can anyone help me out?

Thanks,
Oliver

---

### Post by Ryan Dwyer on 2010-06-25
Is imcar listed in /etc/apache2/sites-enabled/?

Also, remove your DocumentRoot from apache2.conf. That should all be done in the virtual hosts.

---

### Post by 4thfloorstudios on 2010-06-25
> **Ryan Dwyer said:**
> Is imcar listed in /etc/apache2/sites-enabled/?

Yes, it is.

> **Ryan Dwyer said:**
> Also, remove your DocumentRoot from apache2.conf. That should all be done in the virtual hosts.

Mmmh, without the DocumentRoot default setting, nothing works at all (404 on imcar) and I read that the Apache needs a default DocumentRoot?

I get this error on imcar:

```
Not found

The requested URL / was not found on this server.

```

---

### Post by cdenley on 2010-06-25
Do you have a file such as index.html in /var/www/imcar? That is odd that is giving a 403 error for a directory.
```

echo -e "GET / HTTP/1.0\nHost: imcar\n"|nc -q 1 127.0.0.1 80

```

---

### Post by 4thfloorstudios on 2010-06-25
> **cdenley said:**
> Do you have a file such as index.html in /var/www/imcar? That is odd that is giving a 403 error for a directory.
```

echo -e "GET / HTTP/1.0\nHost: imcar\n"|nc -q 1 127.0.0.1 80

```

I, I do not have a file like that but when going to [http://imcar](http://imcar) I get the localhost directory entries (which is /var/www/). The /var/www/imcar is a symlink but as you see I switched FollowSymLinks on so it should work.

It seems to me that the DocumentRoot is not overwritten by the virtual Host.

The strange thing is, if I edit the vhost file to:

```
NameVirtualHost imcar
<VirtualHost imcar:80>
    ServerName imcar
```

I get an error:

```
[Fri Jun 25 15:15:03 2010] [error] VirtualHost imcar:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
 ... waiting [Fri Jun 25 15:15:04 2010] [error] VirtualHost imcar:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```

but it works for imcar!

Errors result from using two different NameVirtualHost directives I think (NameVirtualHost *:80 and NameVirtualHost imcar).

---

### Post by cdenley on 2010-06-25
In previous versions, "NameVirtualHost" was defined in the vhost configuration. In recent versions, that has been moved to /etc/apache2/ports.conf. Since you said you upgraded, I'm not sure if you replaced ports.conf with the new version. Post this output:
```

grep NameVirtualHost /etc/apache2/ports.conf /etc/apache2/sites-enabled/*

```

---

### Post by 4thfloorstudios on 2010-06-25
> **cdenley said:**
> In previous versions, "NameVirtualHost" was defined in the vhost configuration. In recent versions, that has been moved to /etc/apache2/ports.conf. Since you said you upgraded, I'm not sure if you replaced ports.conf with the new version. Post this output:
```

grep NameVirtualHost /etc/apache2/ports.conf /etc/apache2/sites-enabled/*

```

```

/etc/apache2/ports.conf:NameVirtualHost *:80
/etc/apache2/ports.conf:    NameVirtualHost *:443
/etc/apache2/sites-enabled/imcar:#NameVirtualHost imcar:80
```The imcar entry is from testing...

Edit:
Could it be that my /etc/hosts is wrong? I have 127.0.0.1 for localhost and 127.0.1.1 set for imcar.

---

### Post by cdenley on 2010-06-25
I think the error is complaining that you have NameVirtualHost defined for "*" and "imcar". However, "*" applies to all interfaces, while "imcar" applies to "127.0.0.1", so you have defined "127.0.0.1" twice. Whatever you use in the "VirtualHost" tag should match a "NameVirtualHost" definition. What you originally had (*:80) should work.

Restore your configuration, then post this output:
```

cat /etc/apache2/sites-enabled/*
echo -e "GET / HTTP/1.0\nHost: imcar\n"|nc -q 1 127.0.0.1 80

```

---

### Post by 4thfloorstudios on 2010-06-25
> **cdenley said:**
> I think the error is complaining that you have NameVirtualHost defined for "*" and "imcar". However, "*" applies to all interfaces, while "imcar" applies to "127.0.0.1", so you have defined "127.0.0.1" twice. Whatever you use in the "VirtualHost" tag should match a "NameVirtualHost" definition. What you originally had (*:80) should work.

Restore your configuration, then post this output:
```

cat /etc/apache2/sites-enabled/*
echo -e "GET / HTTP/1.0\nHost: imcar\n"|nc -q 1 127.0.0.1 80

```


Edit:
Forgot to thank you for your quick help! :)

Now it works!

I have changed the /etc/hosts entry from 127.0.1.1 to 127.0.0.1 for imcar.

From my hosts file:

```
127.0.0.1    notebook localhost.localdomain localhost imcar
```Below the output of ```
cat /etc/apache2/sites-enabled/*
```. 

```
<VirtualHost*:80>                                                                                                                                                                   
        ServerName localhost                                                                                                                                                         
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

</VirtualHost>

<VirtualHost *:80>
        ServerName imcar
        ServerAdmin webmaster@imcar
        DocumentRoot /var/www/imcar

        <Directory /var/www/imcar>
                Options FollowSymLinks Indexes
                AllowOverride None            
                Order allow,deny              
                allow from all                
        </Directory>                          

        ErrorLog /var/log/apache2/imcar-error.log

        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
                                                      
        ServerSignature On                            
</VirtualHost>                                        
<VirtualHost *:443>                                   
        ServerName svn                                
        ServerAdmin webmaster@localhost               

        DocumentRoot /var/www/svn/
        SSLEngine on              
        SSLCertificateFile /etc/apache2/ssl/apache.pem
        SSLProtocol all                               
        SSLCipherSuite HIGH:MEDIUM                    
        SSLOptions +FakeBasicAuth                     
        SSLVerifyClient none                          

        <Directory /var/www/svn>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None                       
                Order allow,deny                         
                allow from all                           
        </Directory>                                     

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.                                                   
        LogLevel warn                                                     

        CustomLog /var/log/apache2/access.log combined

        # <Location URL> ... </Location>
        # URL controls how the repository appears to the outside world.
        # In this example clients access the repository as http://hostname/svn/
        # Note, a literal /svn should NOT exist in your document root.
        <Location /svn>

          # Uncomment this to enable the repository
          DAV svn

          # Set this to the path to your repository
          #SVNPath /var/lib/svn
          # Alternatively, use SVNParentPath if you have multiple repositories under
          # under a single directory (/var/lib/svn/repo1, /var/lib/svn/repo2, ...).
          # You need either SVNPath and SVNParentPath, but not both.
          SVNParentPath /var/www/svn
          SVNListParentPath On

          # Access control is done at 3 levels: (1) Apache authentication, via
          # any of several methods.  A "Basic Auth" section is commented out
          # below.  (2) Apache <Limit> and <LimitExcept>, also commented out
          # below.  (3) mod_authz_svn is a svn-specific authorization module
          # which offers fine-grained read/write access control for paths
          # within a repository.  (The first two layers are coarse-grained; you
          # can only enable/disable access to an entire repository.)  Note that
          # mod_authz_svn is noticeably slower than the other two layers, so if
          # you don't need the fine-grained control, don't configure it.

          # Basic Authentication is repository-wide.  It is not secure unless
          # you are using https.  See the 'htpasswd' command to create and
          # manage the password file - and the documentation for the
          # 'auth_basic' and 'authn_file' modules, which you will need for this
          # (enable them with 'a2enmod').
          AuthType Basic
          AuthName "Subversion Repository"
          AuthUserFile /etc/apache2/dav_svn.passwd

          # To enable authorization via mod_authz_svn
          #AuthzSVNAccessFile /etc/apache2/dav_svn.authz

          # The following three lines allow anonymous read, but make
          # committers authenticate themselves.  It requires the 'authz_user'
          # module (enable it with 'a2enmod').
          <LimitExcept GET PROPFIND OPTIONS REPORT>
            Require valid-user
          </LimitExcept>

          SSLRequireSSL
        </Location>
</VirtualHost>
```

---

