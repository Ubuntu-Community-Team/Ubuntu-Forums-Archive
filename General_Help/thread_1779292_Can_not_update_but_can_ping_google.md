---
title: "Can not update but can ping google"
date: 2011-06-10
forum: General Help
---

### Post by thebyrnie on 2011-06-10
Hi I have searched this forum and google and cannot seem to find an answer to my problem and was hoping someone might be able to help 

I have installed ubuntu server 10.04 2 32bit numerous times and never had this issue 

I can ping google.com but when I try to update with "sudo apt-get update" it says 

"failed to fetch http://archive.ubuntu.com"

Sorry if I am being vague its just this has never happened before and if I can ping google.com and other websites why can't I update,

I tried another ubuntu server I have here and it worked perfect updating  

Any help would be much appreciated

---

### Post by pqwoerituytrueiwoq on 2011-06-10
is that a copy paste error cause the site is miss spelled
[http://archive.ubun**ut**.com](http://archive.ubunut.com)
should be
[http://archive.ubun**tu**.com](http://archive.ubutu.com)

---

### Post by thebyrnie on 2011-06-10
> **pqwoerituytrueiwoq said:**
> is that a copy paste error cause the site is miss spelled
[http://archive.ubun**ut**.com](http://archive.ubunut.com)
should be
[http://archive.ubun**tu**.com](http://archive.ubutu.com)

sorry it is archive.ubuntu.com I typed it in here wrong I have re-edited the original post 

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-10
have you tried pinging [http://archive.ubutu.com](http://archive.ubutu.com) ?

---

### Post by thebyrnie on 2011-06-10
> **pqwoerituytrueiwoq said:**
> have you tried pinging [http://archive.ubutu.com](http://archive.ubutu.com) ?

just tried it there and it said "ping: unknown host http://archive.ubuntu.com"

but if i ping [www.archive.ubuntu.com](www.archive.ubuntu.com) it works and resolves to 91.189.88.46

---

### Post by pqwoerituytrueiwoq on 2011-06-10
```
ping http://archive.ubuntu.com
ping: unknown host http://archive.ubuntu.com
```
you don't use the protocol in a ping
```
ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=51 time=111 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=51 time=116 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=51 time=110 ms
^C
--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 110.191/112.835/116.507/2.692 ms
```

---

### Post by thebyrnie on 2011-06-10
> **pqwoerituytrueiwoq said:**
> ```
ping http://archive.ubuntu.com
ping: unknown host http://archive.ubuntu.com
```
you don't use the protocol in a ping
```
ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=51 time=111 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=51 time=116 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=51 time=110 ms
^C
--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 110.191/112.835/116.507/2.692 ms
```


Thanks a million have run 

PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=128 time=1.53 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=128 time=1.15 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=128 time=1.22 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=4 ttl=128 time=1.20 ms

--- archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 1.155/1.278/1.536/0.154 ms

---

### Post by pqwoerituytrueiwoq on 2011-06-10
*looks at ping time difference*
dam low end dsl (832 Kbps / 160 Kbps)

we did not do anything the site must have been down or your Internet connection went down when you trued to update in the first place

---

### Post by thebyrnie on 2011-06-10
> **pqwoerituytrueiwoq said:**
> *looks at ping time difference*
dam low end dsl (832 Kbps / 160 Kbps)

we did not do anything the site must have been down or your Internet connection went down when you trued to update in the first place

On a gigabit fibre line here ping's are brilliant, your adsl is good for adsl 

I Know that's the crazy thing just tried it there and received this( only pasted in some)


Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (110: Connection timed out) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

---

