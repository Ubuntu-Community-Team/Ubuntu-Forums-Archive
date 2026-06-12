---
title: "Bind 9 not creating default configuration"
date: 2009-10-21
forum: General Help
---

### Post by StrangeWill on 2009-10-21
This really sucks because I was just about to configure the local DNS so we didn't have to resolve the server by IP anymore...

Wrote over one of the default configuration files by accident, did an apt-get remove bind9, apt-get install bind9 and I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bind9utils
Suggested packages:
  bind9-doc resolvconf
The following NEW packages will be installed:
  bind9 bind9utils
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/350kB of archives.
After this operation, 1065kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package bind9utils.
(Reading database ... 83455 files and directories currently installed.)
Unpacking bind9utils (from .../bind9utils_1%3a9.5.1.dfsg.P2-1ubuntu0.1_amd64.deb) ...
Selecting previously deselected package bind9.
Unpacking bind9 (from .../bind9_1%3a9.5.1.dfsg.P2-1ubuntu0.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up bind9utils (1:9.5.1.dfsg.P2-1ubuntu0.1) ...
Setting up bind9 (1:9.5.1.dfsg.P2-1ubuntu0.1) ...
wrote key file "/etc/bind/rndc.key"
[B]chgrp: cannot access `/etc/bind/named.conf*': No such file or directory
dpkg: error processing bind9 (--configure):[/B]
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

As you can see parts of it are failing, I can manually create the file, but bind fails to start.

```

Failed to start BIND : Unknown error

```

When I first installed bind, webmin created a default setup with all my local zones, seemed to work fine.

Even with a blank config file it just fails to start, weird...


Edit:

oh error log:
```

Oct 21 10:55:11 Server named[11077]: starting BIND 9.5.1-P2 -c /etc/bind/named.conf -u bind
Oct 21 10:55:11 Server named[11077]: found 2 CPUs, using 2 worker threads
Oct 21 10:55:11 Server named[11077]: using up to 4096 sockets
Oct 21 10:55:11 Server named[11077]: loading configuration from '/etc/bind/named.conf'
Oct 21 10:55:11 Server named[11077]: max open files (1024) is smaller than max sockets (4096)
Oct 21 10:55:11 Server named[11077]: using default UDP/IPv4 port range: [1024, 65535]
Oct 21 10:55:11 Server named[11077]: using default UDP/IPv6 port range: [1024, 65535]
Oct 21 10:55:11 Server named[11077]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 21 10:55:11 Server named[11077]: listening on IPv4 interface eth0, 172.16.100.20#53
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 0.IN-ADDR.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 127.IN-ADDR.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 254.169.IN-ADDR.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: D.F.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: A.E.F.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: automatic empty zone: B.E.F.IP6.ARPA
Oct 21 10:55:11 Server named[11077]: command channel listening on 127.0.0.1#953
Oct 21 10:55:11 Server named[11077]: command channel listening on ::1#953
Oct 21 10:55:11 Server named[11077]: the working directory is not writable
Oct 21 10:55:11 Server named[11077]: couldn't open pid file '/var/run/named/named.pid': Permission denied


```
 I guess chown /etc/bind to bind, and do... something with the pid file?


Well I chowned the /var/run/named directory to the user bind, still isn't working... odd...

---

### Post by Giblet5 on 2009-10-21
It just installed when I did it on a clean Karmic beta...

Here are my perms, maybe that'll help.

```
ls -ld /etc/bind
drwxr-sr-x 2 root postdrop 4096 2009-09-02 18:53 /etc/bind
gumbi@pokey.com$ ls -lR /etc/bind
/etc/bind:
total 64
-rw-r--r-- 1 root root      237 2008-01-11 09:19 db.0
-rw-r--r-- 1 root root      304 2008-01-31 10:13 db.127
-rw-r--r-- 1 root postdrop 1081 2009-03-19 15:16 db.192.168.1
-rw-r--r-- 1 root root      237 2008-01-11 09:19 db.255
-rw-r--r-- 1 root postdrop  383 2009-03-16 16:20 db.acme.com
-rw-r--r-- 1 root root      353 2008-01-11 09:19 db.empty
-rw-r--r-- 1 root root      256 2008-01-28 14:37 db.local
-rw-r--r-- 1 root root     1170 2008-09-22 16:52 db.mydomain.net
-rw-r--r-- 1 root postdrop  782 2009-03-16 16:35 db.palazzorospo.com
-rw-r--r-- 1 root root     1506 2008-01-11 09:19 db.root
-rw-r--r-- 1 root postdrop 1693 2009-03-19 15:10 named.conf
-rw-r--r-- 1 root bind      490 2009-08-19 18:03 named.conf.default-zones
-rw-r--r-- 1 root postdrop  586 2009-03-19 14:58 named.conf.local
-rw-r--r-- 1 root postdrop  913 2008-01-28 16:14 named.conf.options
-rw-r--r-- 1 gdm  postdrop   77 2008-01-28 15:53 rndc.key
-rw-r--r-- 1 root root     1317 2008-01-11 09:19 zones.rfc1918
```

Note that setgid bit on the directory...

---

### Post by StrangeWill on 2009-10-21
I changed the named.pid to be in the working directory:
```

root@Server:/etc# chmod 755 bind
root@Server:/etc# ls -ld /etc/bind
drwxr-sr-x 2 bind bind 4096 2009-10-21 10:59 /etc/bind

```
```

Oct 21 11:22:29 Server named[13398]: the working directory is not writable
Oct 21 11:22:29 Server named[13398]: couldn't open pid file 'named.pid': Permission denied

```

Edit:
I get "the working directory is not writable" if I chmod the /etc/bind directory to 777, that is ridiculous.


My config:
```

options {
	directory "/etc/bind";
	pid-file "/var/run/named/named.pid";
	};

server 172.16.100.1 {
	};


```

---

### Post by StrangeWill on 2009-10-21
This is pretty system breaking for our new name lookups, while we can do without it *right now* we'll need it soon, is there a way to delete EVERYTHING bind did and do a clean install?

---

### Post by Giblet5 on 2009-10-21
> **StrangeWill said:**
> I changed the named.pid to be in the working directory:
```

root@Server:/etc# chmod 755 bind
root@Server:/etc# ls -ld /etc/bind
drwxr-sr-x 2 bind bind 4096 2009-10-21 10:59 /etc/bind

```
```

Oct 21 11:22:29 Server named[13398]: the working directory is not writable
Oct 21 11:22:29 Server named[13398]: couldn't open pid file 'named.pid': Permission denied

```

Edit:
I get "the working directory is not writable" if I chmod the /etc/bind directory to 777, that is ridiculous.


My config:
```

options {
	directory "/etc/bind";
	pid-file "/var/run/named/named.pid";
	};

server 172.16.100.1 {
	};


```

If that is your config, then the named.pid is being written to /var/run/named/named.pid and not /etc/bind (the working directory).

The mode on /var/run/named should be 775. The ownership should be root:bind (root and bind group users have full access).

How did things go so wrong?

---

### Post by Giblet5 on 2009-10-21
> **StrangeWill said:**
> This is pretty system breaking for our new name lookups, while we can do without it *right now* we'll need it soon, is there a way to delete EVERYTHING bind did and do a clean install?

At this point, you're probably better off fixing the /var/run/named directory permissions.

That's where you're erroring-out.

Bind is 50KV of simple... I can't imagine how you could have so many problems with, what for me was, a one-liner and some edits.

---

### Post by StrangeWill on 2009-10-21
> **Giblet5 said:**
> At this point, you're probably better off fixing the /var/run/named directory permissions.

That's where you're erroring-out.

Bind is 50KV of simple... I can't imagine how you could have so many problems with, what for me was, a one-liner and some edits.
I can't believe I'm having issues either, it was working fine. The thing that makes me question it being a simple configuration issue is if I run bind as root user, it still errors out with permission errors, too bad that is impossible. ;P

Furthermore, reinstalling it didn't change permissions on anything (that I know of...) and as far as I see, a clean install should also work flawlessly (it isn't).


Log:
```

Oct 21 14:09:53 Server named[27665]: starting BIND 9.5.1-P2 -c /etc/bind/named.conf
Oct 21 14:09:53 Server named[27665]: found 2 CPUs, using 2 worker threads
Oct 21 14:09:53 Server named[27665]: using up to 4096 sockets
Oct 21 14:09:53 Server named[27665]: loading configuration from '/etc/bind/named.conf'
Oct 21 14:09:53 Server named[27665]: max open files (1024) is smaller than max sockets (4096)
Oct 21 14:09:53 Server named[27665]: using default UDP/IPv4 port range: [1024, 65535]
Oct 21 14:09:53 Server named[27665]: using default UDP/IPv6 port range: [1024, 65535]
Oct 21 14:09:53 Server named[27665]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 21 14:09:53 Server named[27665]: listening on IPv4 interface eth0, 172.16.100.20#53
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 0.IN-ADDR.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 127.IN-ADDR.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 254.169.IN-ADDR.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: D.F.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: A.E.F.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: automatic empty zone: B.E.F.IP6.ARPA
Oct 21 14:09:53 Server named[27665]: command channel listening on 127.0.0.1#953
Oct 21 14:09:53 Server named[27665]: the working directory is not writable
Oct 21 14:09:53 Server named[27665]: couldn't open pid file '/var/run/named/named.pid': Permission denied
Oct 21 14:09:53 Server named[27665]: exiting (due to early fatal error)

```

```

root@Server:/# ls -ld /var/run/named
drwxrwxr-x 2 root bind 40 2009-10-21 12:32 /var/run/named
root@Server:/# ls -ld /etc/bind
drwxrwsr-x 2 root bind 4096 2009-10-21 12:31 /etc/bind

```

```

options {
        directory "/etc/bind";
        pid-file "/var/run/named/named.pid";
        };

server 172.16.100.1 {
        };

```

Still getting the same error starting it.

---

### Post by Giblet5 on 2009-10-21
> **StrangeWill said:**
> 
Still getting the same error starting it.


Let's start over, shall we? ;)

```
sudo apt-get remove bind9 --purge
sudo rm -r /etc/bind /var/run/named

## Verify at this point that there is no bind user in
## /etc/passwd, no bind group in /etc/group,
## and no reference to named or bind9 in /etc/insserv.conf
# If no traces, bind 9 is gone.

sudo apt-get install bind9
```


If you get the same error again, we need to report a broken package.

---

### Post by StrangeWill on 2009-10-21
Excellent! Purging the application and deleting the users was the fix. :D

Thanks a ton.


Only a minor issue where it seems to spawn a new instance every time I start it (no option to stop on webmin for some reason), but a small issue that I think I can fix. :D
Edit: 
Done, pid was in a funny directory, find / -name *.pid found it.

---

### Post by silktaco on 2009-11-24
Hey - I had the same problem as this and followed the steps but the solution at the bottom wasn't complete.

I determined after a lot of effort apparmor restricts named rw access to /etc/bind, where is where my bind zone files were.  There are two fixes. Move to /var/lib/bind or adjust apparmor accordingly.

Apprmor may have been the original problem on this thread in the first place - don't know, just saying.

Finally, the reason I put my zone files in /etc/bind is that's because, well, just because. good luck.

Above for the record.

---

### Post by t00ls on 2009-11-26
I just registered because I was looking for a bug report, which brought me here ...........

I'm not sure if this relates, I just did two installs of 9.10,both installations flawless.2 different machines, one in virtual box and one on a dell blade server. Using webmin,I notice that bind only says start, when you click on start, it still says start.

I found a while ago 2 people having the same problem, the default pid file location is messed up....  c&p------------------------------->

the path for the PID is bad after the upgrade of Ubuntu: before:  /var/run/bind/run/named.pid or /var/run/named.pid after:  /var/run/named/named.pid
<-----------------------------end c&p


when I changed it,all I did is put /named in it's place.....return to bind server in webmin.....it's already running

again...if I', in the wrong place ...sorry

---

