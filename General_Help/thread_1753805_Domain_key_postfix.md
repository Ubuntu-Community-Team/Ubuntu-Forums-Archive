---
title: "Domain key postfix"
date: 2011-05-09
forum: General Help
---

### Post by fan0o on 2011-05-09
hi

i have postfix with TLS and now i need to configure DKIM.

This is the [tutorial]("https://help.ubuntu.com/community/Postfix/DomainKeys") that i followed

Now the part that says to create TXT records.

```
**Configuring DNS**

 You  will need to create two TXT records in order for mail recipients to  verify your signed mail. The DNS record should look like this: 
_domainkey.domain.tld. IN TXT "t=y; o=~;Where  the "t=y" means that the domain is in test mode, actually that it is  activated, and the "o=~;" means that only some mail is being signed from  this domain. If you want to indicate that all mail is signed, use  "o=-;". 

mail._domainkey.domain.tld. IN TXT "k=rsa; t=y; p=PpYHdE2tevfEpvL1Tk2dDYv0pF28/f 5MxU83x/0bsn4R4p7waPaz1IbOGs/6bm5QIDAQAB"Where everything after **p=** is actually the content of the public key we generated above, **public.key**. Be sure to only copy the key string itself, leaving out these comments: 
-----BEGIN PUBLIC KEY-----and: 
-----END PUBLIC KEY-------The t=y value pair means that the domain is using this key in test mode, also that is activate. 
```what i did is, following is my /etc/bind/zones/example.com.conf and i added those record below as u can see. Now i am doing this for the first time ever. i was just wondering if this is the right way to add TXT records.

```
 // replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mta.example.com.

// Replace the IP address with the rigt IP addresses.
www              IN      A       192.168.1.x
mta              IN      A       192.168.1.x
ns1              IN      A       192.168.1.x

_domainkey.example.com. IN TXT "t=y; o=-;
mail._domainkey.example.com. IN TXT "k=rsa; t=y; p=MIICXAIBAAKBgQCV0EDZAHoi3Exh+IFigC21m+T4IHbJFFX4OQCo4JeXppW17mNZ
OnpT4QsSmbWXKTm4etACCCqVX5yltOJLlADwl4BWahZ91xrqOxIOyM5tjrVdohc9
XFC3YgJ/0Z8xrw7PCtx9mlDulabRAVXqeDgEI1OKVbjJIO8AmR9e8qeJWwIDAQAB
AoGAHRYVw8i0kj2J4ndr5AYfBEYl+4G7Bf
S2WkD5GS7gVAh0ZsPRekWhzcV6rvfvF+uCQ7hsBw+u6YTfl4gOnh50K2xwJAWGuM
w1PVUCEg3ZFCCAwFRlFBFgtICeX2ONkTcC3lZ616EvojniEiXl2l7aBtI98LaSbw
g49NMqVyDt50I3PBgQJBAJcVZKhiLStb+aVbKwke59W7gvEo7UNNFARjGonx8soz
RQiv1fH2kIz6H7LbaCeGVnbQHsJDeCJ28inft+0mzIs="

```This is the output of 
sudo grep -i dk /var/log/mail.log is 
```
May  8 14:46:25 server02 dk-filter[12713]: Sendmail DomainKeys Filter v1.0.0 starting (args: -u dk-filter -P /var/run/dk-filter/dk-filter.pid -p /var/run/dk-filter/dk-filter.sock -l)
May  8 15:10:27 server02 dk-filter[12713]: Sendmail DomainKeys Filter: mi_stop=1
May  8 15:10:27 server02 dk-filter[12713]: Sendmail DomainKeys Filter v1.0.0 terminating with status 0, errno = 0
May  8 15:10:27 server02 dk-filter[15159]: Sendmail DomainKeys Filter v1.0.0 starting (args: -u dk-filter -P /var/run/dk-filter/dk-filter.pid -p inet:8892@localhost -l -d example.com -s /etc/mail/domainkey.key -S 2007)
May  8 15:28:32 server02 dk-filter[17992]: setgid(): Operation not permitted
May  8 15:28:45 server02 dk-filter[15159]: Sendmail DomainKeys Filter: mi_stop=1
May  8 15:28:45 server02 dk-filter[15159]: Sendmail DomainKeys Filter v1.0.0 terminating with status 0, errno = 0
May  8 15:28:45 server02 dk-filter[18019]: Sendmail DomainKeys Filter v1.0.0 starting (args: -u dk-filter -P /var/run/dk-filter/dk-filter.pid -p inet:8892@localhost -l -d example.com -s /etc/mail/domainkey.key -S 2007)

```

Please help! how do we create TXT DNS records and is there anything i m missing to accomplish the required configuration.

---

### Post by fan0o on 2011-05-11
No luck

Anybody??????

---

