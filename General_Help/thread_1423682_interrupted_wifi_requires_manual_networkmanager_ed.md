---
title: "interrupted wifi requires manual networkmanager editing everytime"
date: 2010-03-06
forum: General Help
---

### Post by gry on 2010-03-06
ubuntu 9.10, 802.11[bgn], wpa/wpa2 home wifi netgear-wnr834b, 
Every time sporadic interference interrupts my wifi connection, I have to:
1) rightclick the wifi icon in the top bar
2) choose 'edit connections' from the menu
3) click the wireless tab in the 'network connections' popup box
4) click the entry for my router
5) click edit
6) type in my login password
7) click the 'wireless security' tab in the 'editing auto hutch' box
8) type in the router's password

This is crazy.  How can I get ubuntu to reconnect without all this hassle?

---

### Post by dcstar on 2010-03-06
> **gry said:**
> ubuntu 9.10, 802.11[bgn], wpa/wpa2 home wifi netgear-wnr834b, 
Every time sporadic interference interrupts my wifi connection, I have to:
1) rightclick the wifi icon in the top bar
2) choose 'edit connections' from the menu
3) click the wireless tab in the 'network connections' popup box
4) click the entry for my router
5) click edit
6) type in my login password
7) click the 'wireless security' tab in the 'editing auto hutch' box
8) type in the router's password

This is crazy.  How can I get ubuntu to reconnect without all this hassle?

Try Applications-Passwords & Encryption Keys and make a network password.

I'm sure that I have seen many posts already on issues like this.

---

### Post by perham on 2010-03-06
> **gry said:**
> ubuntu 9.10, 802.11[bgn], wpa/wpa2 home wifi netgear-wnr834b, 
Every time sporadic interference interrupts my wifi connection, I have to:
1) rightclick the wifi icon in the top bar
2) choose 'edit connections' from the menu
3) click the wireless tab in the 'network connections' popup box
4) click the entry for my router
5) click edit
6) type in my login password
7) click the 'wireless security' tab in the 'editing auto hutch' box
8) type in the router's password

This is crazy.  How can I get ubuntu to reconnect without all this hassle?

install wicd instead. it works like a charm.

---

### Post by gry on 2010-03-07
I was able to make a new keyring, and a new password on it, but have no idea how to create a 'network password'.  Can't find such in the docs.  Any hints?  How do I associate the new password with networkmanager, or whoever needs it?

---

