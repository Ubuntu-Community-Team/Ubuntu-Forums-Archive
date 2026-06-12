---
title: "Unable to view PHP pages from remote site"
date: 2009-12-31
forum: General Help
---

### Post by Jibadee on 2009-12-31
Hello

I have a 9.10 web server running an intranet page on our LAN, we have just opened a new office which is connected by an IPSEC VPN.

From the new office I can only view HTML and not PHP pages.

Could anyone point me in the right direction?

Many thanks

Andy

---

### Post by Wardje on 2009-12-31
Do you have Apache (or lighttpd) and PHP installed and set up?
[https://help.ubuntu.com/9.10/serverguide/C/web-servers.html](https://help.ubuntu.com/9.10/serverguide/C/web-servers.html)

---

### Post by Jibadee on 2010-01-05
Hello

I have Apache2 and php all setup and working for the last 18 months or so, the problem has only occured since opening the new branch and we are connecting from a different subnet.

Web server address is 172.26.0.41 and the new remote office range is 172.24.0.0

---

### Post by Jibadee on 2010-01-05
I have just installed Xampp on my Windows7 machine and everything is working perfectly. 

:S

---

### Post by Jibadee on 2010-01-05
obiously dont want to go live on a vindows box #-o

---

### Post by Jibadee on 2010-01-06
Anyone? :KS

---

### Post by Wardje on 2010-01-07
Sounds more like an apache settings problem then, but am afraid nothing comes to mind :(
Perhaps try asking in the part of these forums concerning the server edition and otherwise checking apache forums:confused:

---

### Post by Jibadee on 2010-01-22
Hello,


Ive started to see this error in the logs when attempting to connect from our subnet

(104)Connection reset by peer: core_output_filter: writing data to the network

(70007)The timeout specified has expired: core_output_filter: writing data to the network

---

### Post by Jibadee on 2010-01-25
Anyone?   :confused::confused::confused:

---

### Post by bubblehead74 on 2010-01-27
This is what I found:

Invalid argument: core_output_filter: writing data to the network

Apache uses the sendfile syscall on platforms where it is available in order to speed     sending of responses. Unfortunately, on some systems, Apache will detect the presence of sendfile at compile-time, even when it does not work properly. This happens most frequently when using network or other non-standard file-system.
   Symptoms of this problem include the above message in the error log and zero-length  responses to non-zero-sized files. The problem generally occurs only for static files, since dynamic content usually does not make use of sendfile.
To fix this problem, simply use the EnableSendfile directive to disable sendfile for all or part of your server. Also see the EnableMMAP, which can help with similar problems.

---

