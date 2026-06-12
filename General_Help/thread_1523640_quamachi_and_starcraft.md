---
title: "quamachi and starcraft"
date: 2010-07-03
forum: General Help
---

### Post by kingwooky on 2010-07-03
Hello I just switched over to Ubuntu from vista because it was giving me to many problems and I'm setting things up.

My question is how can I bind Quamachi's ip to Starcraft like in windows
but since forcebindip wont work im wondering if any of you know what I can do to get it so I can play lan udp games over quamachi?

I have quamachi installed and ready to go... I can see the networks, so once I can get starcraft set up I should be ready to go.
I just need to bind the ip somehow.

Thank you for your help.

---

### Post by kingwooky on 2010-07-04
Bump!

---

### Post by kingwooky on 2010-07-04
Bump!

---

### Post by kingwooky on 2010-07-04
Bump!

---

### Post by kingwooky on 2010-07-04
Bump!

---

### Post by cherva on 2010-07-04
Append your quamachi ip followed by your hostname (type "hostname" in terminal to see your hostname) in /etc/hosts ... Example: ```
11.22.33.44 Jon-PC
``` Then restart wine and try again.

---

### Post by kingwooky on 2010-07-04
how do you append?

---

### Post by kingwooky on 2010-07-05
Bump!

---

### Post by kingwooky on 2010-07-05
Bump!

"how do you append?"

---

### Post by cherva on 2010-07-05
```
gksu gedit /etc/hosts
```
And add it below the other stuff there.
Example:
```
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
11:22:33:44 Jon-PC

```

---

### Post by cherva on 2010-07-06
If this helped, please mark your thread as [SOLVED]

---

