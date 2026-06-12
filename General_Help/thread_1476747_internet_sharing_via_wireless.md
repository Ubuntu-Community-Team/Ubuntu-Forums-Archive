---
title: "internet sharing via wireless"
date: 2010-05-08
forum: General Help
---

### Post by UT8F on 2010-05-08
Hi,
I have dsl connection connected to my laptop, laptop have wireless. How I can share internet via wireless to another laptop? 
When I create wireless network, I cant connect it from another laptop with (WIndows Vista). There allways says that password is incorrect. How I should share internet?



Here photo from where I'm creating network: [http://img705.imageshack.us/img705/1418/screenshotjb.png](http://img705.imageshack.us/img705/1418/screenshotjb.png)
Ubuntu 10.04

---

### Post by 3rdalbum on 2010-05-08
> **UT8F said:**
> Hi,
I have dsl connection connected to my laptop, laptop have wireless. How I can share internet via wireless to another laptop? 
When I create wireless network, I cant connect it from another laptop with (WIndows Vista). There allways says that password is incorrect. How I should share internet?

You're definitely on the right track. You need to use WPA2 encryption with a password, and make sure that Vista connects to your network as "Ad-hoc" (not Infrastructure).

---

### Post by UT8F on 2010-05-08
> **3rdalbum said:**
> You're definitely on the right track. You need to use WPA2 encryption with a password, and make sure that Vista connects to your network as "Ad-hoc" (not Infrastructure).

I did all what you sayd, but when I connect to wifi from laptop with Vista, I cant acces the web pages and vista says Limited Connectivity or somethink like that. Whats wrong?

---

### Post by bumanie on 2010-05-08
What sort of router are you using?

---

### Post by UT8F on 2010-05-08
> **bumanie said:**
> What sort of router are you using?

There is no router. I'm using dsl internet connection. MODEM > LAPTOP. But I need to share my internet to another laptop via wifi. So I'm creating wireless network. I mean MODEM > LAPTOP > WIFI > LAPTOP. Somethink like that. Trying to share from ubuntu, but another laptop with Vista connects to my network. But I cant acces the internet (VISTA). 

I dont know how to explain more detail, because I'm poor on english.

---

### Post by UT8F on 2010-05-08
> **bumanie said:**
> What sort of router are you using?

Oh route, sorry didint understand. I'm using AD-HOC security WPA and WPA2 Personal.

---

### Post by 3rdalbum on 2010-05-08
Vista might need the DNS information copied from your Ubuntu machine or modem. You can find it out from Ubuntu by right-clicking on Network Manager and going to Connection Information.

---

### Post by dz0 on 2010-05-31
maybe smb knows, how to deal if my incomming connection is wimax (Lithuania - Mezon), as Network manager does not "see" my wimax0 connection. by the way "Edit Network Connections" doesn't start up, though "Create new wireless.." pops up ok.
I want to use lubuntu on eeepc.
I saw in several posts, I should also install dnsmasq-base and dhcp-server - do I really need them?

---

