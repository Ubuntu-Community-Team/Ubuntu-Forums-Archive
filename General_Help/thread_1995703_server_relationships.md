---
title: "server relationships"
date: 2012-06-03
forum: General Help
---

### Post by rbcssn on 2012-06-03
Hi there, ):P
how can you tell what services a server is dependent on? For example, web server depends on DNS. I use nmap or netstat to see what services are run on a machine, but what about their dependent services? Hope this makes sense.

---

### Post by maverickaddicted on 2012-06-04
> **rbcssn said:**
> Hi there, ):P
how can you tell what services a server is dependent on? For example, web server depends on DNS. I use nmap or netstat to see what services are run on a machine, but what about their dependent services? Hope this makes sense.
I don't know this will help you or not, but worth a try

[http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html](http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html)

Following are the features -

* Monitoring modes - active, passive or manual
* Start, stop and restart of programs
* Group and manage groups of programs
* Process dependency definition
* Logging to syslog or own logfile
* Configuration - comprehensive controlfile
* Runtime and TCP/IP port checking (tcp and udp)
* SSL support for port checking
* Unix domain socket checking
* Process status and process timeout
* Process cpu usage
* Process memory usage
* Process zombie check
* Check the systems load average
* Check a file or directory timestamp
* Alert, stop or restart a process based on its characteristics
* MD5 checksum for programs started and stopped by monit
* Alert notification for program timeout, restart, checksum, stop resource and timestamp error
* Flexible and customizable email alert messages
* Protocol verification. HTTP, FTP, SMTP, POP, IMAP, NNTP, SSH, DWP,LDAPv2 and LDAPv3
* An http interface with optional SSL support to make monit accessible from a webbrowser

---

### Post by Habitual on 2012-06-04
> **rbcssn said:**
> ...For example, web server depends on DNS....

Linux services either start successfully (0) or they don't (1)
One does not depend on the other to start successfully. 

If DNS did NOT start, apache still could start (but most likely just serve local pages)
If apache did NOT start and DNS did, then I'd suppose NO content and I'd have to check the logs.

"Service dependency" makes me think of Windows.
Can you cite a valid or realistic example of your inquiry?

Thank You.
Subscribed with interest...

---

### Post by rbcssn on 2012-06-05
Thanks! By dependencies I mean one thing (service) depending on another to work, for example the Wiki depending on a web server, Nagios depending on a web server and a user logging in depending on NIS or LDAP.  It's in relation to system discovery. What commands would I use to find out what a server is depending on? Would it be "netstat -tulpn" to see in the foreign address column what other servers are connected?

---

### Post by bab1 on 2012-06-06
> **rbcssn said:**
> Thanks! By dependencies I mean one thing (service) depending on another to work, for example the Wiki depending on a web server, Nagios depending on a web server and a user logging in depending on NIS or LDAP.  It's in relation to system discovery. What commands would I use to find out what a server is depending on? Would it be "netstat -tulpn" to see in the foreign address column what other servers are connected?

There are servers (services) and there are clients in a network.  Most servers are not dependant on other servers to function.  But where there are interdependencies, it might be good to look at these few on a case by case basis.

For example, a webserver (i.e httpd) is not truly dependant on any other services to function, but several servers enhance it's availability and usability.  DNS maps IP addresses to  FQDN.  The database mySQL (mysqld) provides backend database services for the webserver, but neither are *required * services in the strictest sense.

You need to know what you have (or need) to understand what to monitor.  In a typical LAN there usually are DHCP, DNS and HTTP servers.  Everything else is extra.  Maybe a list of standard TCP ports will help you put together a list of servers (services) you are interested in.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers").

---

