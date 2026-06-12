---
title: "How to open ports in Firehol for PS3 Media Server"
date: 2010-11-25
forum: General Help
---

### Post by Jags_FL on 2010-11-25
I'm trying to open ports in Firehol for PS3 Media Server. So far I've tried all options from this [**Firehol "adding services" page**]("http://firehol.sourceforge.net/adding.html") and none of 'em is working for me. 

Here are the IPs:

PC : 192.168.1.139
PS3 : 192.168.1.138
TV: 192.168.1.131
PS3 Media Server Port: 35355

If a port can be opened for specific IPs then I would like to open one for only 2 IPs.

Firehol configuration:

version 5
# Accept all client traffic on any interface
interface any internet
protection strong
policy drop
server "icmp ping ICMP ssh" accept
client all accept

Also what would happen if I remove "server "icmp ping ICMP ssh" accept" line? I've copied the whole thing [from this HowtoForge page]("http://www.howtoforge.com/setting-up-an-iptables-firewall-with-firehol-on-ubuntu").

Thanks a million in advance!

---

### Post by Jags_FL on 2010-11-25
anyone on Firewall/Firehol ?? Thanks!

---

### Post by Gunman1982 on 2010-11-25
Haven't used firehol and probably never will so would I write is without warranty.
I would say that the lines can be interpreted as such:

policy drop (self explanatory, drop all if not defined otherwise)
server "icmp ping ICMP ssh" accept (icmp: accept connection using the icmp protocol which means errors like destination unreachable, ping: shouldn't benecessary since ping is using icmp, ICMP: don't know why again ICMP in capital letters, would delete it, ssh: accept connections to the ssh server, can probably be removed if you don't have a ssh server installed)
client all accept (accept all outbound traffic meaning: you->outside)

so the line you want to change would be the  'server "icmp ping ICMP ssh" accept'
Try it with: 'server "icmp 35355" accept' to accept connections to the pms from all outside or if you want to restrict it to those two addresses I would try this:
```

interface any internet src 192.168.1.138
protection strong
policy drop
server "35355" accept
client all accept

interface any internet src 192.168.1.131
protection strong
policy drop
server "35355" accept
client all accept

interface any internet
protection strong
policy drop
server "icmp" accept
client all accept

```

greetz
Gunman

PS: Btw seems to be a little more informative tutorial: [http://firehol.sourceforge.net/tutorial.html]("http://firehol.sourceforge.net/tutorial.html")

---

### Post by Jags_FL on 2010-11-25
@ Gunman1982

many thanks for the reply. When I changed as you suggested and tried to start Firehol, I'm getting following errors:


$ sudo /etc/init.d/firehol start
 * Starting Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana.sh script to generate this file.

/sbin/firehol: line 5352: rules_35355: command not found

--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Running complex rules function rules_35355() for server '35355'
WHY    : There is no service '35355' defined.
COMMAND: server 35355 accept 
SOURCE : line 30 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Creating chain 'in_internet' under 'INPUT' in table 'filter'
WHY    : Chain 'in_internet' already exists.
COMMAND: \(unset\) 
SOURCE : line 33 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Creating chain 'pr_internet_fragments' under 'in_internet' in table 'filter'
WHY    : Chain 'pr_internet_fragments' already exists.
COMMAND: protection fragments\ new-tcp-w/o-syn\ icmp-floods\ syn-floods\ malformed-xmas\ malformed-null\ malformed-bad\ invalid 100/s 50 
SOURCE : line 34 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 4
WHAT   : Creating chain 'in_internet_35355_s1' under 'in_internet' in table 'filter'
WHY    : Chain 'in_internet_35355_s1' already exists.
COMMAND: server 35355 accept 
SOURCE : line 36 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 5
WHAT   : Creating chain 'in_internet_all_c2' under 'in_internet' in table 'filter'
WHY    : Chain 'in_internet_all_c2' already exists.
COMMAND: client all accept 
SOURCE : line 37 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 6
WHAT   : Creating chain 'in_internet' under 'INPUT' in table 'filter'
WHY    : Chain 'in_internet' already exists.
COMMAND: \(unset\) 
SOURCE : line 39 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 7
WHAT   : Creating chain 'pr_internet_fragments' under 'in_internet' in table 'filter'
WHY    : Chain 'pr_internet_fragments' already exists.
COMMAND: protection fragments\ new-tcp-w/o-syn\ icmp-floods\ syn-floods\ malformed-xmas\ malformed-null\ malformed-bad\ invalid 100/s 50 
SOURCE : line 40 of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 8
WHAT   : Creating chain 'in_internet_all_c2' under 'in_internet' in table 'filter'
WHY    : Chain 'in_internet_all_c2' already exists.
COMMAND: client all accept 
SOURCE : line 43 of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.            [fail]

---

### Post by Jags_FL on 2010-12-20
anyone on how to open ports in Firehol ? Thanks.

---

### Post by Jags_FL on 2010-12-22
anyone?

---

