---
title: "Blocked from archives.ubuntu.com"
date: 2010-10-14
forum: General Help
---

### Post by baaka on 2010-10-14
I have not been able to get to [www.ubuntu.com](www.ubuntu.com) or any of the ip's that resolve to archives.ubuntu.com. I contacted my ISP provider and they confirmed they could not reach them either. Would their be any reason why Ubuntu would block an ISP from getting to them? I am unable to update any of my desktops or install any applications from the repositories.

---

### Post by lisati on 2010-10-14
I just went to archives.ubuntu.com, and Firefox told me, "server not found".

---

### Post by Sub101 on 2010-10-14
There is no "s" on the end of archives.

[http://archive.ubuntu.com/]("http://archive.ubuntu.com/")

EDIT: Unless that is a different thing....

---

### Post by baaka on 2010-10-14
Your correct it is archive.ubuntu.com and still I can not reach it via my current Internet provider. I can reach it via other providers.

---

### Post by Sub101 on 2010-10-14
Odd one...

Can you ping it?

---

### Post by coffeecat on 2010-10-14
> **baaka said:**
> Your correct it is archive.ubuntu.com and still I can not reach it via my current Internet provider. I can reach it via other providers.

Try 91.189.88.45 in Firefox from the ISP that's giving you trouble. If that takes you to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) then your ISP's nameserver needs attention.

---

### Post by baaka on 2010-10-14
Nslookup gets the following from ISP DNS

Server:  rad0.nefcom.net
Address:  69.57.112.10

Non-authoritative answer:
Name:    archive.ubuntu.com
Addresses:  91.189.92.167, 91.189.92.169, 91.189.92.170, 91.189.92.171
          91.189.92.172, 91.189.88.30, 91.189.88.31, 91.189.88.40, 91.189.88.45
          91.189.88.46, 91.189.92.166

Trace Route fails with the following

Tracing route to archive.ubuntu.com [91.189.88.40]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.5.1
  2    14 ms    16 ms     7 ms  67-223-192-65.nefcom.net [67.223.192.65]
  3   136 ms   211 ms   209 ms  ge-6-24.car1.Atlanta2.Level3.net [4.71.253.21]
  4    40 ms    38 ms    31 ms  ae-61-51.ebr1.Atlanta2.Level3.net [4.68.103.28]

  5    30 ms    41 ms    20 ms  ae-6-6.ebr1.Washington12.Level3.net [4.69.148.10
6]
  6    29 ms    33 ms    21 ms  ae-1-100.ebr2.Washington12.Level3.net [4.69.143.
214]
  7    45 ms    24 ms    38 ms  4.69.148.49
  8   118 ms   137 ms   112 ms  ae-42-42.ebr2.London1.Level3.net [4.69.137.69]
  9   102 ms   117 ms   102 ms  ae-100-100.ebr1.London1.Level3.net [4.69.141.165
]
 10   114 ms   104 ms   128 ms  ae-3-3.ebr2.London2.Level3.net [4.69.141.190]
 11     *      135 ms     *     ae-26-52.car2.London2.Level3.net [4.68.117.48]
 12   117 ms   115 ms   118 ms  gi1-0-1.oxygen.canonical.com [195.50.121.2]
 13     *        *        *     Request timed out.
 14     *     ^C
C:\Documents and Settings\Brad>tracert 91.189.88.45

Tracing route to prat.canonical.com [91.189.88.45]
over a maximum of 30 hops:

  1     4 ms     1 ms     1 ms  192.168.5.1
  2     9 ms    17 ms    17 ms  67-223-192-65.nefcom.net [67.223.192.65]
  3    70 ms   194 ms   211 ms  ge-6-24.car1.Atlanta2.Level3.net [4.71.253.21]
  4    28 ms    34 ms    29 ms  ae-61-51.ebr1.Atlanta2.Level3.net [4.68.103.28]

  5    33 ms    36 ms    50 ms  ae-6-6.ebr1.Washington12.Level3.net [4.69.148.10
6]
  6    38 ms    41 ms    47 ms  ae-1-100.ebr2.Washington12.Level3.net [4.69.143.
214]
  7    25 ms    49 ms    39 ms  4.69.148.49
  8   105 ms   117 ms   110 ms  ae-44-44.ebr2.London1.Level3.net [4.69.137.77]
  9   109 ms   114 ms   120 ms  ae-100-100.ebr1.London1.Level3.net [4.69.141.165
]
 10   110 ms   106 ms   120 ms  ae-3-3.ebr2.London2.Level3.net [4.69.141.190]
 11     *      108 ms   109 ms  ae-26-54.car2.London2.Level3.net [4.68.117.112]

 12   114 ms    95 ms   142 ms  gi1-0-1.oxygen.canonical.com [195.50.121.2]
 13     *        *        *     Request timed out.

---

### Post by Sub101 on 2010-10-14
Can you access this:

caryopsis.canonical.com

I think it is an issue with your isp DNS. If the above works try changing your dns settings.

---

### Post by baaka on 2010-10-14
> **Sub101 said:**
> Can you access this:

caryopsis.canonical.com

I think it is an issue with your isp DNS. If the above works try changing your dns settings.

No I can not access that site either. I have also tried OpenDNS servers with no success.

---

### Post by baaka on 2010-10-17
Does Ubuntu block ip ranges? Or would this more likely be an ISP issue? Unfortunately if I can not get this resolved I will have to switch distributions since I can not get to the repositories.

---

### Post by sandyd on 2010-10-17
> **baaka said:**
> Does Ubuntu block ip ranges? Or would this more likely be an ISP issue? Unfortunately if I can not get this resolved I will have to switch distributions since I can not get to the repositories.
[s]where are you?[/s]
florida eh?

try the florida university repos.

it seems that theirs a loose end on canonicals side somewhere (indicated by your traceroute) as I cannot access it from level3 either.

---

