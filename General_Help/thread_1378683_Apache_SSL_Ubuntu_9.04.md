---
title: "Apache SSL Ubuntu 9.04"
date: 2010-01-11
forum: General Help
---

### Post by patdundee on 2010-01-11
Hi guys
 
One one of my servers I have multiple sites with various IP address's. Each site works fine with this as the first line
<VirtualHost *:80>
 
 
I am having a problem with SSL on the server 
 
I have moved a site from Ubuntu 8.10 which ran with no errors on port 80 and port 443 with its own respective IP
 
I have assigned a Seperate IP for the ssl cert on the site in question but I get an error when I apply changes and Apache Stops
 
SSL is enabled on the server
 
As soon as I add the SSL Virtual host apache will not start. If I rem out SSLEngine on then apache starts and all sites run except of course the 443 site
 
Every site except for this one runs as <VirtualHost *:80>
 
This sites config runs as shown below and also errors if the virtusl host is changed to *:80
 
<VirtualHost IP Address:80>
DocumentRoot /path to site
ServerName site name
ServerAlias site name
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /path to site>
Options FollowSymLinks MultiViews
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
LogLevel warn
CustomLog /var/log/apache2/access.log combined
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
DirectoryIndex home.php index.html index.xhtml default.htm default.html index.php default.php
</VirtualHost>
 
<VirtualHost IP Address:443>
DocumentRoot /path to site
ServerName Site name
SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/site.crt
SSLCertificateKeyFile /etc/ssl/private/site.key
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /path to site>
Options FollowSymLinks MultiViews
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
LogLevel warn
CustomLog /var/log/apache2/access.log combined
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
DirectoryIndex home.php index.html index.xhtml default.htm default.html index.php default.php
<Directory "/path to site">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
 
Any help would be greatly appreciated

---

### Post by spiderbatdad on 2010-01-11
what is the error in your apache logs? Have you checked the ports.conf directory?

---

### Post by patdundee on 2010-01-11
Hi Spider
Now thats strange Brand new Cert just got it a while ago and the apache logs show
 
[Tue Jan 12 00:26:48 2010] [error] Init: Unable to read server certificate from file /etc/ssl/certs/filename.crt

---

### Post by spiderbatdad on 2010-01-11
Does your doc root point to the correct ssl cert file?
```
DocumentRoot /path to site
ServerName Site name
SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
**SSLCertificateFile /etc/ssl/certs/site.crt**
SSLCertificateKeyFile /etc/ssl/private/site.key
```

---

### Post by patdundee on 2010-01-11
Hi Spider
Here is the full apache log for the error
 
[Tue Jan 12 00:47:10 2010] [error] Init: Unable to read server certificate from file /etc/ssl/certs/domainname.crt

[Tue Jan 12 00:47:10 2010] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag

[Tue Jan 12 00:47:10 2010] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error

---

### Post by patdundee on 2010-01-11
Yup it odes point correctly
 
Not had an error like that before :)

---

### Post by spiderbatdad on 2010-01-11
```
SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
```
This error suggests the csr and crt files are mixed up.

---

### Post by patdundee on 2010-01-11
Hi
Got that sorted and changed it from a crt to a pem
 
Now for some reason it is asking the following
 
* Starting web server apache2
Apache/2.2.11 mod_ssl/2.2.11 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server [www.360cycles.co.uk:443](www.360cycles.co.uk:443) (RSA)
Enter pass phrase:Apache:mod_ssl:Error: Private key not found.
**Stopped
   ...fail!
 
I do not remember using a passphrase but I have an idea what it is. Is there a way we can skip the passphrase when Apache restarts or can the passphrase be hard coded

---

### Post by spiderbatdad on 2010-01-11
That I do not know.Back when I ran apache from home ( a couple of years ago now) I always had to enter a passphrase for the certificate upon restart. I would look through the Apache ssl documentation.
[http://httpd.apache.org/docs/2.2/ssl/](http://httpd.apache.org/docs/2.2/ssl/)

---

### Post by patdundee on 2010-01-11
Hi Spider
 
Found the solution
 
If you remember the passphrase then
 
cmd line 
 
$ openssl rsa -in keyname.key -out nekeyname.key
 
cp the newkeyname to the correct directory and adjust the config as required
 
:)

---

### Post by spiderbatdad on 2010-01-12
Thanks for posting back your solution. :D

---

