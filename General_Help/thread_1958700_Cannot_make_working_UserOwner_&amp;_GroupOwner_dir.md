---
title: "Cannot make working UserOwner &amp; GroupOwner directives in proftpd with xampp"
date: 2012-04-14
forum: General Help
---

### Post by tanoloco on 2012-04-14
Hello,

I've installed  **XAMPP for Linux 1.7.7** which comes with **ProFTPD 1.3.3e**
I wanted to configure proftpd in order that a foo user logins in ftp with  /somewhere/htdocs/fooroot as its documentroot.

To do so, I created a new user foo in my **lubuntu oneiric** and changed in proftpd.conf
```
DefaultRoot ~/ftp-root
```
Then I created a softlink under foo's home called ftp-root and pointing to /somewhere/htdocs/fooroot
```

su foo
cd /home/foo
ln -sT /somewhere/htdocs/footroot ftp-root

```


Everything is working excellently: if I login to ftp as foo I correctly have its htdocs/fooroot as root

**Now the remaining problem is that every new file is owned by foo, while I need a different ownership as nobody:nogroup**

I tried to use
```

UserOwner	nobody
GroupOwner	nogroup

```
with no luck

Here is my current proftpd.conf so far
```

# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName			"ProFTPD"
ServerType			standalone
DefaultServer			on

# Port 21 is the standard FTP port.
Port				21
# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
#Umask				022
Umask				002

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
#Group				nogroup

# Normally, we want files to be overwriteable.
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
</Directory>

# only for the web servers content
#DefaultRoot /opt/lampp/htdocs
DefaultRoot ~/ftp-root

# nobody gets the password "lampp"
UserPassword nobody wRPBu8u4YP0CY

# nobody is no normal user so we have to allow users with no real shell
RequireValidShell off

# nobody may be in /etc/ftpusers so we also have to ignore this file
UseFtpUsers off


```

I tried as said
```

<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
  UserOwner	nobody
  GroupOwner	nogroup
</Directory>

```

it didn't work. I also tried
```

<IfModule mod_cap.c>
  CapabilitiesSet +CAP_CHOWN
</IfModule>
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
  UserOwner	nobody
  GroupOwner	nogroup
</Directory>

```
as suggested here [http://forums.proftpd.org/smf/index.php/topic,1207.msg3751.html#msg3751]("http://forums.proftpd.org/smf/index.php/topic,1207.msg3751.html#msg3751") but it didn't work either.

I've got acl set on htdocs (the parent folder of fooroot), don't know if this interferes somehow
```

drwxrwsr-x+ 11 nobody users  4096 2012-04-14 23:28 htdocs
$ sudo getfacl htdocs
[sudo] password for xxx: 
# file: htdocs
# owner: nobody
# group: users
# flags: -s-
user::rwx
group::rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:other::r-x

```

Here is my vhost setting if needed
```

NameVirtualHost *:8002
Listen 8002

Alias /fooroot/cgi-bin/ 	/media/data/htdocs/cgi-bin/
Alias /fooroot		/media/data/htdocs/fooroot

<VirtualHost 127.0.0.2:80 *:8002>

	ServerAlias fooroot
	ServerName fooroot
	ServerAdmin webmaster@localhost

# 	Possible values include: debug, info, notice, warn, error, crit,
# 	alert, emerg.
# 	LogLevel warn

	DocumentRoot /media/data/htdocs/fooroot
	<Directory /media/data/htdocs/fooroot>
 		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /media/data/htdocs/logs/fooroot-error.log
	CustomLog /media/dati/htdocs/logs/fooroot-access.log combined
</VirtualHost>

```

and my /etc/hosts
```

127.0.0.1	localhost

127.0.0.2	fooroot
...

127.0.1.1	pc-name

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Any suggestion please?

---

### Post by tanoloco on 2012-04-17
Hello,

I solved using virtual users,
please see [http://forums.proftpd.org/smf/index.php/topic,10351.0.html]("http://forums.proftpd.org/smf/index.php/topic,10351.0.html")

---

