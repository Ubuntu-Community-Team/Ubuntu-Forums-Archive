---
title: "Bind"
date: 2012-06-06
forum: General Help
---

### Post by jmore9 on 2012-06-06
Hello !

I am running Ubuntu 12.04 Desktop and have seen that there are some updates for BIND.  Now i do not have a server running that i know about so are these updates needed ?

What is BIND on the desktop used for ?  Is it needed at all ?

Thanks for your time in advance

---

### Post by btindie on 2012-06-06
BIND is a DNS server used for providing hostname resolution. It may have been installed as a dependency of something else you installed?

I think when you install KVM (virtual machine host) it tends to depend on dnsmasq which is similar and provides extra features.

It should be save to remove it, it'll complain if something else depends on it.

---

### Post by jmore9 on 2012-06-06
Ok I dont have vm installed as far as i know unless something else needed it.  I will attempt to remove it and see what happens.

Thanks for the response.

---

### Post by jmore9 on 2012-06-06
When i try to uninstall some of the bind9 componets it wants to remove ubuntu-desktop , not good.  Here is a list of some of the items that it wants to upgrade - to me they look like some kind of server stuff but i don't know a lot about the server side.

Heres is some of what it wants to install / upgrade



Version of "host" bundled with BIND 9.X --- bind9-host

Clients provided with BIND --- dnsutils

BIND9 Shared Library used by BIND --- libbind9-80

DNS Shared Library used by BIND --- libdns81

ISC Shared Library used by BIND --- libisc83

Command Channel Libarry used by BIND --- libisccc80 

Config file handling library used by BIND --- libsiccfg82

Lightweight Resolver Library used by BIND --- liblwres80


recommended updates

Windows matching library - daemon --- bamfdaemon

Internationalization support for MIT Kerberos --- krb5-locales

Windows matching library - shared library --- libbamf0

Windows matching library - shared library --- libbamf3-0

MIT kerberos runtime libraries-krb5 GSS-API Mechanism --- Libgssapi

and about 20 more similiar


Looks to a reinstall is coming up.  Neverhad thses updates in any previous ubuntus that i have ran.

Any ideas ?

---

### Post by btindie on 2012-06-06
Which packages are you trying to remove?

It doesn't look like the ubuntu-desktop meta package depends directly on any of the bind packages. However some of the other packages may in turn depend on some of the BIND libraries, this doesn't necessarily include the daemon process.

To find out if named is listening on port 53 run
```
sudo netstat -npul | grep :53
```To see which packages are installed with bind in the name run
```
dpkg -l '*bind*'
```If you type the following you'll see if it's running```
sudo service bind9 status
```

---

### Post by jmore9 on 2012-06-06
sudo netstat -npul | grep :53
[sudo] password for jeffm: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           589/avahi-daemon: r
udp        0      0 127.0.0.1:53            0.0.0.0:*                           957/dnsmasq     
udp6       0      0 :::5353   
jeffm@jeffm-MS-7108:~$



dpkg -l '*bind*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  bind           <none>         (no description available)
un  bind9          <none>         (no description available)
ii  bind9-host     1:9.8.1.dfsg.P Version of 'host' bundled with BIND 9.X
un  libbind0       <none>         (no description available)
un  libbind9-41    <none>         (no description available)
ii  libbind9-80    1:9.8.1.dfsg.P BIND9 Shared Library used by BIND
ii  libindi-data   0.8-1ubuntu1   Instrument-Neutral Device Interface library 
ii  libindi0       0.8-1ubuntu1   Instrument-Neutral Device Interface library 
un  libindicate    <none>         (no description available)
ii  libindicate-gt 0.6.92-0ubuntu library for raising indicators via DBus - GT
un  libindicate-qt <none>         (no description available)
ii  libindicate-qt 0.2.5.91-1ubun Qt bindings for libindicate
ii  libindicate5   0.6.92-0ubuntu library for raising indicators via DBus
ii  libindicator-m 0.6.0-0ubuntu1 indicator status provider - shared library
ii  libindicator3- 0.5.0-0ubuntu1 panel indicator applet - shared library
ii  libindicator7  0.5.0-0ubuntu1 panel indicator applet - shared library
ii  libkeybinder0  0.2.2-3build1  registers global key bindings for applicatio
ii  libpam-winbind 2:3.6.3-2ubunt Samba nameservice and authentication integra
ii  winbind        2:3.6.3-2ubunt Samba nameservice integration server
jeffm@jeffm-MS-7108:~$ 



sudo service bind9 status
bind9: unrecognized service
jeffm@jeffm-MS-7108:~$ 


So is the samba thing using the bind ?

---

### Post by jmore9 on 2012-06-07
Finally figured out what they were attached to , something called remmia remote deaktop or somethng like that.  Uninstalled that and the updates went away.

---

