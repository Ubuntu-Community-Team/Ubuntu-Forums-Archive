---
title: "wifi connects exactly on third try!"
date: 2011-08-27
forum: General Help
---

### Post by loolooyyyy on 2011-08-27
wifi connects exactly on third try! funny, but it's true
encryption is WPA/WPA-2

how do i make it connect on first try?

---

### Post by coldraven on 2011-08-27
I don't know for sure but you could try changing channels in your router. It could be that a neighbour is on the same channel as you.
I get into my router with the address [http://192.168.2.1/](http://192.168.2.1/) in the browser. You will need to know the router's password.
I don't get any interference here, my house has stone walls two feet thick!

---

### Post by bkratz on 2011-08-27
> **coldraven said:**
> I don't know for sure but you could try changing channels in your router. [COLOR="Red"]It could be that a neighbour is on the same channel as you.[/COLOR]
I get into my router with the address [http://192.168.2.1/](http://192.168.2.1/) in the browser. You will need to know the router's password.
I don't get any interference here, my house has stone walls two feet thick!

The easiest way would be to drop to the terminal and type in

```
sudo iwlist scan
```

and see if there is interference

---

### Post by loolooyyyy on 2011-08-27
my neighbors have two routers, i know, there is no need for iwlist, as they are visible in network-manager
but i've been fine for two months! and i know my neighbors, it's a miracle they know how to turn their pc on, so they couldnt have changed their channel
but i'll give it a shot
thanx

---

### Post by coldraven on 2011-08-28
> **bkratz said:**
> The easiest way would be to drop to the terminal and type in

```
sudo iwlist scan
```and see if there is interference

I love this forum, I just learned about iwlist. Thanks bkratz

---

### Post by bkratz on 2011-08-28
> **coldraven said:**
> I love this forum, I just learned about iwlist. Thanks bkratz


Glad to have helped someone!

---

