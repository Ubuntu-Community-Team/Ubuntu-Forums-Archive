---
title: "ubuntu and xampp help"
date: 2010-08-30
forum: General Help
---

### Post by onio on 2010-08-30
hello everyone?

i need same error can anyone help me?
i'm connect by putty

**Access forbidden!**

            
     [COLOR=red]New XAMPP security concept:[/COLOR]
     Access to the requested directory is only available from the local network.
     This setting can be configured in the file "httpd-xampp.conf".
           
  If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].

---

### Post by WorMzy on 2010-08-30
Well, have you looked at that config file?

---

### Post by onio on 2010-08-30
> **WorMzy said:**
> Well, have you looked at that config file?

yeah i'm looked but i'm not understand :(
can you help me?

---

### Post by WorMzy on 2010-08-30
Well, I don't use XAMPP, but if you post the config file here, I'll take a look at it.

---

### Post by onio on 2010-08-30
> **WorMzy said:**
> Well, I don't use XAMPP, but if you post the config file here, I'll take a look at it.
ok , inside httpd-xampp.conff file

<IfDefine PHP4>
LoadModule php4_module        modules/libphp4.so
</IfDefine>
<IfDefine PHP5>
LoadModule php5_module        modules/libphp5.so
</IfDefine>
# since LAMPP 0.9.8:
LoadModule perl_module        modules/mod_perl.so

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
    Allow from ::1 127.0.0.0/8 202.180.218.213/8 \
        fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 \
        fe80::/10 169.254.0.0/16

    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>

---

### Post by onio on 2010-08-30
Lost connection to MySQL server at 'reading initial communication packet',  system error: 111 


what is error?   :confused:

---

### Post by WorMzy on 2010-08-30
```
#
# New XAMPP security concept
#
<LocationMatch "^/(?i?ampp|security|licenses|phpmyadmin|webalize r|server-status|server-info))">
Order deny,allow
#Deny from all
Allow from ::1 127.0.0.0/8 202.180.218.213/8 \
fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 \
fe80::/10 169.254.0.0/16

ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>
```

Well, I believe this is where the problem is. If you want to access these URLs from outside of your local network, then delete this entire section.

If you only want to be able to access a single address from it (e.g. [www.yoururl.com/phpmyadmin](www.yoururl.com/phpmyadmin)) then just remove that argument from the location match.

So ```
<LocationMatch "^/(?i?ampp|security|licenses|_phpmyadmin|_webalize r|server-status|server-info))">
```
becomes
```
<LocationMatch "^/(?i?ampp|security|licenses|webalize r|server-status|server-info))">
```

About the error 111, look here: [http://stackoverflow.com/questions/1420839/cant-connect-to-mysql-server-error-111](http://stackoverflow.com/questions/1420839/cant-connect-to-mysql-server-error-111)

---

### Post by onio on 2010-08-30
thank you

also [AMXBans] SQL error: can't connect: 'Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)'

---

### Post by WorMzy on 2010-08-30
Now, that one I'm not so sure about. There's a number of different solutions for this, but the success rate for each of them seems to vary.

The one that I normally recommend is just creating the file by "touch"ing it, then "chown"ing it to mysql. But I don't know whether XAMPP creates the mysql user when you install it, since I've never used it.

You could try it anyway, it can't do any harm.

```
sudo touch /tmp/mysql.sock
```
```
sudo chown mysql /tmp/mysql.sock
```

If that doesn't help then you might be able to find a more effective solution on the [XAMPP forums]("http://www.apachefriends.org/f/viewforum.php?f=34").

Don't forget to remove the file we created:
```
sudo rm /tmp/mysql.sock
```

---

### Post by onio on 2010-08-31
i'm installing commands
[COLOR=#993300][FONT=Courier New]sudo  /etc/init.d/apache2 
[/FONT][/COLOR][COLOR=#993300][FONT=Courier New]sudo  apt-get install mysql-server[/FONT][/COLOR]
[COLOR=#993300][FONT=Courier New]sudo  apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin[/FONT][/COLOR]


URl [http://xocoo.wordpress.com/2009/04/30/installing-lamp-on-ubuntu/](http://xocoo.wordpress.com/2009/04/30/installing-lamp-on-ubuntu/)

i'm great DB but cannot connect mysql 
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by onio on 2010-08-31
can anyone help me?

SQL error: can't connect: 'Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)'

[IMG]http://img153.imageshack.us/img153/7928/errorsda.jpg[/IMG]


Cannot connect DB.  Web [http://202.180.218.140/view.php](http://202.180.218.140/view.php)

19 tables greated in DB when installing web


Also restart apache2

 * Restarting web server apache2                                                      [Tue Aug 31 18:50:33 2010] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
 ... waiting [Tue Aug 31 18:50:34 2010] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.

???


i'm added 


[LIST]
[*] [COLOR=#993300]sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin[/COLOR]
[/LIST]
 [COLOR=#000000]gksudo gedit /etc/apache2/apache2.conf[/COLOR]   [COLOR=#000000][/COLOR]edit [COLOR=#000000]apache2.conf[/COLOR] file
add

 [COLOR=#000000]Include /etc/phpmyadmin/apache.conf[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]in end line[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]this is correct?
[/COLOR]

---

### Post by onio on 2010-09-01
i'm cheking netstat -an|more

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 202.180.218.140:53      0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0     52 202.180.218.140:22      202.180.218.129:49496   ESTABLISHED
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN
udp        0      0 202.180.218.140:53      0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp6       0      0 :::53                   :::*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     2852     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    2941     @/org/kernel/udev/ude
vd
unix  7      [ ]         DGRAM                    3732     /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     46071    /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     52769
unix  3      [ ]         STREAM     CONNECTED     52768
unix  2      [ ]         DGRAM                    52292
unix  2      [ ]         DGRAM                    4499
unix  2      [ ]         DGRAM                    4160
unix  2      [ ]         DGRAM                    3854
unix  2      [ ]         DGRAM                    3817
unix  3      [ ]         DGRAM                    2975
unix  3      [ ]         DGRAM                    2974
unix  3      [ ]         STREAM     CONNECTED     2923     @/com/ubuntu/upstart


can anyone help me?

---

### Post by onio on 2010-09-02
> **onio said:**
> i'm cheking netstat -an|more

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 202.180.218.140:53      0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0     52 202.180.218.140:22      202.180.218.129:49496   ESTABLISHED
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN
udp        0      0 202.180.218.140:53      0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp6       0      0 :::53                   :::*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     2852     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    2941     @/org/kernel/udev/ude
vd
unix  7      [ ]         DGRAM                    3732     /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     46071    /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     52769
unix  3      [ ]         STREAM     CONNECTED     52768
unix  2      [ ]         DGRAM                    52292
unix  2      [ ]         DGRAM                    4499
unix  2      [ ]         DGRAM                    4160
unix  2      [ ]         DGRAM                    3854
unix  2      [ ]         DGRAM                    3817
unix  3      [ ]         DGRAM                    2975
unix  3      [ ]         DGRAM                    2974
unix  3      [ ]         STREAM     CONNECTED     2923     @/com/ubuntu/upstart


can anyone help me?

anyone here?

---

