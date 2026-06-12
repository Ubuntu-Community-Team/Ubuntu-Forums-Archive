---
title: "Anyone else having update issues?"
date: 2009-10-02
forum: General Help
---

### Post by SoylentSteak on 2009-10-02
Update manager repeatedly couldn't get all updates, and when I chose to download the ones it could, it was very slow, so I canceled. I was just wondering if, perhaps, this is because it's getting close to Karmic's release and maybe the servers are full? Or, is it just me?

---

### Post by paradox242 on 2009-10-02
Same issues here, trying to install packages for Jaunty. It's hanging on:

0% [Connecting to us.archive.ubuntu.com (91.189.88.40)]

When I ping us.archive.ubuntu.com I get:

64 bytes from jackass.canonical.com (91.189.88.140): icmp_seq=1 ttl=47 time=118 ms
64 bytes from jackass.canonical.com (91.189.88.140): icmp_seq=3 ttl=47 time=115 ms

Has it always resolved to a computer called jackass? Or has it been haxxored?

---

### Post by marmotapl on 2009-10-02
I had the same problem updating some samba-servers-security-updates-thing. I've tried twice to download the updates... The first time I was downloading the security updates plus the updates for OOo and the update manager throw me an error at the end of the process (i was downloading at 4 Kb/s or so >.<), the second time I've selected the security updates only (there were 3 i guess), and the download rate was very low, but the download finished without a problem.

Maybe u can try again...

Cheers. (y)

PS: Sorry for the bad english, I'm Chilean =)

---

### Post by paradox242 on 2009-10-02
Now it says:

PING us.archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=47 time=121 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=47 time=117 ms

Interesting choice of hostnames to say the least...

Still can't update.

---

### Post by Giblet5 on 2009-10-02
It sure looks like someone's been baiting with DNS poison...

I resolve it as vostok.canonical.com.

Heh heh. Those crazy kids...

---

### Post by fazavon on 2009-10-02
I thinks its everyone, 9.10 Beta was released last night, so the servers are getting a work out. Wait till Sunday and everything should calm down and be back to normal.

//j

---

### Post by csabo2 on 2009-10-02
Jackass?  not looking good.  I need to get kernel-headers-2.6.28-15-server now any ideas on how/where?

EDIT: I'm getting prat.canonical.com now :X
2nd EDIT: pinged again and got jackass again :D

---

### Post by SoylentSteak on 2009-10-02
> **fazavon said:**
> I thinks its everyone, 9.10 Beta was released last night, so the servers are getting a work out. 

Happens every time. ](*,)

---

