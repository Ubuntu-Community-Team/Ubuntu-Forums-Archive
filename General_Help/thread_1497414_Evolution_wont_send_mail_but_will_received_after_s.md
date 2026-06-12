---
title: "Evolution wont send mail but will received after switching to Comcast"
date: 2010-05-30
forum: General Help
---

### Post by cforput on 2010-05-30
OK,
so my Evolution worked fine. I was able to send and receive messages. THen I switched my ISP from a local provider to Comcast. I did nothing to Evolution and now it won't send my emails. I still receive stuff fine. I am using GMail's SMTP server.


Karmic 9.10
Evolution 2.28.1
smtp.gmail.com

I don't see anyplace to include the port number like I could in Thunderbird so I have no idea what port I am using but the thing that is curious is that it doesn't work on Comcast when it did on both my local provider and Sprint's mobile broadband.

Any suggestions?

---

### Post by Guitar John on 2010-05-30
Change outgoing server to smtp.comcast.net and check Requires Secure.

---

### Post by Bobhuber on 2010-05-30
> **cforput said:**
> OK,
so my Evolution worked fine. I was able to send and receive messages. THen I switched my ISP from a local provider to Comcast. I did nothing to Evolution and now it won't send my emails. I still receive stuff fine. I am using GMail's SMTP server.


Karmic 9.10
Evolution 2.28.1
smtp.gmail.com

I don't see anyplace to include the port number like I could in Thunderbird so I have no idea what port I am using but the thing that is curious is that it doesn't work on Comcast when it did on both my local provider and Sprint's mobile broadband.

Any suggestions?
At the end of the outgoing server name put a colon and then the port number.
As an example Verizon uses 587 > outgoing.verizon.net:587

---

### Post by AgentZ86 on 2010-06-12
> **Bobhuber said:**
> At the end of the outgoing server name put a colon and then the port number.
As an example Verizon uses 587 > outgoing.verizon.net:587

I did this for evolution, and not sending

Thunderbird workings fine when changing the outgoing port ?

???

---

