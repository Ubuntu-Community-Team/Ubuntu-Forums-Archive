---
title: "Ubuntu masquerade and squid"
date: 2011-08-18
forum: General Help
---

### Post by Kyaw Kyaw on 2011-08-18
Hello,

I have issues that my masquerade configuration and squid do not work  properly. I am very beginner, please help the following error message on  client workstation.

 **[COLOR=SeaGreen]ERROR[/COLOR]**

 **[COLOR=SeaGreen]The requested URL could not be retrieved[/COLOR]**

 
       [COLOR=SeaGreen]The following error was encountered while trying to retrieve the URL: [http://www.google.com/](http://www.google.com/)[/COLOR][INDENT] [COLOR=SeaGreen]**Access Denied.**[/COLOR]
 [/INDENT][COLOR=SeaGreen]Access  control configuration prevents your request from being allowed at this  time. Please contact your service provider if you feel this is  incorrect.[/COLOR]
  [COLOR=SeaGreen]Your cache administrator is Your_Squid_mgr.[/COLOR]
 [COLOR=SeaGreen]
  [/COLOR] 
       [COLOR=SeaGreen]Generated Thu, 18 Aug 2011 03:13:18 GMT by SquidProx02 (squid/2.7.STABLE9)[/COLOR]
 

Please check my configuration as below:
I would highly appreciated pls point me out, my wrong and missing
[COLOR=Blue][SIZE=4]
/etc/squid/squid.conf
  [/SIZE][/COLOR]
"cache_mgr Your_Squid_mgr 
forwarded_for off 
visible_hostname SquidProx02 
#cache_effective_user Your_user 
cache_effective_user squid 
#cache_effective_group Your_user 
cache_effective_group squid 
  
cache_mem 200 MB 
#/media/Data/ is my mounted drive name, change it with yours mounted drive name. 
#cache_dir ufs /media/DATA/squid2/cache0 500 16 256  
#cache_dir ufs /media/DATA/squid2/cache1 500 16 256 
#cache_dir ufs /media/DATA/squid2/cache2 500 16 256 
#cache_dir ufs /media/DATA/squid2/cache3 500 16 256 
#coredump_dir /media/DATA/squid2/ 
 
cache_dir ufs /usr/squid/squid1 1000 16 256  
cache_dir ufs /usr/squid/squid2 1000 16 256  
cache_dir ufs /usr/squid/squid3 1000 16 256  
cache_dir ufs /usr/squid/squid4 1000 16 256  
cache_dir ufs /usr/squid/squid5 1000 16 256  
cache_dir ufs /usr/squid/squid6 1000 16 256  
cache_dir ufs /usr/squid/squid7 1000 16 256  
cache_dir ufs /usr/squid/squid8 1000 16 256  
cache_dir ufs /usr/squid/squid9 1000 16 256  
cache_dir ufs /usr/squid/squid10 1000 16 256  
coredump_dir /usr/squid/ 
  
logformat combined %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st "%{Referer}>h" "%{User-Agent}>h" %Ss:%Sh 
access_log /usr/squid/access.log squid 
cache_store_log none 
cache_log /usr/squid/cache.log 
  
#acl apache rep_header Server ^Apache 
#broken_vary_encoding allow apache 
maximum_object_size 1024 KB 
maximum_object_size_in_memory 128 KB 
  
#negative_ttl 2 minute 
#half_closed_clients off 
ipcache_size 4096 
ipcache_low 95 
ipcache_high 100 
  
memory_pools off 
reload_into_ims ON 
pipeline_prefetch ON 
  
 
acl all src 0.0.0.0/0.0.0.0 
acl internal_network src 192.168.1.0/24 
#acl users proxy_auth REQUIRED 
#acl manager proto cache_object 
acl localhost src 127.0.0.1/255.255.255.255 
#acl to_localhost dst 127.0.0.0/8 
#acl SSL_ports port 443 563 # https, snews 
#acl SSL_ports port 873 # rsync 
acl Safe_ports port 80 # http 
#acl Safe_ports port 21 # ftp 
acl Safe_ports port 443 563 # https, snews 
#acl Safe_ports port 70 # gopher 
#acl Safe_ports port 210 # wais 
acl Safe_ports port 1025-65535 # unregistered ports 
#acl Safe_ports port 280 # http-mgmt 
#acl Safe_ports port 488 # gss-http 
#acl Safe_ports port 591 # filemaker 
#acl Safe_ports port 777 # multiling http 
#acl Safe_ports port 631 # cups 
#acl Safe_ports port 873 # rsync 
#acl Safe_ports port 901 # SWAT 
# acl sectionx proxy_auth REQUIRED 
#acl purge method PURGE 
#acl CONNECT method CONNECT 
 
#http_access allow manager localhost 
#http_access allow users 
http_access allow internal_network 
#http_access deny manager 
#http_access allow purge localhost 
#http_access deny purge 
#http_access deny !Safe_ports 
#http_access deny CONNECT !SSL_ports 
http_access allow localhost 
#http_access deny all 
 
#icp_access allow all 
 
cache_swap_high 99 
cache_swap_low 95 
 
http_port 3128 transparent 
acl our_networks src 192.168.1.0/24 
acl localnet src 0.0.0.0/255.255.255.255 
http_access allow localnet 
http_access allow our_networks 
 
#always_direct deny ALL 
 
cache_peer 141.220.1.17 parent 3128 0  "


[SIZE=4][COLOR=Blue]/etc/iptables.rules[/COLOR][/SIZE]

"  # * mangle
# : PREROUTING ACCEPT [405:40408]
# : INPUT ACCEPT [405:40408]
# : FORWARD ACCEPT [0:0]
#  : OUTPUT ACCEPT [816:69917]
 # : POSTROUTING ACCEPT [816:69917]
# COMMIT

#*nat
# REROUTING ACCEPT [0:0]
#: OUTPUT ACCEPT [0:0]
# OSTROUTING ACCEPT [0:0]
#-A POSTROUTING -o eth0 -j MASQUERADE

-A PREROUTING –i eth0:1 –p tcp –m tcp –dport 80 –j DNAT –to-destination 192.168.1.252:3128
-A PREROUTING –i eth0:1 –p tcp –m tcp –dport 80 –j REDIRECT –to-ports 3128
-A POSTROUTING –s 192.168.1.0/24 –o eth0 –j MASQUERADE
COMMIT

#*filter
#:FORWARD DROP [0:0]
#:INPUT ACCEPT [0:0]
#:OUTPUT ACCEPT [0:0]
-A INPUT  –m state –i eth0:1 –state REALATED,ESTABLISHED –j ACCEPT
-A INPUT  –i lo –j ACCEPT
-A INPUT  eth0:1 –j ACCEPT
# permit ssh using putty
-A INPUT  –p tcp –m tcp –dport 22 –j ACCEPT 
# permit ssh using putty permit webmin access
-A INPUT  –p tcp –m tcp –dport 10000 –j ACCEPT 
# permit ssh using putty permit webmin access
-A INPUT  –j LOG
-A INPUT  –j DROP
-A FORWARD  –i eth0:1 –j ACCEPT
-A OUTPUT  –o lo –j ACCEPT
-A OUTPUT  –o eth0:1 –j ACCEPT
-A FOWARD  –o eth0:1 –j ACCEPT
-A FORWARD  –s 192.168.1.0/24 –o eth0 –j ACCEPT
-A FORWARD  –d 192.168.1.0/24 –m state –state ESTABLISHED,REALTED –I eth0 –j ACCEPT
COMMIT

:INPUT ACCEPT [1565:148315]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [2293:200061]

-A INPUT –i lo –j ACCEPT
-A INPUT –m state –i eth0:1 –state REALATED,ESTABLISHED –j ACCEPT
-A INPUT eth0:1 –j ACCEPT
-A INPUT –p tcp –m tcp –dport 22 –j ACCEPT # permit ssh using putty
-A INPUT –p tcp –m tcp –dport 10000 –j ACCEPT # permit webmin access
-A INPUT –j LOG
-A INPUT –j DROP
-A FORWARD –i eth0:1 –j ACCEPT
-A OUTPUT –o lo –j ACCEPT
-A OUTPUT –o eth0:1 –j ACCEPT
-A FOWARD –o eth0:1 –j ACCEPT
-A FORWARD –s 192.168.1.0/24 –o eth0 –j ACCEPT
-A FORWARD –d 192.168.1.0/24 –m state –state ESTABLISHED,REALTED –I eth0 –j ACCEPT

COMMIT

#-A POSTROUTING -o eth0 -j MASQUERADE
#*filter
#:INPUT ACCEPT [1565:148315]
#:FORWARD DROP [0:0]
#:OUTPUT ACCEPT [2293:200061]
# -A FORWARD -o eth0 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 
# -A FORWARD -i eht0 -m state --state RELATED,ESTABLISHED -j ACCEPT      "

[SIZE=4][COLOR=Blue]
/etc/sysctl.conf[/COLOR][/SIZE]

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
net.ipv4.ip_forward=1

Thank you very much.

---

