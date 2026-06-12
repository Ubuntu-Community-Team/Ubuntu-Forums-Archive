---
title: "ubuntu apache2"
date: 2011-01-06
forum: General Help
---

### Post by cheti on 2011-01-06
Didnt find a topic to make this thread so im gonna make it here (admins can move it later)

I have ubuntu 9 or 10 and i have apache2 with php running there

it works fine ([http://hvmedia.dyndns.org](http://hvmedia.dyndns.org))

but i have a few problems:

1. cant see my subdomains (ezurek and sbnciface) out from my computer
2. hvmedia.dyndns.org/title.php - i cant upload stuff

please help me...
subdomains work if i look them in the server computer, from my PC it doesent work..

---

### Post by bodhi.zazen on 2011-01-06
Can not tell from what you posted.

How did you configure your virtual hosts (sub domains) ? What is the url ?

How did you configure uploads ? to upload files to a server I personally use scp (winscp from windows).

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by cheti on 2011-01-06
I have apache2 ([http://hvmedia.dyndns.org](http://hvmedia.dyndns.org)) and it works fine, except when i try to upload with php ([http://hvmedia.dyndns.org/title.php](http://hvmedia.dyndns.org/title.php)) password is lol, when i try to upload smth, it says file cannot be moved...


Also i created 2 subdomains, but they dont work outside the network, even not from my other computer.

---

### Post by bodhi.zazen on 2011-01-06
> **cheti said:**
> I have apache2 ([http://hvmedia.dyndns.org](http://hvmedia.dyndns.org)) and it works fine, except when i try to upload with php ([http://hvmedia.dyndns.org/title.php](http://hvmedia.dyndns.org/title.php)) password is lol, when i try to upload smth, it says file cannot be moved...


Also i created 2 subdomains, but they dont work outside the network, even not from my other computer.

What are the permissions on the directory you are uploading to / probably need to make the appropriate location writable by apache.
What do the logs show (error message) ?
What are the other two domains ? How did you configure them (DNS and with apache)?

---

### Post by cheti on 2011-01-06
logs dont show any messages, i have only 1 subdomain now and it is ezurek

here is my /etc/apache2/sites-available/default



> <VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/hvmedia
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/hvmedia>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory> "/usr/lib/cgi-bin">
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

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName ezurek.hvmedia.dyndns.org
    ServerAlias ezurek.hvmedia.dyndns.org
    DocumentRoot /var/www/ezurek
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/ezurek>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory> "/usr/lib/cgi-bin">
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

</VirtualHost>here is my /etc/hosts

> 192.168.1.103    asdasd-LIFEBOOK-S7010    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    asdasd-LIFEBOOK-S7010    localhost6.localdomain6    localhost6
127.0.1.1    asdasd-LIFEBOOK-S7010
127.0.0.1    ezurek.hvmedia.dyndns.org
192.168.1.103    ezurek.hvmedia.dyndns.org


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostsand here is my /etc/apache2/httpd.conf

> <VirtualHost 192.168.1.103:80>
DocumentRoot /var/www/ezurek
ServerName ezurek.hvmedia.dyndns.org
ServerAdmin [EMAIL="administrator@hvmedia.dyndns.org"]administrator@hvmedia.dyndns.org[/EMAIL]
ScriptAlias "/cgi-bin/" "/var/www/ezurek/cgi-bin/"
ServerAlias ezurek.hvmedia.dyndns.org
</VirtualHost>i can see the subdomain (ezurek) finely on my servercomputer
but on my other computer i can only see my main domain (hvmedia.dyndns.org)

---

### Post by bodhi.zazen on 2011-01-06
did you register the sub-domain "ezurek.hvmedia.dyndns.org" ?

---

### Post by cheti on 2011-01-07
what you mean ?

i have dyndns.org free account

---

### Post by bodhi.zazen on 2011-01-07
> **cheti said:**
> what you mean ?

i have dyndns.org free account

You can not simply register "hvmedia.dyndns.org" and add on subdomains "ezurek.hvmedia.dyndns.org" or "foo.hvmedia.dyndns.org"

You have to register each subdomain as well, as an A name.

if you are using subdomains you can either register a domain name, just hvmedia , and add the rest by managing your DNS name.

Well, long story short, dyndns is probably not what you want to do.

You can try

hvmedia.dyndns.org/ezurek

---

### Post by cheti on 2011-01-08
> **bodhi.zazen said:**
> You can not simply register "hvmedia.dyndns.org" and add on subdomains "ezurek.hvmedia.dyndns.org" or "foo.hvmedia.dyndns.org"

You have to register each subdomain as well, as an A name.

if you are using subdomains you can either register a domain name, just hvmedia , and add the rest by managing your DNS name.

Well, long story short, dyndns is probably not what you want to do.

You can try

hvmedia.dyndns.org/ezurek
oh, and how do i do that /ezurek ?

---

### Post by bodhi.zazen on 2011-01-08
> **cheti said:**
> oh, and how do i do that /ezurek ?

move /var/www/ezurek to /var/www/hvmedia

Or make the default document root simply /var/www , without any virutal hosts.

You would then browse to 

[http://hvmedia.dyndns.org/media](http://hvmedia.dyndns.org/media)

[http://hvmedia.dyndns.org/ezurek](http://hvmedia.dyndns.org/ezurek)

You could almost certainly do something with mod_rewrite as well.

---

