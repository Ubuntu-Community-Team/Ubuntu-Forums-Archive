---
title: "Webmin Bind9 DNS"
date: 2012-07-07
forum: General Help
---

### Post by phpkid on 2012-07-07
I need help setting up the Bind DNS is this right

i repleace my website with "mywebsite.com"

is this right im i suppose to use the lan ip address
please help 

$ttl 38400
mywebsite.com.	  IN	SOA	mywebsite.com. 
hostmaster.mywebsite.com. (
			1341713681
			10800
			3600
			604800
			38400 )
mywebsite.com.	  IN	  NS	  mywebsite.com.
mywebsite.com.	  IN	  A	  192.168.1.3
[www.mywebsite.com](www.mywebsite.com).	  IN	  A	  192.168.1.3
ns1.mywebsite.com.	  IN	  A	  192.168.1.3
ns2.mywebsite.com.	  IN	  A	  192.168.1.3
mywebsite.com.	  IN	  NS	  ns1.mywebsite.com.
mywebsite.com.	  IN	  NS	  ns2.mywebsite.com.

---

### Post by phpkid on 2012-07-14
Can anyone with more experience tell me what to do

---

