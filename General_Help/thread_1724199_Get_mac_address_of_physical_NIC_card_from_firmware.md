---
title: "Get mac address of physical NIC card from firmware &amp; physical/virtual ethernet identi"
date: 2011-04-08
forum: General Help
---

### Post by mayapower on 2011-04-08
Hi,

I have tried several solutions and posted this query to many linux related forums but so far I am not even near to solution.

I need a small shell based program that prints the mac address of physical ethernet adapter from it's firmware. I need this utility[[COLOR=blue][/COLOR]]("http://www.linuxforums.org/forum/#") appliance activation. I have tried several example but none of them is flawless, The easiest method I have found is to parse the output of "ifconfig" command but it has also some drawbacks.
 
More description:
 
1. Firstly program should differentiate between physical and virtual adapters. Physical means installed on board(wired or wireless) or installed additionally. Virtual adapters are those created by VPN or created by virtualization apps such as VirtualBox/VMWare etc. I am not interested in virtual ones.
 
2. In case of more them one physical adapters(wired and wireless), it should print the mac address and description(name & vendor) of both/all adapters.
 
3. If media is disconnected then also it should be able to read the mac address and description(name, vendor) of card.
 
4. This one is bit complex. On linux mac address can easily be changed but AFAIK the universal mac address (mac address burned inside ROM) can't be changed. There is command line tool "ethtool" is available that reads the mac address from ROM. I have heard that there are some issues with ethtool as it is limited to use only two types of drivers.
 
I would appreciate if someone point me out the right direction to solve the problem. I am new to Linux world.
 
Thanks
 
Prashant

---

