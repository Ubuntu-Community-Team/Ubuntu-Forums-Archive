---
title: "Apache2 only serves default VirtualHost"
date: 2010-03-25
forum: General Help
---

### Post by kentuckyShades on 2010-03-25
All,

I have three server names pointing to the same IP address (site1.com, site2.com, and site3.com), however apache2 is redirecting all requests for site2 and site3 to site1 (site1 is my first declared virtual host listed in my sites-available folder). 

These lines are in my httpd.conf file:
```

Listen 8080
ServerName [http://123.45.67.89:8080](http://123.45.67.89:8080)
DocumentRoot "/media/disk1/mystuff/htdocs"

```

I have a file /etc/apache2/conf.d/virtual.conf that only contains this line:
```

NameVirtualHost *:8080

```
and there are three files in /etc/apache2/sites-available

000-site1.com
001-site2.com
002-site3.com

000-site1.com contains the following:
```

<VirtualHost *:8080>
ServerName [www.site1.com](www.site1.com)
ServerAlias site1.com *.site1.com
DocumentRoot /media/disk1/mystuff/htdocs/site1.com
# Indexes + Directory Root.
DirectoryIndex index.html
DocumentRoot /media/disk1/mystuff/htdocs/site1.com
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /media/disk1/mystuff/htdocs/site1.com>
Options +Indexes FollowSymLinks +ExecCGI
AllowOverride AuthConfig FileInfo
Order allow,deny
Allow from all
</Directory>
# CGI Directory
ScriptAlias /cgi-bin/ /media/disk1/mystuff/htdocs/site1.com/cgi-bin/
<Location /cgi-bin>
Options +ExecCGI
</Location>
# Logfiles
ErrorLog /var/log/apache2/site1.com/error.log
CustomLog /var/log/apache2/site1.com/access.log combined
</VirtualHost>

```
site2 and site3 are more or less the same except for these lines...
```

ServerName [www.site2.com](www.site2.com)
ServerAlias site2.com *.site2.com
DocumentRoot /media/disk1/mystuff/htdocs/site2.com

```
Why can't apache figure out where to send requests for site2 and site3? What am I missing? Any help would be greatly appreciated!

---

### Post by cdenley on 2010-03-25
This belongs in the Server section. Did you enable the site configurations?
```

sudo a2ensite 000-site1.com
sudo a2ensite 001-site2.com
sudo a2ensite 002-site3.com
sudo /etc/init.d/apache2 reload

```

You shouldn't be adding anything to httpd.conf. If you need apache to listen on port 8080, that belongs in /etc/apache2/ports.conf.

---

### Post by kentuckyShades on 2010-03-25
I enabled each of my sites-available using the a2ensite command you mentioned and reloaded, but apache still points site2 and site3 to site1.

I'm not sure exactly what you meant by "this belongs in the server section". What belongs in the server section?

And if I remove Listen, ServerName, and DocumentRoot from httpd.conf, I get the following error when restarting apache

```

 * Stopping web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

---

### Post by cdenley on 2010-03-25
> **kentuckyShades said:**
> 
I'm not sure exactly what you meant by "this belongs in the server section". What belongs in the server section?


You posted this thread in the "General" section. Your post would get noticed by more server experts if you had posted it in the "Server" section.
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Are you sure your web browser isn't displaying a cached page?
```

echo -e "GET / HTTP/1.0\nHost: site1.com\n"|nc 127.0.0.1 8080
echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc 127.0.0.1 8080
echo -e "GET / HTTP/1.0\nHost: site3.com\n"|nc 127.0.0.1 8080

```

---

### Post by kentuckyShades on 2010-03-25
oops, I'm new to this site and this was my first thread. You're right, this post would've been better off in the server section. There's no way to move this thread once it's been created, is there? And yes, I have the same problem after flushing all my browser cache.

---

### Post by kentuckyShades on 2010-03-25
Hmm, I ran your echo command and seemed to have received the expected output, but apache still redirects site2 to site1 from my browser.

```

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc 127.0.0.1 8080
HTTP/1.1 200 OK
Date: Thu, 25 Mar 2010 21:16:38 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 10 Mar 2010 00:58:55 GMT
ETag: "b2c-3c-48167cd6e11c0"
Accept-Ranges: bytes
Content-Length: 60
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

<html><body><h1>index page of site2.com</h1></body></html>


```

---

### Post by cdenley on 2010-03-25
> **kentuckyShades said:**
> Hmm, I ran your echo command and seemed to have received the expected output, but apache still redirects site2 to site1 from my browser.

```

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc 127.0.0.1 8080
HTTP/1.1 200 OK
Date: Thu, 25 Mar 2010 21:16:38 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 10 Mar 2010 00:58:55 GMT
ETag: "b2c-3c-48167cd6e11c0"
Accept-Ranges: bytes
Content-Length: 60
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

<html><body><h1>index page of site2.com</h1></body></html>


```

Well the server is working properly. Either it is still cached, or the browser isn't sending the correct hostname in the http request.

---

### Post by kentuckyShades on 2010-03-25
I flushed my browser cache twice already and have the same problem. I tried it with both chrome and firefox, and even repeated the process on different machines on my network and no luck. 

Do you have any other ideas what could be causing apache to redirect all server name requests to my default virtualhost?

---

### Post by cdenley on 2010-03-25
> **kentuckyShades said:**
> I flushed my browser cache twice already and have the same problem. I tried it with both chrome and firefox, and even repeated the process on different machines on my network and no luck. 

Do you have any other ideas what could be causing apache to redirect all server name requests to my default virtualhost?

Try posting your entire site configurations for all 3 sites.
```

cat /etc/apache2/sites-enabled/*

```

---

### Post by kentuckyShades on 2010-03-26
```

~$ cat /etc/apache2/sites-enabled/*
<VirtualHost *:8080>                             
        ServerName www.site1.com        
        ServerAlias site1.com *.site1.com
        DocumentRoot /media/disk1/mystuff/htdocs/site1.com
        # Indexes + Directory Root.                           
        DirectoryIndex index.html                             
        DocumentRoot /media/disk1/mystuff/htdocs/site1.com
        <Directory />                                         
                Options FollowSymLinks                        
                AllowOverride None                            
        </Directory>                                          
        <Directory /media/disk1/mystuff/htdocs/site1.com> 
                Options +Indexes FollowSymLinks +ExecCGI      
                AllowOverride AuthConfig FileInfo             
                Order allow,deny                              
                Allow from all                                
        </Directory>                                          
        # CGI Directory                                       
        ScriptAlias /cgi-bin/ /media/disk1/mystuff/htdocs/site1.com/cgi-bin/
        <Location /cgi-bin>                                                     
                Options +ExecCGI                                                
        </Location>                                                             
        # Logfiles                                                              
        ErrorLog  /var/log/apache2/site1.com/error.log                 
        CustomLog /var/log/apache2/site1.com/access.log combined       
</VirtualHost>                                                                  
<VirtualHost *:8080>                                                            
        ServerName www.site2.com                                        
        ServerAlias site2.com *.site2.com             
        DocumentRoot /media/disk1/mystuff/htdocs/site2.com               
        # Indexes + Directory Root.                                             
        DirectoryIndex index.html                                               
        DocumentRoot /media/disk1/mystuff/htdocs/site2.com               
        <Directory />                                                           
                Options FollowSymLinks                                          
                AllowOverride None                                              
        </Directory>                                                            
        <Directory /media/disk1/mystuff/htdocs/site2.com>                
                Options +Indexes FollowSymLinks +ExecCGI                        
                AllowOverride AuthConfig FileInfo                               
                Order allow,deny                                                
                Allow from all
        </Directory>
        # CGI Directory
        ScriptAlias /cgi-bin/ /media/disk1/mystuff/htdocs/site2.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>
        # Logfiles
        ErrorLog  /var/log/apache2/site2.com/error.log
        CustomLog /var/log/apache2/site2.com/access.log combined
</VirtualHost>
<VirtualHost *:8080>
        ServerName www.site3.com                                        
        ServerAlias site3.com *.site3.com
        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /media/disk1/mystuff/htdocs/site3.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /media/disk1/mystuff/htdocs/site3.com>
                Options +Indexes FollowSymLinks +ExecCGI
                AllowOverride AuthConfig FileInfo
                Order allow,deny
                Allow from all
        </Directory>
        # CGI Directory
        ScriptAlias /cgi-bin/ /media/disk1/mystuff/htdocs/site3.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>
        # Logfiles
        ErrorLog  /var/log/apache2/site3.com/error.log
        CustomLog /var/log/apache2/site3.com/access.log combined
</VirtualHost>


```

---

### Post by spiderbatdad on 2010-03-26
The problem appears to be that you do not have NameVirtualHost directives...this is required, as far as I know, even when using ServerAlias.
[http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost)
[http://httpd.apache.org/docs/2.0/mod/core.html#serveralias](http://httpd.apache.org/docs/2.0/mod/core.html#serveralias)

---

### Post by kentuckyShades on 2010-03-26
My NameVirtualHost directive is declared as follows and I still have the same issue.
```

~$ cat /etc/apache2/conf.d/virtual.conf
NameVirtualHost *:8080

```

---

### Post by cdenley on 2010-03-26
> **kentuckyShades said:**
> My NameVirtualHost directive is declared as follows and I still have the same issue.
```

~$ cat /etc/apache2/conf.d/virtual.conf
NameVirtualHost *:8080

```

I think that belongs in /etc/apache2/ports.conf. Are you sure you're connecting to port 8080 from your browser?

[http://site2.com:8080/](http://site2.com:8080/)

```

nc -z -v site2.com 8080
echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc site2.com 8080

```

---

### Post by kentuckyShades on 2010-03-26
I tried your commands with and without the 8080 reference since my DNS provider already does a port 80 redirect for me. Also,  moving the NameVirtualHost directive from /etc/apache2/conf.d/virtual.conf to /etc/apache2/ports.conf didn't make any difference. The reason I had it in conf.d was because I read that "When Apache starts up it reads the contents of all files included in /etc/apache2/conf.d, and files you create here won't get trashed on package upgrades."

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

```

~$ nc -z -v site2.com 8080
DNS fwd/rev mismatch: site2.com != url-redirect.noip.net
Warning: inverse host lookup failed for ***.**.**.251: Unknown host
site2.com [***.**.**.252] 8080 (http-alt) : No route to host

~$ nc -z -v site2.com
Warning: inverse host lookup failed for ***.**.**.251: Unknown host
DNS fwd/rev mismatch: site2.com != url-redirect.noip.net
no port[s] to connect to

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc site2.com 8080
site2.com [***.**.**.252] 8080 (http-alt) : No route to host

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc site2.com
no port[s] to connect to

```

---

### Post by cdenley on 2010-03-26
> **kentuckyShades said:**
> I tried your commands with and without the 8080 reference since my DNS provider already does a port 80 redirect for me. Also,  moving the NameVirtualHost directive from /etc/apache2/conf.d/virtual.conf to /etc/apache2/ports.conf didn't make any difference. The reason I had it in conf.d was because I read that "When Apache starts up it reads the contents of all files included in /etc/apache2/conf.d, and files you create here won't get trashed on package upgrades."

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

```

~$ nc -z -v site2.com 8080
DNS fwd/rev mismatch: site2.com != url-redirect.noip.net
Warning: inverse host lookup failed for ***.**.**.251: Unknown host
site2.com [***.**.**.252] 8080 (http-alt) : No route to host

~$ nc -z -v site2.com
Warning: inverse host lookup failed for ***.**.**.251: Unknown host
DNS fwd/rev mismatch: site2.com != url-redirect.noip.net
no port[s] to connect to

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc site2.com 8080
site2.com [***.**.**.252] 8080 (http-alt) : No route to host

~$ echo -e "GET / HTTP/1.0\nHost: site2.com\n"|nc site2.com
no port[s] to connect to

```

There is no such thing as "redirect" with DNS services. The domain name needs to resolve to an IP which can be used to connect to your web server. However, I'm guessing site2.com, or whatever it really is, is resolving to a web server hosted by whoever you got the domain from. Their web server then redirects to a URL you gave. The output you posted indicated that whatever server site2.com resolves to, it isn't listening on port 8080. Simply removing the "8080" argument results in an invalid syntax since netcat doesn't assume port 80.

Your web server is working properly. Now you need real DNS service, not some redirection service. Any request your server receives on port 80 will have no matching site configurations, and the global DocumentRoot will be used.

---

