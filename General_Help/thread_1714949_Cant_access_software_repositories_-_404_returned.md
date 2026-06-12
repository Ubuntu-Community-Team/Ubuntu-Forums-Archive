---
title: "Cant access software repositories - 404 returned"
date: 2011-03-26
forum: General Help
---

### Post by jock mackay on 2011-03-26
I have a Dell Mini running 10.10 dual booted. Accessing internet through a BT Home HUB version 2. I feel stupid having to ask for this help, but after fighting for three months to get my Internet working fully (problem solved by making the Wireless setting 802.11 B/G, instead of the BT default), now I can not access software repositories. when I try through synaptic to load Icedtea, or Google chrome for example, I get server not found 404. I was previously able to get software.

There is most likely a very obvious answer, but it's not obvious to me, so I would welcome some advice.

Remember, I am still very much a novice>

---

### Post by ~Plue on 2011-03-26
could you post the output of the following from a terminal window
```

sudo apt-get update && sudo apt-get install chromium-browser
```

---

### Post by garvinrick4 on 2011-03-26
> **jock mackay said:**
> I have a Dell Mini running 10.10 dual booted. Accessing internet through a BT Home HUB version 2. I feel stupid having to ask for this help, but after fighting for three months to get my Internet working fully (problem solved by making the Wireless setting 802.11 B/G, instead of the BT default), now I can not access software repositories. when I try through synaptic to load Icedtea, or Google chrome for example, I get server not found 404. I was previously able to get software.

There is most likely a very obvious answer, but it's not obvious to me, so I would welcome some advice.

Remember, I am still very much a novice>Internet not working most likely.
As previous from terminal:
```
sudo apt-get update
```

---

### Post by garvinrick4 on 2011-03-26
```
gedit /etc/apt/sources.list
```
to see what repositories you have open and what server (mirror) you are using.
If you can open firefox and browse the internet might just need to change server.
In software sources.

---

### Post by jock mackay on 2011-03-26
My thanks to all who responded.

Problem solved.

---

