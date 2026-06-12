---
title: "Having problems with mumble-server"
date: 2011-01-12
forum: General Help
---

### Post by Espryon on 2011-01-12
Ive tweaked the .ini file with little tweaks back and forth trying to get it so i can atleast connect to the server with a superuser and a different port then default but no luck at all.  Any help would be appreciated and also mods if you move this can you pm me to where to moved it lol.

Heres the mumble-server.ini file 

```
# Path to database. If blank, will search for
# murmur.sqlite in default locations or create it if not found.
database=/home/espryon/murmur.sqlite

# If you wish to use something other than SQLite, you'll need to set the name
# of the database above, and also uncomment the below.
# Sticking with SQLite is strongly recommended, as it's the most well tested
# and by far the fastest solution.
#
#dbDriver=QMYSQL
#dbUsername=
#dbPassword=
#dbHost=
#dbPort=
#dbPrefix=murmur_
#dbOpts=

# Murmur defaults to not using D-Bus. If you wish to use dbus, which is one of the
# RPC methods available in murmur, please specify so here.
#
# dbus=system

# Alternate service name. Only use if you are running distinct
# murmurd processes connected to the same D-Bus daemon.
#dbusservice=net.sourceforge.mumble.murmur

# If you want to use ZeroC Ice to communicate with Murmur, you need
# to specify the endpoint to use. Since there is no authentication
# with ICE, you should only use it if you trust all the users who have
# shell access to your machine.
# Please see the ICE documentation on how to specify endpoints.
# ice="tcp -h 127.0.0.1 -p 6502"

# Ice primarily uses local sockets. This means anyone who has a
# user account on your machine can connect to the Ice services.
# You can set a plaintext "secret" on the Ice conntection, and
# any script attempting to access must then have this secret.
#icesecret=

# How many login attempts do we tolerate from one IP
# inside a given timeframe before we ban the connection?
# Note that this is global (shared between all virtual servers), and that
# it counts both successfull and unsuccessfull connection attempts.
# Set either Attempts or Timeframe to 10 to disable.
#autobanAttempts = 10
#autobanTimeframe = 120
#autobanTime = 300

# Murmur default to logging to murmur.log. If you leave this blank,
# murmur will log to the console (linux) or through message boxes (win32).
logfile=/home/espryon/Desktop/mumble-server.log

# If set, murmur will write its process ID to this file.
pidfile=/var/run/mumble-server/mumble-server.pid

# The below will be used as defaults for new configured servers.
# If you're just running one server (the default), it's easier to
# configure it here than through D-Bus or Ice.
#
# Welcome message sent to clients when they connect
welcometext="<br />Welcome Espryon's Mumble Server this server is running <b>Murmur</b>.<br />Enjoy your stay!<br />"

# Port to bind TCP and UDP sockets to
port=9988

# Specific IP or hostname to bind to.
# If this is left blank (default), murmur will bind to all available addresses.
#host=
# Password to join server
serverpassword=Agent007
# Maximum bandwidth (in bits per second) clients are allowed
# to send speech at.
bandwidth=72000

# Maximum number of concurrent clients allowed.
users=100

# Regular expression used to validate channel names
# (note that you have to escape backslashes with \ )
#channelname=[ \\-=\\w\\#\\[\\]\\{\\}\\(\\)\\@\\|]+

# Regular expression used to validate user names
# (note that you have to escape backslashes with \ )
#username=[-=\\w\\[\\]\\{\\}\\(\\)\\@\\|\\.]+

# Maximum length of text messages in characters. 0 for no limit.
#textmessagelength=5000

# Maximum length of text messages in characters, with image data. 0 for no limit.
#imagemessagelength=131072

# Allow clients to use HTML in messages, user comments and channel descriptions?
#allowhtml=true

# Murmur retains the per-server log entries in an internal database which
# allows it to be accessed over D-Bus/ICE.
# How many days should such entries be kept?
logdays=31

# To enable public server registration, the serverpassword must be blank, and
# this must all be filled out.
# The password here is used to create a registry for the server name; subsequent
# updates will need the same password. Dont lose your password.
# The URL is your own website, and only set the registerHostname for static IP
# addresses.
#
#registerName=
#registerPassword=
#registerUrl=http://mumble.sourceforge.net/
#registerHostname=

# To enable bonjour service discovery uncomment the following line.
# To change the name announced by bonjour adjust the registerName variable.
# See [http://developer.apple.com/networking/bonjour/index.html](http://developer.apple.com/networking/bonjour/index.html) for more information
# about bonjour.
#bonjour=True

# If you have a proper SSL certificate, you can provide the filenames here.
#sslCert=
#sslKey=

# If murmur is started as root, which user should it switch to?
# This option is ignored if murmur isnt started with root privileges.
uname=Espry

# If this options is enabled, only clients which have a certificate are allowed
# to connect.
#certrequired=False

# You can configure any of the configuration options for Ice here. We recommend
# leave the defaults as they are.
# Please note that this section has to be last in the configuration file.
#
[Ice]
Ice.Warn.UnknownProperties=1
Ice.MessageSizeMax=65536
```

and i get a log like this

```
<W>2011-01-11 22:23:11.849 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 22:23:11.863 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 22:23:11.878 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 22:23:11.883 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.69" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 22:23:11.885 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 22:23:11.914 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 22:23:12.050 1 => Server: TCP Listen on [::]:9988 failed: The bound address is already in use
<W>2011-01-11 22:23:12.114 1 => Stopped
<W>2011-01-11 22:26:06.779 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 22:26:06.793 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 22:26:06.807 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 22:26:06.813 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.70" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 22:26:06.814 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 22:26:06.844 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 22:26:07.010 1 => Server listening on [::]:9988
<W>2011-01-11 22:26:07.101 1 => Announcing server via bonjour
<W>2011-01-11 22:26:07.200 1 => Not registering server as public
<W>2011-01-11 22:28:20.220 1 => <1:(-1)> New connection: 192.168.0.153:55397
<W>2011-01-11 22:28:20.386 1 => <1:(-1)> Connection closed: The remote host closed the connection [1]
<W>2011-01-11 22:37:07.768 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 22:37:07.782 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 22:37:07.796 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 22:37:07.801 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.79" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 22:37:07.803 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 22:37:07.833 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 22:37:07.978 1 => Server listening on [::]:9989
<W>2011-01-11 22:37:08.067 1 => Announcing server via bonjour
<W>2011-01-11 22:37:08.168 1 => Not registering server as public
<W>2011-01-11 22:53:59.780 Initializing settings from /home/espryon/Desktop/mumble-server.ini (basepath /home/espryon/Desktop)
<W>2011-01-11 22:53:59.794 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 22:53:59.809 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 22:53:59.814 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.89" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 22:53:59.815 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 22:53:59.844 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 22:53:59.947 1 => Server: TCP Listen on [::]:9989 failed: The bound address is already in use
<W>2011-01-11 22:54:00.035 1 => Stopped
<W>2011-01-11 22:59:11.611 Initializing settings from /home/espryon/Desktop/mumble-server.ini (basepath /home/espryon/Desktop)
<W>2011-01-11 22:59:11.625 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 22:59:11.639 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 22:59:11.645 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.91" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 22:59:11.646 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 22:59:11.675 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 22:59:11.806 1 => Server listening on [::]:9989
<W>2011-01-11 22:59:11.892 1 => Announcing server via bonjour
<W>2011-01-11 22:59:11.967 1 => Not registering server as public
<W>2011-01-11 23:21:43.750 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 23:21:43.751 Binding to address 192.168.0.153
<W>2011-01-11 23:21:43.764 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 23:21:43.778 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 23:21:43.783 Failed to register on DBus: org.freedesktop.DBus.Error.AccessDenied Connection ":1.94" is not allowed to own the service "net.sourceforge.mumble.murmur" due to security policies in the configuration file
<C>2011-01-11 23:21:43.785 MurmurIce: Initialization failed: Ice::SocketException
<W>2011-01-11 23:21:43.814 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 23:21:43.949 1 => Server: TCP Listen on 192.168.0.153:64738 failed: The bound address is already in use
<W>2011-01-11 23:21:44.030 1 => Stopped
<W>2011-01-11 23:29:23.260 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 23:29:23.274 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 23:29:23.289 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 23:29:23.321 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 23:29:23.460 1 => Server listening on [::]:9988
<W>2011-01-11 23:29:23.540 1 => Announcing server via bonjour
<W>2011-01-11 23:29:23.626 1 => Registration needs nonempty 'registername', 'registerpassword' and 'registerurl', must have an empty 'password' and allowed pings.
<W>2011-01-11 23:30:08.050 1 => <1:(-1)> New connection: 192.168.0.153:46309
<W>2011-01-11 23:30:08.236 1 => <1:(-1)> Connection closed: The remote host closed the connection [1]
<W>2011-01-11 23:35:23.481 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-11 23:35:23.495 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<W>2011-01-11 23:35:23.509 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-11 23:35:23.540 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<W>2011-01-11 23:35:23.663 1 => Server: TCP Listen on [::]:9988 failed: The bound address is already in use
<W>2011-01-11 23:35:23.744 1 => Stopped
<W>2011-01-12 00:03:39.893 Initializing settings from /etc/mumble-server.ini (basepath /etc)
<W>2011-01-12 00:03:39.907 SSL: Added CA certificates from '/etc/ssl/certs/ca-certificates.crt'
<C>2011-01-12 00:03:39.919 WARNING: You are running murmurd as root, without setting a uname in the ini file. This might be a security risk.
<W>2011-01-12 00:03:39.938 ServerDB: Openend SQLite database /home/espryon/murmur.sqlite
<W>2011-01-12 00:03:39.941 Resource limits were 0 0
<W>2011-01-12 00:03:39.941 Successfully dropped capabilities
<W>2011-01-12 00:03:39.970 Murmur 1.2.2 (1.2.2-4) running on X11: Ubuntu 10.10: Booting servers
<F>2011-01-12 00:03:39.974 SQL Error [INSERT INTO `slog` (`server_id`, `msg`) VALUES(?,?)]: disk I/O error Unable to fetch row

```
The fact of the matter is ive read multiple faqs over the past 3 days and tried configuring it on my laptop then my dedicated server then reloaded ubuntu and ive had constant problems.  To be completely honest i dont know what people see in mumble but my guild wants mumble over teamspeak 3.  Any help would be much appreciated.

---

### Post by Espryon on 2011-01-12
bump="bump" Oo

---

### Post by Espryon on 2011-01-12
> **Espryon said:**
> bump="bump" Oo
.

---

### Post by Espryon on 2011-01-12
[QUOTE=Espryon;10346874].[/QUOTE.

---

### Post by s.fox on 2011-01-12
Please refrain from BUMPING your posts so regularly.

Please wait 24 hours before BUMPING again.

Thank you.

---

