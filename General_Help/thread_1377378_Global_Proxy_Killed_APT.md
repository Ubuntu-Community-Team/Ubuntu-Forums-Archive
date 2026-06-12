---
title: "Global Proxy Killed APT"
date: 2010-01-10
forum: General Help
---

### Post by ravious on 2010-01-10
Using 9.04

Went to System->Prefs->Network Proxy.

Set a network proxy, then applied system wide..

Ended up setting it back to default, and applied system wide again.


Now every time i try to use apt or synaptic i always get a connection error because its trying to connect to the proxy that i had previously created and removed earlier..

I've looked over several forums posts, and they all said to check the

/etc/apt/apt.conf

for any listing of the proxy but its a blank file.

Not sure what to try next.. Can anyone offer any advice?

---

### Post by dcstar on 2010-01-11
> **ravious said:**
> Using 9.04

Went to System->Prefs->Network Proxy.

Set a network proxy, then applied system wide..

Ended up setting it back to default, and applied system wide again.


Now every time i try to use apt or synaptic i always get a connection error because its trying to connect to the proxy that i had previously created and removed earlier..

I've looked over several forums posts, and they all said to check the

/etc/apt/apt.conf

for any listing of the proxy but its a blank file.

Not sure what to try next.. Can anyone offer any advice?

Go into Synaptic and remove it there.

---

### Post by ravious on 2010-01-11
There is nothing listed under synaptic proxy settings.

---

### Post by dcstar on 2010-01-12
> **ravious said:**
> There is nothing listed under synaptic proxy settings.

Try adding something there, saving it, and then removing it.

---

