---
title: "Can't Get Squid To Start, Squid.Conf Attached"
date: 2011-06-26
forum: General Help
---

### Post by terrykiwi83 on 2011-06-26
Pulling my hair out here, squid just doesn't want to run at all.

When I invoke the sudo service squid start 

It says 

```

Squid Start/Running, Process 305080

```

When I check running process nothing is there, and when I look at the status of the squid server via webmin it also says 'down'

My Squid.conf is below.

```

 http_port 3128
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
cache_mem 200 MB
 cache_swap_low 90
 cache_swap_high 95
 maximum_object_size 500 KB
 minimum_object_size 10 KB
 maximum_object_size_in_memory 500 KB
 cache_dir ufs /squid/cache 20000 16 256
 cache_access_log /squid/logs/access.log
cache_log /squid/logs/cache.log
emulate_httpd_log on
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
visible_hostname roswell

 http_access allow all
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
cache_mgrt root 
 httpd_accel_port 80
 httpd_accel_host virtual
 httpd_accel_with_proxy on
 httpd_accel_uses_host_header on
coredump_dir /var/spool/squid

```

Specs. Ubuntu Server 11.04 32bit

---

### Post by SeijiSensei on 2011-06-26
Logs are your friends.  What do you see in /var/log/squid?

---

### Post by terrykiwi83 on 2011-06-26
In there I see access.log cache.log store.log

is there anything in particular am looking for, had a look at cache.log and can't see any errors.

---

### Post by terrykiwi83 on 2011-06-26
bump, there has to be something wrong with the config file I just can't figure out what.

---

