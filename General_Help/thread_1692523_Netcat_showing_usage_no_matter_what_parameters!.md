---
title: "Netcat showing usage no matter what parameters!"
date: 2011-02-21
forum: General Help
---

### Post by pjani on 2011-02-21
I just installed ubuntu 10.04.2 LTS server on my two IBM machines. Both machines have netcat-openbsd installed(1.89-3ubuntu2) and both machines have three cards one is primary for external network other two cards are gigabit. And between machines i have over these four gigabit cards established bond which works np!

The problem becomes problem when i try to run netcat to test speed of this bond.

i type in 
nc -ulp 5000 > /dev/null
i get
usage: nc [...
i have tried almost every single combination of parameters but nc keeps throwing up usage info...

thank you, for your help.

---

