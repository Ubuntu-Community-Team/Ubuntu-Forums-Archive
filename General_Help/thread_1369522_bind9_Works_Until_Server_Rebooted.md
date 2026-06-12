---
title: "bind9 Works Until Server Rebooted"
date: 2010-01-01
forum: General Help
---

### Post by shortsword on 2010-01-01
Noob Alert.  But, not to Linux.  I have been using Fedora Core, Fedora, Red Hat, Suse, and Ubuntu at work and home, for more than 5 years.  At work I administer machines and develop software for Linux/Microsoft/mainframes.  But, this is my first foray into the Bind world.  So, there I be a noob.

I have been using host files at home to resolve the various machines on my LAN for several years.  That is a problem when we take a power hit, have other problems with the router, change routers, or machines come and go on the LAN.  The last is especially egregious as we get more and more wireless machines coming around.  It is way to much work to get all the hosts files correct again.  Setting up a DNS server and having to make changes in only one locale for the whole LAN is very attractive.  And, I now have a machine that is up 24X7X356 since last March.  So I have had this attractive idea in my mind since then.  And, having a few spare cycles over the holidays, decided to go forward.

So, using the fine tutorial I found in the Ubuntu documentation I set out to do this on my always up machine.  And had some success.  After restarting bind9 all the machines on my LAN were able to resolve both local IP addresses and WAN side IP addresses without a problem.

Until I rebooted the machine hosting bind9.  After rebooting that machine, it is necessary to again restart bind9 before machines on the LAN can resolve IP addresses.

Investigation showed me that during boot the domain service ends up listening on port 53 only on localhost.  Here is the result of the specified netstat command just after rebooting,


```
sudo netstat -aunt | grep 53

tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp6       0      0 :::53                   :::*                               
```

After executing "sudo /etc/init.d/bind9 restart" the same netstat command gives this,

```
tcp        0      0 192.168.1.102:53        0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           127.0.0.1:36180         TIME_WAIT  
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
udp        0      0 192.168.1.102:53        0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp6       0      0 :::53                   :::*         
```

Here is the entries from the /var/log/daemon.log applicable to named during reboot:

```
Jan  1 00:55:20 diningroom named[7773]: shutting down: flushing changes
Jan  1 00:55:20 diningroom named[7773]: stopping command channel on 127.0.0.1#953
Jan  1 00:55:20 diningroom named[7773]: stopping command channel on ::1#953
Jan  1 00:55:20 diningroom named[7773]: no longer listening on ::#53
Jan  1 00:55:20 diningroom named[7773]: no longer listening on 127.0.0.1#53
Jan  1 00:55:20 diningroom named[7773]: no longer listening on 192.168.1.102#53
Jan  1 00:55:20 diningroom named[7773]: exiting
Jan  1 00:56:23 diningroom NetworkManager: <info>  starting... 
Jan  1 00:56:26 diningroom named[5060]: starting BIND 9.4.2-P2.1 -u bind
Jan  1 00:56:26 diningroom named[5060]: found 1 CPU, using 1 worker thread
Jan  1 00:56:26 diningroom named[5060]: loading configuration from '/etc/bind/named.conf'
Jan  1 00:56:26 diningroom named[5060]: listening on IPv6 interfaces, port 53
Jan  1 00:56:26 diningroom named[5060]: listening on IPv4 interface lo, 127.0.0.1#53
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: D.F.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 8.E.F.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: 9.E.F.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: A.E.F.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: automatic empty zone: B.E.F.IP6.ARPA
Jan  1 00:56:26 diningroom named[5060]: command channel listening on 127.0.0.1#953
Jan  1 00:56:26 diningroom named[5060]: command channel listening on ::1#953
Jan  1 00:56:26 diningroom named[5060]: zone 0.in-addr.arpa/IN: loaded serial 1
Jan  1 00:56:26 diningroom named[5060]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan  1 00:56:26 diningroom named[5060]: zone 1.168.192.in-addr.arpa/IN: loaded serial 20091231
Jan  1 00:56:26 diningroom named[5060]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan  1 00:56:26 diningroom named[5060]: /etc/bind/db.gladieuxnet:17: #diningroom.gladieuxnet: bad owner name (check-names)
Jan  1 00:56:26 diningroom named[5060]: zone gladieuxnet/IN: loading from master file /etc/bind/db.gladieuxnet failed: bad owner name (check-names)
Jan  1 00:56:26 diningroom named[5060]: zone localhost/IN: loaded serial 2
Jan  1 00:56:26 diningroom named[5060]: running
```

And these are the entries from the same log file when the "sudo /etc/init.d/bind9 restart" command is run,

```
Jan  1 01:03:47 diningroom named[5060]: shutting down: flushing changes
Jan  1 01:03:47 diningroom named[5060]: stopping command channel on 127.0.0.1#953
Jan  1 01:03:47 diningroom named[5060]: stopping command channel on ::1#953
Jan  1 01:03:47 diningroom named[5060]: no longer listening on ::#53
Jan  1 01:03:47 diningroom named[5060]: no longer listening on 127.0.0.1#53
Jan  1 01:03:47 diningroom named[5060]: exiting
Jan  1 01:03:49 diningroom named[7629]: starting BIND 9.4.2-P2.1 -u bind
Jan  1 01:03:49 diningroom named[7629]: found 1 CPU, using 1 worker thread
Jan  1 01:03:49 diningroom named[7629]: loading configuration from '/etc/bind/named.conf'
Jan  1 01:03:49 diningroom named[7629]: listening on IPv6 interfaces, port 53
Jan  1 01:03:49 diningroom named[7629]: listening on IPv4 interface lo, 127.0.0.1#53
Jan  1 01:03:49 diningroom named[7629]: listening on IPv4 interface eth0, 192.168.1.102#53
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: D.F.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 8.E.F.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: 9.E.F.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: A.E.F.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: automatic empty zone: B.E.F.IP6.ARPA
Jan  1 01:03:49 diningroom named[7629]: command channel listening on 127.0.0.1#953
Jan  1 01:03:49 diningroom named[7629]: command channel listening on ::1#953
Jan  1 01:03:49 diningroom named[7629]: zone 0.in-addr.arpa/IN: loaded serial 1
Jan  1 01:03:49 diningroom named[7629]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan  1 01:03:49 diningroom named[7629]: zone 1.168.192.in-addr.arpa/IN: loaded serial 20091231
Jan  1 01:03:49 diningroom named[7629]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan  1 01:03:49 diningroom named[7629]: /etc/bind/db.gladieuxnet:17: #diningroom.gladieuxnet: bad owner name (check-names)
Jan  1 01:03:49 diningroom named[7629]: zone gladieuxnet/IN: loading from master file /etc/bind/db.gladieuxnet failed: bad owner name (check-names)
Jan  1 01:03:49 diningroom named[7629]: zone localhost/IN: loaded serial 2
Jan  1 01:03:49 diningroom named[7629]: running
```

Note that in the first set of log entries and the first netstat output, named listened on both ports 53 and 953 but only for the localhost address.  In the second set of log entiries and netstat output, named listens on port 53 on both localhost and on 192.168.1.102 (the IP address of the machine running bind/named) and listens on port 953 only on localhost.

Here is the contents of my /etc/bind/named.conf file,

```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";
```

Of the files mentioned therein, the only one that I have changed from the original installation version is /etc/bind/named.conf.local.  That file contains,

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "gladieuxnet" {
	type master;
	file "/etc/bind/db.gladieuxnet";
};

zone "1.168.192.in-addr.arpa" {
	type master;
	notify no;
	file "/etc/bind/db.192";
};
```

The /etc/bind/db.gladieuxnet file contains,

```
;
; BIND data file for gladieunet
;
$TTL	604800
@	IN	SOA	diningroom.gladieuxnet. sshortsword.cox.net. (
		       20091231		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@			IN	NS	diningroom.gladieuxnet.
@			IN	A	192.168.1.102
ns			IN	A	192.168.1.102
joshuaroom		IN	A	192.168.1.100
laptop1			IN	A	192.168.1.101
heatherroom		IN	A	192.168.1.103
diningroomWinMedia	IN	A	192.168.1.105
joshualaptop		IN	A	192.168.1.106
```

And the /etc/bind/db.192 file contains,

```
;
; BIND reverse data file for gladieuxnet
;
$TTL	604800
@	IN	SOA	gladieuxnet. sshortsword.cox.net. (
		       20091231		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	gladieuxnet.
1.0.0	IN	PTR	gladieuxnet.
```

My /etc/hosts file contains,

```
127.0.0.1 localhost
192.168.1.102 diningroom.gladieuxnet DININGROOM diningroom
192.168.1.103 heatherroom.gladieuxnet HEATHERROOM heatherroom
192.168.1.100 joshuaroom.gladieuxnet JOSHUAROOM joshuaroom
192.168.1.105 diningroomWinMedia.gladieuxnet DININGROOMWINMEDIA diningroommedia
192.168.1.101 laptop1.gladieuxnet LAPTOP1 laptop1
192.168.1.106 joshualaptop.gladieuxnet JOSHUALAPTOP joshualaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

This hosts file contents was generated by some software.  This is readable, but the file was much more readable (though containing similar information) before I started messing with bind9.

My /etc/resolv.conf file contains,

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5007
#
### END INFO

search oc.cox.net


nameserver 192.168.1.102
nameserver 68.105.28.12
nameserver 68.105.29.12
```

My /etc/host.conf file contains,

```
# The "order" line is only used by old versions of the C library.
order bind,hosts
multi on
```

This file has been changed since I began the bind9 exercise, the order value was previously hosts,bind.

Finally, my whole LAN is sitting behind a NAT router which has NO open ports.  All "servers" on my LAN can be accessed ONLY from the LAN, as far as I know.  The router is set to feed all LAN machines my local DNS server's IP address as the primary DNS server and the first two of my ISP's DNS servers as the secondary and tertiary DNS servers.  See the results of this in the contents of the generated /etc/resolv.conf file above.  And all machines both Windows and Linux are getting those three DNS addresses from the router.

The DNS server (192.168.1.102) has a firewall rule allowing everone on the LAN to access port 53.  It also has rules allowing only known LAN machines to access ssh (port 22) and ipp (port 631).  Everything else on the machine is locked down.

The DNS server is running Ubuntu 8.04.3 LTS (Hardy Heron), and bind9 9.4.2.dfsg.P2.2ub.

My apologies for a very long post.  I tried to provide everything I know of that might help solve the problem up front.  If I have forgotten anything that is needed please ask and I will be happy to supply more information.

Thank you for any and all help solving this problem.

---

### Post by shortsword on 2010-01-01
I have now become aware of these lines which appear in both of the sets of log entries that I included in my original post,

```
Jan  1 00:56:26 diningroom named[5060]: /etc/bind/db.gladieuxnet:17: #diningroom.gladieuxnet: bad owner name (check-names)

```

Anybody have any idea what might be causing this error?

---

### Post by shortsword on 2010-01-01
I solved the "bad owner name" error problem.

That was caused by a badly formed line in the db.gladieuxnet file.

And, unfortunately, it was a line I purposely left out of the listing of that file in my original post.  I was not sure the line was needed and did not want to appear "too" stupid.  Big mistake.

Instead I used the wrong comment character (# instead of ;) to comment the line out and that caused the "bad owner name" error.

When I changed to a semi-colon comment character, I got a different error, No A or AAAA record for the DNS server machine.  So, the line is needed after all.

After removing the comment character, bind9 restarts without errors in the daemon.log file.

But, I still have the original problem where by, rebooting the machine causes named to listen only on localhost.

I will submit a new reply to my original post, with corrected data asking about the original problem.

---

### Post by shortsword on 2010-01-01
As I said in my previous post, I have solved the "bad owner name" problem.  But, I still have the original problem that when the server hosting bind9 is rebooted named comes up and listens only on localhost.  Only after restarting bind9 does named start listening on port 53 for its IP address.

Here is the result of the specified netstat command just after rebooting,



```
sudo netstat -aunt | grep 53

tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp6       0      0 :::53                   :::*                               

```

After executing "sudo /etc/init.d/bind9 restart" the same netstat command gives this,

```
tcp        0      0 192.168.1.102:53        0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           127.0.0.1:37367         TIME_WAIT  
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
udp        0      0 192.168.1.102:53        0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp6       0      0 :::53                   :::*                      
```         

Here is the entries from the /var/log/daemon.log applicable to named during reboot:

```
Jan  1 18:03:05 diningroom named[5448]: starting BIND 9.4.2-P2.1 -u bind
Jan  1 18:03:05 diningroom named[5448]: found 1 CPU, using 1 worker thread
Jan  1 18:03:05 diningroom named[5448]: loading configuration from '/etc/bind/named.conf'
Jan  1 18:03:05 diningroom named[5448]: listening on IPv6 interfaces, port 53
Jan  1 18:03:06 diningroom named[5448]: listening on IPv4 interface lo, 127.0.0.1#53
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: D.F.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 8.E.F.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: 9.E.F.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: A.E.F.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: automatic empty zone: B.E.F.IP6.ARPA
Jan  1 18:03:06 diningroom named[5448]: command channel listening on 127.0.0.1#953
Jan  1 18:03:06 diningroom named[5448]: command channel listening on ::1#953
Jan  1 18:03:06 diningroom named[5448]: zone 0.in-addr.arpa/IN: loaded serial 1
Jan  1 18:03:06 diningroom named[5448]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan  1 18:03:06 diningroom named[5448]: zone 1.168.192.in-addr.arpa/IN: loaded serial 20091231
Jan  1 18:03:06 diningroom named[5448]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan  1 18:03:06 diningroom named[5448]: zone gladieuxnet/IN: loaded serial 20091231
Jan  1 18:03:06 diningroom named[5448]: zone localhost/IN: loaded serial 2
Jan  1 18:03:06 diningroom named[5448]: running
```

And these are the entries from the same log file when the "sudo /etc/init.d/bind9 restart" command is run,

```
Jan  1 18:08:44 diningroom named[5448]: shutting down: flushing changes
Jan  1 18:08:44 diningroom named[5448]: stopping command channel on 127.0.0.1#953
Jan  1 18:08:44 diningroom named[5448]: stopping command channel on ::1#953
Jan  1 18:08:44 diningroom named[5448]: no longer listening on ::#53
Jan  1 18:08:44 diningroom named[5448]: no longer listening on 127.0.0.1#53
Jan  1 18:08:44 diningroom named[5448]: exiting
Jan  1 18:08:46 diningroom named[7878]: starting BIND 9.4.2-P2.1 -u bind
Jan  1 18:08:46 diningroom named[7878]: found 1 CPU, using 1 worker thread
Jan  1 18:08:46 diningroom named[7878]: loading configuration from '/etc/bind/named.conf'
Jan  1 18:08:46 diningroom named[7878]: listening on IPv6 interfaces, port 53
Jan  1 18:08:46 diningroom named[7878]: listening on IPv4 interface lo, 127.0.0.1#53
Jan  1 18:08:46 diningroom named[7878]: listening on IPv4 interface eth0, 192.168.1.102#53
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: D.F.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 8.E.F.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: 9.E.F.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: A.E.F.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: automatic empty zone: B.E.F.IP6.ARPA
Jan  1 18:08:46 diningroom named[7878]: command channel listening on 127.0.0.1#953
Jan  1 18:08:46 diningroom named[7878]: command channel listening on ::1#953
Jan  1 18:08:46 diningroom named[7878]: zone 0.in-addr.arpa/IN: loaded serial 1
Jan  1 18:08:46 diningroom named[7878]: zone 127.in-addr.arpa/IN: loaded serial 1
Jan  1 18:08:46 diningroom named[7878]: zone 1.168.192.in-addr.arpa/IN: loaded serial 20091231
Jan  1 18:08:46 diningroom named[7878]: zone 255.in-addr.arpa/IN: loaded serial 1
Jan  1 18:08:46 diningroom named[7878]: zone gladieuxnet/IN: loaded serial 20091231
Jan  1 18:08:46 diningroom named[7878]: zone localhost/IN: loaded serial 2
Jan  1 18:08:46 diningroom named[7878]: running
```

Note that in the first set of log entries and the first netstat output, named listened on both ports 53 and 953 but only for the localhost address. In the second set of log entiries and netstat output, named listens on port 53 on both localhost and on 192.168.1.102 (the IP address of the machine running bind/named) and listens on port 953 only on localhost.

Here is the contents of my /etc/bind/named.conf file,

```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";
```

Of the files mentioned therein, the only one that I have changed from the original installation version is /etc/bind/named.conf.local. That file contains,

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "gladieuxnet" {
	type master;
	file "/etc/bind/db.gladieuxnet";
};

zone "1.168.192.in-addr.arpa" {
	type master;
	notify no;
	file "/etc/bind/db.192";
};

```

The /etc/bind/db.gladieuxnet file contains,

```
;
; BIND data file for gladieunet
;
$TTL	604800
@	IN	SOA	diningroom.gladieuxnet. sshortsword.cox.net. (
		       20091231		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@			IN	NS	diningroom.gladieuxnet.
@			IN	A	192.168.1.102
ns			IN	A	192.168.1.102
joshuaroom		IN	A	192.168.1.100
laptop1			IN	A	192.168.1.101
diningroom		IN	A	192.168.1.102
heatherroom		IN	A	192.168.1.103
diningroomWinMedia	IN	A	192.168.1.105
joshualaptop		IN	A	192.168.1.106

```

And the /etc/bind/db.192 file contains,

```
;
; BIND reverse data file for gladieuxnet
;
$TTL	604800
@	IN	SOA	gladieuxnet. sshortsword.cox.net. (
		       20091231		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	gladieuxnet.
1.0.0	IN	PTR	gladieuxnet.
```

My /etc/hosts file contains,

```
127.0.0.1 localhost
192.168.1.102 diningroom.gladieuxnet DININGROOM diningroom
192.168.1.103 heatherroom.gladieuxnet HEATHERROOM heatherroom
192.168.1.100 joshuaroom.gladieuxnet JOSHUAROOM joshuaroom
192.168.1.105 diningroomWinMedia.gladieuxnet DININGROOMWINMEDIA diningroommedia
192.168.1.101 laptop1.gladieuxnet LAPTOP1 laptop1
192.168.1.106 joshualaptop.gladieuxnet JOSHUALAPTOP joshualaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

This hosts file contents was generated by some software. This is readable, but the file was much more readable (though containing similar information) before I started messing with bind9.

My /etc/resolv.conf file contains,

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5007
#
### END INFO

search oc.cox.net


nameserver 192.168.1.102
nameserver 68.105.28.12
nameserver 68.105.29.12

```

My /etc/host.conf file contains,

```
# The "order" line is only used by old versions of the C library.
order bind,hosts
multi on
```

This file has been changed since I began the bind9 exercise, the order value was previously hosts,bind.

Finally, my whole LAN is sitting behind a NAT router which has NO open ports. All "servers" on my LAN can be accessed ONLY from the LAN, as far as I know. The router is set to feed all LAN machines my local DNS server's IP address as the primary DNS server and the first two of my ISP's DNS servers as the secondary and tertiary DNS servers. See the results of this in the contents of the generated /etc/resolv.conf file above. And all machines both Windows and Linux are getting those three DNS addresses from the router.

The DNS server (192.168.1.102) has a firewall rule allowing everone on the LAN to access port 53. It also has rules allowing only known LAN machines to access ssh (port 22) and ipp (port 631). Everything else on the machine is locked down.

The DNS server is running Ubuntu 8.04.3 LTS (Hardy Heron), and bind9 9.4.2.dfsg.P2.2ub.

My apologies for a very long post. I tried to provide everything I know of that might help solve the problem up front. If I have forgotten anything that is needed please ask and I will be happy to supply more information.

Thank you for any and all help solving this problem.

---

### Post by dcstar on 2010-01-01
> **shortsword said:**
> As I said in my previous post, I have solved the "bad owner name" problem.  But, I still have the original problem that when the server hosting bind9 is rebooted named comes up and listens only on localhost.
..........

If you have installed a Desktop system that uses Network Manager, then you will only get networking enabled after GUI login.

---

### Post by shortsword on 2010-01-02
David,

Both Gnome and KDE are installed.  Your criteria is met.

You may be able to convince me that there is something hindering networking during the period in which bind9 is starting during bootup.

However, I am not convinced that the explanation you gave explains the situation.  Here's why.

Experiment performed to prove David's hypothesis,

[LIST=1]
[*]Reboot the machine on which bind9 is running.
[*]When login screen appears, do not log in.
[*]Go to another machine on the LAN and login.  (By the way, I still have visual of the other machine's flat panel display and keyboard.  So, even if someone else in the house were still up, which they aren't, I would know if someone else logged in to it.)
[*]ping the machine running bind9 using its hostname.  UNSUCCESSFUL.
[*]ssh to the machine running bind9 using its hostname.  UNSUCCESSFUL.
[*]ping the machine running bind9 using its IP address.  SUCCESSFUL.
[*]ssh to the machine running bind9 using its IP address. SUCCESSFUL.
[*]ls the /home/<my username>/Pictures folder.  (There are different contents in this folder on each of the two machines in question.)
[*]The ls results are those for the machine on which bind9 is running.
[/LIST]

So, networking is running fine on the bind9 machine, without anyone being logged in to it except through ssh.

---

### Post by slakkie on 2010-01-02
Can we have a look at your named.conf.options file?

And can you run the following? *update-rc.d -n -f bind9 remove*. Don't worry, you don't have to be root for this and we don't actually remove it (-n).

---

### Post by shortsword on 2010-01-02
slakkie,

I'm sorry.  I should have included the named.conf.options file in my original (and amended) post but left it out.  It contains this,

```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
	 	68.105.28.12;
	 	68.105.29.12;
	 	68.105.28.11;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on { any; };
	listen-on-v6 { any; };
};
```

The next to the last line in the options section (e.g., listen-on { any }; ), was not in the file originally.  I added that line in an attempt to fix the reboot problem.  It does not seem to have had any affect, and I have not yet deleted it.

The only other change I have made to the file is to add the three IP addresses of my ISP's DNS servers to the forwarders section.

The results of running the *update-rc.d -n -f bind9 remove* command are,

```
 Removing any system startup links for /etc/init.d/bind9 ...
   /etc/rc0.d/K85bind9
   /etc/rc1.d/K85bind9
   /etc/rc2.d/S15bind9
   /etc/rc3.d/S15bind9
   /etc/rc4.d/S15bind9
   /etc/rc5.d/S15bind9
   /etc/rc6.d/K85bind9
```

---

### Post by slakkie on 2010-01-02
Could you set *listen-on-v6* to *none*? Perhaps also check the options in */etc/default/bind9*, I know I had problems with bind when using ipv6, so I added changed the startup options to *OPTIONS="-u bind -4"* to force ipv4. I don't know if it will help you, but you can give it a shot...

---

### Post by shortsword on 2010-01-02
My rebooting problem seems to have been solved.

I stumbled across the answer while researching another problem, which still remains unsolved.

The /etc/network/interfaces file contained an entry for the loopback interface but not one for the ethernet card.

I added these lines to that file,

```
auto eth0
iface eth0 inet dhcp
```

Since there was no previous entry for eth0 I could not simply 

```
ifdown eth0
```

So I had to reboot.  When the system came back up it was listening on port 53 on eth0 as well as on the loopback.

Presumably the eth0 interface was being started previously by some other mechanism.  As I said in an earlier post, the networking was up on this machine, even without a user logging in.

Does anybody know if the lines that I added to the interfaces file might have some deletirious debian/ubuntu affect?

---

### Post by slakkie on 2010-01-02
> **shortsword said:**
> 
Does anybody know if the lines that I added to the interfaces file might have some deletirious debian/ubuntu affect?

Nope :) See also: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

---

### Post by dcstar on 2010-01-02
> **shortsword said:**
> My rebooting problem seems to have been solved.

I stumbled across the answer while researching another problem, which still remains unsolved.

**The /etc/network/interfaces file contained an entry for the loopback interface but not one for the ethernet card.**

I added these lines to that file,

```
auto eth0
iface eth0 inet dhcp
```

Since there was no previous entry for eth0 I could not simply 

```
ifdown eth0
```

So I had to reboot.  When the system came back up it was listening on port 53 on eth0 as well as on the loopback.

Presumably the eth0 interface was being started previously by some other mechanism. ** As I said in an earlier post, the networking was up on this machine, even without a user logging in.**


Maybe, maybe also the other machine you used to test the ping already had the ARP of that server's ethernet card cached so even though it would respond to an IP ping, it was really just luck because the server LAN card was just alive in a basic mode.

Any system using Network Manager will only configure the networking when the GUI is loaded, all other "traditional" systems actually populate the /etc/network/interfaces which is read at boot-up and fully enables networking at that time.

I install gnome-network-admin, that fully configures the /etc/network/interfaces file, and then I remove the execrable network-manager package because I don't like systems that do not have fully operational networking at boot-up.

---

