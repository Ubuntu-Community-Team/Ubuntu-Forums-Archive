---
title: "SSH after changing the hostname"
date: 2010-05-14
forum: General Help
---

### Post by tom.swartz07 on 2010-05-14
Hi All,

I just have a simple question. When I installed Lucid a few weeks ago, I didnt feel very inspired, and thus left the host name at default. 

I just changed the hostname today, and I discovered that I can no longer resolve the host for ssh connections to the computer....


When I changed the hostname files, I followed this guide: [http://ubuntuforums.org/showthread.php?t=774029](http://ubuntuforums.org/showthread.php?t=774029)

Is there a file that I need to change regarding SSH that has a hostname in it?

Specifically, Im trying to ssh and VNC connect to the Ubuntu box from my iPhone. I have a PuTTY client installed on it (from the app store, called iSSH) and up until now, it worked.

---

### Post by BoneKracker on 2010-05-14
What do you mean by "I can no longer resolve the host for ssh connections to the computer"?

Do you mean the resolver on remote clients is unable to get an IP address when that client attempts an ssh connection to the host on which you changed the hostname?

If that's the case, and you are using dynamic dns, reboot the machine on which you changed the hostname. (Or, if rebooting is a problem, release the dhcp lease and get a new one, and then do whatever is necessary, if anything, to refresh the upstream dns records.)

If you're not using dynamic dns, by what means have your ssh clients been resolving the hostname in the past?  static DNS? /etc/hosts?  NIS?  other?

If you had previously entered hostname-address pairs in the /etc/hosts file of various machines, you will need to update those to reflect the new hostname (on the client, not on the server -- in other words, on your iPhone).

If you're talking about your ssh daemon being unable to resolve the hostnames of connecting clients (reverse DNS lookup), as part of the authentication process, changing the hostname of the ssh host should have no bearing on that.

---

### Post by tom.swartz07 on 2010-05-14
> **BoneKracker said:**
> What do you mean by "I can no longer resolve the host for ssh connections to the computer"?

Do you mean the resolver on remote clients is unable to get an IP address when that client attempts an ssh connection to the host on which you changed the hostname?

If that's the case, and you are using dynamic dns, reboot the machine on which you changed the hostname. (Or, if rebooting is a problem, release the dhcp lease and get a new one, and then do whatever is necessary, if anything, to refresh the upstream dns records.)

If you're not using dynamic dns, by what means have your ssh clients been resolving the hostname in the past?  static DNS? /etc/hosts?  NIS?  other?

If you had previously entered hostname-address pairs in the /etc/hosts file of various machines, you will need to update those to reflect the new hostname.

If you're talking about your ssh daemon being unable to resolve the hostnames of connecting clients (reverse DNS lookup), as part of the authentication process, changing the hostname of the ssh host should have no bearing on that.

Sorry- I shouldve been more specific.

It seems as though the client (my jailbroken iPhone) cannot properly resolve the hostname from the network. I already restarted the host computer, so all of the proper settings should be updated. The app could see itself on the network, I can ssh into the iPhone and do things, but it wont resolve the proper IP to the Ubuntu Host.

The interesting part is; Im on a University network, so there are upwards of 1000 computers here: is it just the nature of the network not updating the DHCP list fast enough for the new hostname to catch?

---

### Post by tom.swartz07 on 2010-05-14
When I try to VNC from the iPhone app, the IP that hostname.local resolves to is 192.168.250.64:0 - my ACTUAL IP on the network is 192.168.255.119

I cant figure this one out....

---

### Post by CharlesA on 2010-05-14
It sounds like you are on a totally different subnet (if you are using the default subnet mask for a class C address)

How is the machine you are trying to VNC into hooked up to the internet?

---

### Post by tom.swartz07 on 2010-05-14
> **CharlesA said:**
> Are you running a local DNS server?

Nope.
DNS for my computer is mandated to use the University's servers. If we try hosting our own DNS we get access revoked. Buzzkill, man.

---

### Post by CharlesA on 2010-05-14
How is the machine connected to the internet?

---

### Post by BoneKracker on 2010-05-14
> **tom.swartz07 said:**
> When I try to VNC from the iPhone app, the IP that hostname.local resolves to is 192.168.250.64:0 - my ACTUAL IP on the network is 192.168.255.119

I cant figure this one out....

Yeah.  As I suspected.  The problem is on the iPhone side.

I'm going to assume the university is using DHCP and dynamic dns.

Maybe try shutting it (the iPhone) down and bringing it back up.

The dhcp server probably gave the linux box a new address when you changed its hostname (although those technically are supposed to be bound by MAC address and/or DUID), some servers do this.  Universities tend to have particularly dicked-up DHCP configurations, since their environment is so volatile (machines and people always coming and going).

Your iPhone may be caching the results of its previous DNS query (as a resource conservation measure).  It might need to dump that.  I don't know how to make that happen, but rebooting seems like one reasonable guess.

---

### Post by tom.swartz07 on 2010-05-14
> **CharlesA said:**
> How is the machine connected to the internet?

We connect to the local internet, which is governed by a Cisco Clean Access server, from there, the IP's of all of the machines are updated and connected to the internet.

Theyre really secretive about how they do their servers, but I know how to poke around... :P

---

### Post by BoneKracker on 2010-05-14
> **tom.swartz07 said:**
> When I try to VNC from the iPhone app, the IP that hostname.local resolves to is 192.168.250.64:0 - my ACTUAL IP on the network is 192.168.255.119

I cant figure this one out....

Oh, wait.  I see.  It may not just be a problem on the iPhone.

Try these (from your linux box):

nslookup hostname

dig hostname

whois 192.168.255.119

whois 192.168.250.64

---

### Post by CharlesA on 2010-05-14
whois and dig would help you get to the bottom of it.

What did you change the hostname to anyhow? Could there be two hosts with the same name?

---

### Post by BoneKracker on 2010-05-14
I don't know how Ubuntu handles its dhcp client configuration, but you might also want to check those settings to make sure you're not manually forcing it to still send the old hostname or manually forcing it to use a particular client identifier.

You could also just blast around the problem ineligantly by disconnecting from the network, changing host name again, spoofing a different MAC address, and reconnecting.

---

### Post by tom.swartz07 on 2010-05-15
> **CharlesA said:**
> whois and dig would help you get to the bottom of it.

What did you change the hostname to anyhow? Could there be two hosts with the same name?

haha- i seriously doubt that there is another host named tardis on the campus network. :: Pushes up nerd glasses ::

> **BoneKracker said:**
> I don't know how Ubuntu handles its dhcp client configuration, but you might also want to check those settings to make sure you're not manually forcing it to still send the old hostname or manually forcing it to use a particular client identifier.

You could also just blast around the problem ineligantly by disconnecting from the network, changing host name again, spoofing a different MAC address, and reconnecting.

Im away from my computer ATM, but as soon as i get back ill definitely poke around with whois and others. Ill let you guys know what happens!


Thanks again!

---

### Post by tom.swartz07 on 2010-05-15
Just as I suspected, whois didnt work on the local network, it just returned the error message saying that the ip range from 250.0 to 255.255 

dig returns:

```
tom@tardis:~$ dig tardis

; <<>> DiG 9.7.0-P1 <<>> tardis
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 22116
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;tardis.				IN	A

;; AUTHORITY SECTION:
.			10800	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010051501 1800 900 604800 86400

;; Query time: 80 msec
;; SERVER: 192.168.242.248#53(192.168.242.248)
;; WHEN: Sat May 15 22:12:09 2010
;; MSG SIZE  rcvd: 99

tom@tardis:~$ 

```

---

### Post by CharlesA on 2010-05-15
What about nslookup?

---

### Post by tom.swartz07 on 2010-05-15
Oops. Forgot that

```
tom@tardis:~$ nslookup tardis
Server:		192.168.242.248
Address:	192.168.242.248#53

** server can't find tardis: NXDOMAIN

tom@tardis:~$ 

```

---

### Post by CharlesA on 2010-05-15
That looks fine, since there is no domain.

What does this return:

```
hostname -f
```

---

### Post by BoneKracker on 2010-05-15
> **tom.swartz07 said:**
> When I try to VNC from the iPhone app, the IP that hostname.local resolves to is 192.168.250.64:0 - my ACTUAL IP on the network is 192.168.255.119

Earlier he referred to "hostname.local".

Are they using "local" internally as the domain name?

---

### Post by CharlesA on 2010-05-15
> **BoneKracker said:**
> Earlier he referred to "hostname.local".

Are they using "local" internally as the domain name?

I know I ran into problems when I didn't include the FQDN when changing the hostname.

I think we need to know a bit more about the network config to be on any help.

---

### Post by tom.swartz07 on 2010-05-16
Okay. I think I need to take a step back here and get everything as clear as possible so that we could work this out.

My computer is connected to a University network, governed by a Cisco clean access server. To log in, we open a browser and type user credentials. If they are valid, the MAC address is allowed to connect to the greater part of the internet. If it is not valid, you are only allowed to access the network help page.

BEFORE I changed my hostname; 
Ubuntu computer was named lucid-laptop
I was able to connect through iSSH, a port of PuTTY for the iPhone by using the following settings
    Host: lucid-laptop.local
    Port: 22

It would work fine because both the iPhone and computer were connected to the same network. Granted, I couldnt get "true" SSH because the network will not allow us to port forward.

AFTER I changed the hostname:
Ubuntu computer is named tardis
I am unable to connect via iSSH using the following settings
    Host: tardis.local
    Port: 22

The following information was asked, and I will repost it here:

```
tom@tardis:~$ nslookup tardis
Server:		192.168.242.248
Address:	192.168.242.248#53

** server can't find tardis: NXDOMAIN

tom@tardis:~$ dig tardis

; <<>> DiG 9.7.0-P1 <<>> tardis
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 27747
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;tardis.				IN	A

;; AUTHORITY SECTION:
.			10790	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010051600 1800 900 604800 86400

;; Query time: 2 msec
;; SERVER: 192.168.242.248#53(192.168.242.248)
;; WHEN: Sun May 16 13:40:25 2010
;; MSG SIZE  rcvd: 99

tom@tardis:~$ whois 192.168.255.119

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    PRIVATE-ADDRESS-CBLK-RFC1918-IANA-RESERVED
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is used as private address space.
Comment:    Addresses from this block can be used by
Comment:    anyone without any need to coordinate with
Comment:    IANA or an Internet registry. Addresses from
Comment:    this block are used in multiple, separately
Comment:    operated networks.
Comment:    This block was assigned by the IETF in the
Comment:    Best Current Practice document, RFC 1918
Comment:    which can be found at:
Comment:    http://www.rfc-editor.org/rfc/rfc1918.txt
RegDate:    1994-03-15
Updated:    2010-03-15

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  abuse@iana.org

# ARIN WHOIS database, last updated 2010-05-15 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at https://www.arin.net/whois_tou.html
tom@tardis:~$ whois 192.168.250.64

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    PRIVATE-ADDRESS-CBLK-RFC1918-IANA-RESERVED
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is used as private address space.
Comment:    Addresses from this block can be used by
Comment:    anyone without any need to coordinate with
Comment:    IANA or an Internet registry. Addresses from
Comment:    this block are used in multiple, separately
Comment:    operated networks.
Comment:    This block was assigned by the IETF in the
Comment:    Best Current Practice document, RFC 1918
Comment:    which can be found at:
Comment:    http://www.rfc-editor.org/rfc/rfc1918.txt
RegDate:    1994-03-15
Updated:    2010-03-15

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  abuse@iana.org

# ARIN WHOIS database, last updated 2010-05-15 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at https://www.arin.net/whois_tou.html
tom@tardis:~$ 

```


Any other information about the network would anyone need? I could try and glean it from my mates that work at the help desk...

---

### Post by CharlesA on 2010-05-16
Can you please verify that the .local domain is part of the hostname by running this:

```
hostname -f
```

It should return this:

```
tardis.local
```

Also what does /etc/resolv.conf look like?

---

### Post by tom.swartz07 on 2010-05-16
> **CharlesA said:**
> Can you please verify that the .local domain is part of the hostname by running this:

```
hostname -f
```

It should return this:

```
tardis.local
```

```
tom@tardis:~$ hostname -f
tardis
tom@tardis:~$ 
```

Nope! no .local

That might be the problem! how does one fix that?


```

# Generated by NetworkManager
domain resnet.scranton.edu
search resnet.scranton.edu
nameserver 192.168.242.248
nameserver 134.198.10.10
nameserver 134.198.100.150
/etc/resolv.conf (END) 

```

---

### Post by CharlesA on 2010-05-16
I cannot recall how I fixed mine, I think I did a clean install after I was unable to find any info on how to change the domain name on my server.

I don't know if this will help or not: [http://www.cyberciti.biz/faq/linux-setting-hostname-and-domain-name-of-my-server/](http://www.cyberciti.biz/faq/linux-setting-hostname-and-domain-name-of-my-server/)

---

### Post by BoneKracker on 2010-05-16
Apparently your local dns server is not providing whois service; your whois query got forwarded, and since it was within an IANA-assigned private address range it went to the "blackhole".

Also, the nslookup with a blank domain name was ignored by the local dns server and forwarded, and you therefore received an NXDOMAIN reply from a higher-echelon dns server (i.e., the domain "no domain" does not exist).

So the dns-related information we got so far is useless.

Cisco clean access server is Windows-oriented a network access control device.  If you were on a Windows box, it might be manipulating settings on your machine via a client (or "agent"), but since you're on Linux, I think all it's doing is authenticating you via web-based username/password dialog.

Here's some more we know:

We know the following, which came from the dhcp server and is recorded on your /etc/resolv.conf file:

domain resnet.scranton.edu
search resnet.scranton.edu
nameserver 192.168.242.248
nameserver 134.198.10.10
nameserver 134.198.100.150


A whois query of one of those addresses will tell us something about the network:
```
~ $ whois 134.198.10.10

OrgName:    University of Scranton 
OrgID:      UNIVER-81-Z
Address:    800 Linden Street
Address:    Rm #029 Alumni Memorial Hall
City:       Scranton
StateProv:  PA
PostalCode: 18510
Country:    US

NetRange:   134.198.0.0 - 134.198.255.255 
CIDR:       134.198.0.0/16 
NetName:    UOFSCRANTON
NetHandle:  NET-134-198-0-0-1
Parent:     NET-134-0-0-0-0
NetType:    Direct Assignment
NameServer: PLATYPUS.SCRANTON.EDU
NameServer: PHOENIX.SCRANTON.EDU
Comment:    http://www.scranton.edu
RegDate:    1989-07-13
Updated:    2008-03-25

RAbuseHandle: AMA67-ARIN
RAbuseName:   MASZEROSKI, ANTHONY 
RAbusePhone:  +1-570-941-4226
RAbuseEmail:  MASZEROSKIA3@scranton.edu 

RTechHandle: RRI5-ARIN
RTechName:   Rignanesi, Raymond 
RTechPhone:  +1-570-941-4041
RTechEmail:  rignanesir2@scranton.edu 

OrgAbuseHandle: AMA67-ARIN
OrgAbuseName:   MASZEROSKI, ANTHONY 
OrgAbusePhone:  +1-570-941-4226
OrgAbuseEmail:  MASZEROSKIA3@scranton.edu

OrgTechHandle: CAK11-ARIN
OrgTechName:   Krzywiec, Calvin Anthony
OrgTechPhone:  +1-570-941-6748
OrgTechEmail:  krzywiecc2@scranton.edu

# ARIN WHOIS database, last updated 2010-05-16 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at https://www.arin.net/whois_tou.html
```

So there's three phone numbers you can call if you can't resolve this yourself, or you could always walk down to room 29 Alumni Hall and make a nuisance of yourself till they square you away.

In the mean time, make sure what you've got set in your network manager makes sense.  Verify that /etc/hosts makes sense.

We can also try directly specifying the server and repeating some of these queries, and trying them with a domain.

See if it still has a record for your old hostname:

nslookup lucid-laptop
nslookup lucid-laptop.local 192.168.242.248

Try your new hostname with different domains, and try forcing it to respond with an authoritative answer from the local dns server:

nslookup tardis 192.168.242.248
nslookup tardis.local 192.168.242.248
nslookup tardis.resnet.scanton.edu 192.168.242.248

Unlikely, but try forcing the whois to a local dns server:
whois -h 192.168.242.248 192.168.255.119
whois -h 192.168.242.248 192.168.250.64

You might just need to go down there and ask them to help you set up access again.  They might not be assigning dns dynamically.  Maybe you "signed up" your host when they set up your clean access account.

Beyond those guesses, this is over my head personally.

---

### Post by tom.swartz07 on 2010-05-16
> **BoneKracker said:**
> Apparently your local dns server is not providing whois service; your whois query got forwarded, and since it was within an IANA-assigned private address range it went to the "blackhole".

Also, the nslookup with a blank domain name was ignored by the local dns server and forwarded, and you therefore received an NXDOMAIN reply from a higher-echelon dns server (i.e., the domain "no domain" does not exist).

So the dns-related information we got so far is useless.

Cisco clean access server is Windows-oriented a network access control device.  If you were on a Windows box, it might be manipulating settings on your machine via a client (or "agent"), but since you're on Linux, I think all it's doing is authenticating you via web-based username/password dialog.

Here's some more we know:

We know the following, which came from the dhcp server and is recorded on your /etc/resolv.conf file:

domain resnet.scranton.edu
search resnet.scranton.edu
nameserver 192.168.242.248
nameserver 134.198.10.10
nameserver 134.198.100.150


A whois query of one of those addresses will tell us something about the network:
```
~ $ whois 134.198.10.10

OrgName:    University of Scranton 
OrgID:      UNIVER-81-Z
Address:    800 Linden Street
Address:    Rm #029 Alumni Memorial Hall
City:       Scranton
StateProv:  PA
PostalCode: 18510
Country:    US

NetRange:   134.198.0.0 - 134.198.255.255 
CIDR:       134.198.0.0/16 
NetName:    UOFSCRANTON
NetHandle:  NET-134-198-0-0-1
Parent:     NET-134-0-0-0-0
NetType:    Direct Assignment
NameServer: PLATYPUS.SCRANTON.EDU
NameServer: PHOENIX.SCRANTON.EDU
Comment:    http://www.scranton.edu
RegDate:    1989-07-13
Updated:    2008-03-25

RAbuseHandle: AMA67-ARIN
RAbuseName:   MASZEROSKI, ANTHONY 
RAbusePhone:  +1-570-941-4226
RAbuseEmail:  MASZEROSKIA3@scranton.edu 

RTechHandle: RRI5-ARIN
RTechName:   Rignanesi, Raymond 
RTechPhone:  +1-570-941-4041
RTechEmail:  rignanesir2@scranton.edu 

OrgAbuseHandle: AMA67-ARIN
OrgAbuseName:   MASZEROSKI, ANTHONY 
OrgAbusePhone:  +1-570-941-4226
OrgAbuseEmail:  MASZEROSKIA3@scranton.edu

OrgTechHandle: CAK11-ARIN
OrgTechName:   Krzywiec, Calvin Anthony
OrgTechPhone:  +1-570-941-6748
OrgTechEmail:  krzywiecc2@scranton.edu

# ARIN WHOIS database, last updated 2010-05-16 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at https://www.arin.net/whois_tou.html
```

So there's three phone numbers you can call if you can't resolve this yourself, or you could always walk down to room 29 Alumni Hall and make a nuisance of yourself till they square you away.

In the mean time, make sure what you've got set in your network manager makes sense.  Verify that /etc/hosts makes sense.

We can also try directly specifying the server and repeating some of these queries, and trying them with a domain.

See if it still has a record for your old hostname:

nslookup lucid-laptop
nslookup lucid-laptop.local 192.168.242.248

Try your new hostname with different domains, and try forcing it to respond with an authoritative answer from the local dns server:

nslookup tardis 192.168.242.248
nslookup tardis.local 192.168.242.248
nslookup tardis.resnet.scanton.edu 192.168.242.248

Unlikely, but try forcing the whois to a local dns server:
whois -h 192.168.242.248 192.168.255.119
whois -h 192.168.242.248 192.168.250.64

You might just need to go down there and ask them to help you set up access again.  They might not be assigning dns dynamically.  Maybe you "signed up" your host when they set up your clean access account.

Beyond those guesses, this is over my head personally.


This is bollocks. I guess Ill just take a wander on over to the help desk in Alumni Hall tomorrow.


Thanks again for all of the help!!
Ill let you guys know what I come up with.

---

### Post by CharlesA on 2010-05-17
Good luck. What a pain in the butt.

---

### Post by tom.swartz07 on 2010-05-17
On a comical note:
They at least know that I was up to something...
> 
Splunk alerts showed this PC port scanning destination port 5900/tcp
(used by VNC remote access). I don't know if the student is playing with
network scanning tools, is infected, or something else.

Current Assignees: ResCon


HAHA!

---

### Post by tom.swartz07 on 2010-05-18
Alrighty. Update.


They thought that my iPod was a full-blown computer with a virus, so they cut it off the network. I went and talked to them earlier today and got the functionality restored. They also said that they purge the DHCP client list every Wednesday morning at 2am (which explains why I have to log back in to the network every Wednesday morning)

They advised that I simply hang out until tomorrow morning and see if the DHCP server picks up the new hostname after Logging back in.


Hopefully this will all sort out in the wash! 

Thanks for the help guys!

---

### Post by CharlesA on 2010-05-18
That would explain it then. Hope it works tomorrow!

---

### Post by tom.swartz07 on 2010-05-18
Thanks Charles!

Ill let you know yay or nay tomorrow!

---

### Post by BoneKracker on 2010-05-18
Did you tell them the whole linux community is watching?

:popcorn:

---

### Post by tom.swartz07 on 2010-05-21
Whelp, it looks like I pointed out a security hole that they decided to patch up.

I tried using my iPhone, didnt work. Tried using my buddies Ubuntu box, didnt work. I called them and they told me that they changed the rules after I went to them about it.

They wont allow anyone to use SSH unless they specifically register at the IT desk and have an Admin specifically add an exception for your MAC address. 

Im not going to bother with it, as Im only here for another week and then Ill be home for the summer.

Some nutcases here, you know?


Anyway- Cheers for all of the help and support!

---

### Post by BoneKracker on 2010-05-21
> **tom.swartz07 said:**
> Whelp, it looks like I pointed out a security hole that they decided to patch up.

I tried using my iPhone, didnt work. Tried using my buddies Ubuntu box, didnt work. I called them and they told me that they changed the rules after I went to them about it.

They wont allow anyone to use SSH unless they specifically register at the IT desk and have an Admin specifically add an exception for your MAC address. 

Im not going to bother with it, as Im only here for another week and then Ill be home for the summer.

Some nutcases here, you know?


Anyway- Cheers for all of the help and support!
Actually, their policy makes sense.  Starting around 2008 or so, there was a huge surge in brute-force attacks against sshd (probably something the script-kiddies got hold of), so MAC-based filtering would be a simple way to easily cut most of that off (and it benefits you by keeping you out the line of fire).

I'm sure you know enough not to use key-based authentication instead of password-based.

---

### Post by tom.swartz07 on 2010-05-21
> **BoneKracker said:**
> Actually, their policy makes sense.  Starting around 2008 or so, there was a huge surge in brute-force attacks against sshd (probably something the script-kiddies got hold of), so MAC-based filtering would be a simple way to easily cut most of that off (and it benefits you by keeping you out the line of fire).

I'm sure you know enough not to use key-based authentication instead of password-based.

Yepper. I have a 2040bit? RSA key. I cant remember the exact spec of it, but I was impressed by the fact that it took my dual core x64 processor over an hour to process it all. Granted, most of it was probably collection of 'noise' from what I was doing at the time....

Next semester I might head over and get myself setup for ssh..
its just not economical at this time.

---

