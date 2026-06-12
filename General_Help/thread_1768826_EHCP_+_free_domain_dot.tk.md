---
title: "EHCP + free domain dot.tk"
date: 2011-05-27
forum: General Help
---

### Post by smithmario on 2011-05-27
Dear all,
I need help to make my free domain from dot.tk to work on my local ubuntu server.
my topologi 
----------------------------hotspot
------------------------------|
IP public(bridge)--------mikrotik--------client
------------------------------|
------------------------------|
-----------[B]Ubuntu server (Lusca proxy, unbound, bind, EHCP, webmin, apache2 mysql)

[/B]4 X chain=dstnat action=dst-nat to-addresses=192.168.0.2 to-ports=80 protocol=tcp dst-address=325.xxxx(ip public)  dst-port=80

I was make free domain from dot.tk
EHCP setting
add dns only hosting
Normally, do not write www. only yourdom.com forexample,
Enter serverip where domain is hosted actually
domainname : mylapo.tk
serverip         : ip public

I only have 1 ip public, can I do this for free domain on dot.tk?

Edit dns template for this domain
$TTL    86400
@       IN      SOA     ns.mylapo.tk. {dnsemail} (
                        {serial}     ; Serial, this is [www.ehcp.net]("http://www.ehcp.net/") dns zone template file.. 
                        10800   ; Refresh
                        1200     ; Retry
                        86400  ; Expire
                        86400 ) ; Minimum

mylapo.tk.           IN NS   ns.mylapo.tk.
ns.mylapo.tk.        IN A    {dnsip}
ns1.mylapo.tk.       IN A    {dnsip}
ns2.mylapo.tk.       IN A    {dnsip}
dns.mylapo.tk.       IN A    {dnsip}
dns1.mylapo.tk.       IN A    {dnsip}
dns2.mylapo.tk.       IN A    {dnsip}
mylapo.tk.           IN A    {webip}
mail.mylapo.tk.      IN A    {mailip}
smtp.mylapo.tk.   IN A    {webip}
imap.mylapo.tk.   IN A    {webip}
webmail.mylapo.tk.   IN A    {webip}
ftp.mylapo.tk.       IN CNAME        mylapo.tk.
[www.mylapo.tk.]("http://www.mylapo.tk/")       IN CNAME        mylapo.tk.
mylapo.tk.           IN MX  10 mail.mylapo.tk.
mylapo.tk.           IN TXT "v=spf1 a mx"

{customdns}

*                       IN A    {webip}

---------------------------
[http://www.dot.tk]("http://www.dot.tk/")
Use my own DNS Services
Use Custom DNS Service

ns1.mylapo.tk.       IN A    {dnsip}
ns2.mylapo.tk.       IN A    {dnsip}

Nameserver----------IP Address
ns1.mylapo.tk------n/a or ip public ?
ns2.mylapo.tk------n/a or ip public ?

Am I  wrong about this setting ?
How to make my free domain from dot.tk work on my local ubuntu webserver ?
Thanks for help

---

