---
title: "squid.conf problem ... what s wrong?"
date: 2006-03-07
forum: General Help
---

### Post by hudanet2005 on 2006-03-07
below my squid.conf:


http_port 127.0.0.1:3128

icp_port 0

cache_mem 32 MB

cache_dir ufs /var/spool/squid 6000 14 256

cache_access_log /var/log/squid/access.log

cache_store_log none

negative_ttl 1 minutes

cache_effective_user proxy

cache_effective_group proxy

maximum_object_size 1024 KB

minimum_object_size 4 KB

ftp_user [email]user@huda.net[/email]

redirect_program /usr/bin/adzapper

cache_mgr [email]bulaklarak2005@yahoo.com[/email]

acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8

acl SSL_ports port 443 563	# https, snews
acl SSL_ports port 873		# rsync
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
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

acl warnet_hudanet src 192.168.1.0/255.255.255.0

acl blokporno dstdomain &#8220;/etc/squid/urllrng&#8221;

acl blokkata url_regex -i &#8220;/etc/squid/katalrng&#8221;

http_access allow warnet_hudanet

http_access deny blokporno

http_access deny blokkata 

http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports

http_access allow localhost

http_access deny all

http_reply_access allow all

icp_access allow all

coredump_dir /var/spool/squid

visible_hostname [www.bulaklarak.net](www.bulaklarak.net)

half_closed_clients off

cache_swap_high 100%

cache_swap_low 80% 

httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on
httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on


i did sudo squid -z
there is no error message
but my clients couldn't connect to the proxy

is there something wrong with my squid.conf?
i m in the dark right now
...  i need a light

would u please help me out of this deep darkness?

---

