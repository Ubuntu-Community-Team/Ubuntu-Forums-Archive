---
title: "Bind/DNS issues"
date: 2009-10-12
forum: General Help
---

### Post by Muscovy on 2009-10-12
I'm putting lamp and a DNS server on an old laptop of mine. It's running a minimalist version of normal Ubuntu.

  I got the lamp package working fine, and I can see my website when I type in my IP. But the DNS is giving me a headache.
  For a start, not two tutorials are the same. Mainly they have small conflicts, but it's still confusing. I've been using [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) as my information for the most part.
  At no point have I been able to see my site in a browser. Twice I managed to ping the domain, only for it to fail on a ping seconds later. I've tried ```
named-checkzone domain.org /etc/bind/db.domain.org
``` and previously got errors about my nameserver containing no domains, and I *think* I fixed it, but all I know is that ```
named-checkzone domain.org /etc/bind/db.domain.org
``` returns no errors now.

  Any ideas as to what I might have done wrong? I don't seem to be getting errors, everything seems fine other than the fact it... didn't work.

 I can put my config files up if anyone could make use of them.

            -Thanks

---

### Post by shylent on 2009-10-12
Paste your zone file and the relevant parts from the named.conf file (the zone declarations).

Anyway, to set up bind, you must understand how dns works and why it works. I don't see how this can be done by blindly following the tutorial. But, then again, that's just me.

---

### Post by Muscovy on 2009-10-12
/etc/bind/db.alexandos.org
```

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA  ns1.alexandos.org.  root.alexandos.org. (
			      3		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns1.alexandos.org.
@	IN	A	154.5.45.68
box     IN      A       154.5.45.68

www           IN      A       154.5.45.68
mta           IN      A       154.5.45.68
ns1           IN      A       154.5.45.68       IN      A       192.168.1.71

```

/etc/bind/db.ns1.alexandos.org
```

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA  ns1.alexandos.org.  root.ns1.alexandos.org. (
			      3		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	A	alexandos.org.
@	IN	A	mta.alexandos.org.
@	IN	A	ns1.alexandos.org.
@	IN	A	192.168.1.71
box     IN      A       192.168.1.71

```

And here's the significant parts of named.conf
```

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

```
My local IP is 192.168.1.71 and my world IP is 154.5.45.68 .

---

### Post by Muscovy on 2009-10-12
It seems I didn't have and needed a MX (mail) entry. Now the server can ping, dig, and even open in firefox... but only on that computer, not even on other lan computers.

Edit: I'm positive port 53 isn't blocked. canyouseeme.org can see it.

---

### Post by shylent on 2009-10-13
You see, the zone declarations you've pasted don't mention the          /etc/bind/db.alexandos.org file anywhere. Anyway, did I get it right, that you want to be able to reach your webserver *by the symbolic name* (f.ex www.alexandos.org) *from inside your LAN*? In that case, all you need are the following declarations:
zone declaration in the named.conf:

```

zone "alexandos.org" {   
  type master;    
  file "/etc/bind/db.alexandos.org";
};

```zone datafile (/etc/bind/db.alexandos.org)
```

[FONT=Courier New]$TTL    604800
@    IN    SOA  ns.alexandos.org.  root.alexandos.org. ( 
                                                        2009101300  ; Serial             
                                                        604800      ; Refresh              
                                                        86400       ; Retry            
                                                        2419200     ; Expire             
                                                        604800 )    ; Negative Cache TTL
               A 192.168.1.71
               NS alexandos.org.
ns             CNAME @
www            CNAME @ ; or something
[/FONT]
```That is assuming, that your dns/web server's ip in your lan is 192.168.1.71 (the "external" ip is irrelevant).

Check the configuration (mind the trailing dots!):
dig @192.168.1.71 www.alexandos.org__[]("http://www.alexandos.org"). (should mention 192.168.1.71 in the answer section)
dig @192.168.1.71 alexandos.org. (should also answer with 192.168.1.71)


Remember, if you change your zone datafiles, you must increment the serial.

---

### Post by Muscovy on 2009-10-15
I actually want it viewable worldwide. I simply posted the fact that most of the LAN couldn't view it because it didn't make sense.

  I'll try adding in the zone declaration, I can't believe I missed that.

  Also, I'm a little confused about the serials. You increment them... one per edit? One per domain/subdomain? All I know is they go up.


Edit: In about 15 minutes I'll have my results up.

Edit 2: Nothing happened.

Edit 3: I am getting errors about 127.0.0.1#953 now.

---

### Post by Muscovy on 2009-10-21
Bump.

---

### Post by Muscovy on 2009-10-24
Ok, I've fixed it up (more or less :confused:), and I have no errors, and can ping, dig, and view the domain from the server computer. Is an ubuntu port blocked or something?


Edit: Ok, it seems I was only getting through because of an edit to resolve.conf. What is going on?

---

