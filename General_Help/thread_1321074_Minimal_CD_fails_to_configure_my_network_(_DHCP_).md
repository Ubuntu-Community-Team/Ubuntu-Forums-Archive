---
title: "Minimal CD fails to configure my network ( DHCP )"
date: 2009-11-09
forum: General Help
---

### Post by Somme on 2009-11-09
This is the first time I see such behavior. When I boot from the Minimal CD, when it comes to the part where it should configure my network, it fails ( autoconfiguration failed ).
I though it could be a temporary ISP issue but when I replaced Minimal CD with 9.10 LiveCD, connection was up without any notable delay.

Any ideas ? I used the same Minimal CD yesterday on another computer .. everything seemed to be ok.

---

### Post by Giblet5 on 2009-11-09
Your ISP won't provide DHCP configuration, but your DSL or cable modem should. DHCP starts at home. :)

---

### Post by Somme on 2009-11-09
> **Giblet5 said:**
> Your ISP won't provide DHCP configuration, but your DSL or cable modem should. DHCP starts at home. :)

I don't have any modems/routers or whatever you might add to the list :roll:

---

### Post by Giblet5 on 2009-11-09
Then how are you connecting to the internet?

---

### Post by Somme on 2009-11-09
> **Giblet5 said:**
> Then how are you connecting to the internet?

I'm hardwired and don't even know where the cable starts/ends ( ok, I know the end point - my PC ).

---

### Post by Giblet5 on 2009-11-09
Interesting!

OK, you need to pull up the network configuration for whatever OS you're using to access this forum and write down:

IP Address
Network Mask
Default Gateway
DNS servers (at least one)

Then you'll have to plug those same values in to network-manager on Ubuntu after the install completes (you don't have to be connected to install).

---

### Post by Somme on 2009-11-09
> **Giblet5 said:**
> Interesting!

OK, you need to pull up the network configuration for whatever OS you're using to access this forum and write down:

IP Address
Network Mask
Default Gateway
DNS servers (at least one)

Then you'll have to plug those same values in to network-manager on Ubuntu after the install completes ([COLOR=Red]**you don't have to be connected to install**[/COLOR]).

No, I have to be connected ( Minimal CD doesn't contain any packages ). Anyway, I'll try what you said.

---

### Post by Somme on 2009-11-10
As an update, even if I configure my network manually ( by entering my IP, geteway, DHCP host and DNS servers ), it still doesn't work.
Any other ideas ? Could it really be the fault of my ISP ( can't reach them at the moment ) ?

---

