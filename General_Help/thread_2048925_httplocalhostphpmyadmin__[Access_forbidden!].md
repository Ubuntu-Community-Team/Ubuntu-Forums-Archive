---
title: "http://localhost/phpmyadmin/  [Access forbidden!]"
date: 2012-08-27
forum: General Help
---

### Post by mahbubur39 on 2012-08-27
Hello,

I have install ubuntu 12.04 on my dell laptop . I have also install XAMPP on it /opt/lampp

now it works for [http://localhost](http://localhost)


But when i try to access [http://localhost/phpmyadmin](http://localhost/phpmyadmin) then it shows like this 
```

**Access forbidden!**

[COLOR=red][FONT=Times New Roman]New XAMPP security concept:[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Access to the requested object is only available from the local network.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]This setting can be configured in the file "httpd-xampp.conf".[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].[/FONT][/COLOR]
**Error 403**

[localhost]("http://localhost/")
Apache/2.4.2 (Unix) OpenSSL/1.0.1c PHP/5.4.4



```[SIZE=3][COLOR=Plum]here is my httpd-xampp.conf[/COLOR][/SIZE]

```

<IfDefine PHP4>
LoadModule php4_module        modules/libphp4.so
</IfDefine>
<IfDefine PHP5>
LoadModule php5_module        modules/libphp5.so
</IfDefine>
# Disabled in XAMPP 1.8.0-beta2 because of current incompatibilities with Apache 2.4
# LoadModule perl_module        modules/mod_perl.so


Alias /phpmyadmin "/opt/lampp/phpmyadmin"
Alias /phpsqliteadmin "/opt/lampp/phpsqliteadmin"

# since XAMPP 1.4.3
<Directory "/opt/lampp/phpmyadmin">
    AllowOverride AuthConfig Limit
    Order allow,deny
    Allow from all
</Directory>

<Directory "/opt/lampp/phpsqliteadmin">
    AllowOverride AuthConfig Limit
    Order allow,deny
    Allow from all
</Directory>

# since LAMPP 1.0RC1
AddType application/x-httpd-php .php .php3 .php4

XBitHack on

# since 0.9.8 we've mod_perl
<IfModule mod_perl.c>
        AddHandler perl-script .pl
    PerlHandler ModPerl::PerlRunPrefork
    PerlOptions +ParseHeaders
        PerlSendHeader On
</IfModule>

# demo for mod_perl responsehandler
#PerlModule Apache::CurrentTime
#<Location /time>
#      SetHandler modperl
#      PerlResponseHandler Apache::CurrentTime
#</Location>

# AcceptMutex sysvsem is default but on some systems we need this
# thanks to jeff ort for this hint
#AcceptMutex flock
#LockFile /opt/lampp/logs/accept.lock

# this makes mod_dbd happy - oswald, 02aug06
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#DBDriver sqlite3

#
# New XAMPP security concept
#
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))">
    Order deny,allow
        #Deny from all
        Allow from all    
    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>


```
Please help me ..

Thanks for advance..

---

### Post by mahbubur39 on 2012-08-28
Hello,

please can cay one help me :sad::sad::sad::sad::sad::sad:

---

### Post by Rexilion on 2012-08-28
I guess that the following line is somewhat incorrect:

> <LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))">

did you try:

```
http://127.0.0.1/phpmyadmin
```

?

---

### Post by mahbubur39 on 2012-08-29
I got the solution 

first use this [http://daksh21ubuntu.blogspot.co.uk/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.co.uk/2012/07/new-xampp-security-concept-problem-in.html)

then

```

rasel@rasel-Dell:~$ sudo -s
rasel@rasel-Dell:~$ type your password
root@rasel-Dell:/# cd /opt/lampp/phpmyadmin
root@rasel-Dell:/opt/lampp/phpmyadmin# chmod 644 config.inc.php
root@rasel-Dell:/opt/lampp/phpmyadmin# cd /
root@rasel-Dell: /opt/lampp/lampp restart


Thats all its works for me 

```

---

### Post by dakshbhatt21 on 2013-02-23
hey buddy go through this link and if not solve then tell me . . .

[http://daksh21ubuntu.blogspot.in/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.in/2012/07/new-xampp-security-concept-problem-in.html)

---

### Post by zero2xiii on 2013-02-23
Hay,

hate to point out the obvious.. But have you tried http**s** instead of just http?

I know for webmin https is a MUST..

Good luck

---

