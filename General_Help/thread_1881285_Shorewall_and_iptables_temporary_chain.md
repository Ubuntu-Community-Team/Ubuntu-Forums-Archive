---
title: "Shorewall and iptables temporary chain"
date: 2011-11-15
forum: General Help
---

### Post by gib86 on 2011-11-15
Hi!
I'm trying to write a simple captive portal to use in our little wifi network. The software is written in Java and it simply write and apply iptables rules generated from database based on user and group. When i finish the beta version i release it with GPL licence.

The problem is: i'm running shorewall to define default rules (all drop) and the rule to redirect all http request to Captive Portal Login Page. When user log in i generate some iptables rules and apply with a new Chain (with ulog rules too). 
All works perfectly but when i'm logged out from system all the rules and the chain created will be deleted the redeirect rule defined in shorewall won't work.

When i restart shorewall it works.

I tryied to run iptables -L <chainname> and all rulesgenerated from my software is cleaned (no chian/target with this name) and i've tryied to diff an "iptables -L" before and after restarting shorewall with no differences.

Somebody can help me?

Sorry for my little english.

---

