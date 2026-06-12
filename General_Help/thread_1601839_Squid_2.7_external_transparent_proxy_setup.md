---
title: "Squid 2.7 external transparent proxy setup"
date: 2010-10-20
forum: General Help
---

### Post by aktiwers on 2010-10-20
Hi all,

Okay so I have been trying to setup Squid 2.7 as an external transparent proxy on my web-server. I have appache2 running on the server with some sites.

I have added the following to /etc/squid/squid.conf
```

httpd_accel_port 8080
http_port 3128 transparent
http_access allow all
httpd_accel_with_proxy on
httpd_accel_uses_host_header on

``` 

And run this in IP tables (to redirect all traffic to port 8080?)
```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 8080 -j REDIRECT --to-port 3128
```

Since using --dport 80 as every guide seams to suggest, breaks my appache2 or the sites it is hosting gets offline.

  tail -f /var/log/squid/access.log gives me:
```
1287498053.141      2 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498053.823      1 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498054.067      2 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498054.282      1 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498054.506      1 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498055.501      1 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498056.338     14 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498058.160      2 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498075.561      1 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html
1287498076.308      2 144.182.192.58 TCP_DENIED/400 1873 GET error:invalid-request - NONE/- text/html

```

And Firefox with Tor tells me that the Page has been denied, contact webmaster (my self).

I'm a noob at squid and would love to get a helping eye on this.

Cheers

Oh yea.. it should not matter but I am in Debian.

---

