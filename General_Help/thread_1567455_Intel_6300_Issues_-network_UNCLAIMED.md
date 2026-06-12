---
title: "Intel 6300 Issues -network UNCLAIMED"
date: 2010-09-03
forum: General Help
---

### Post by SteveS1949 on 2010-09-03
Hi, I have a netbook with an Intel 6300 card in it. However, I cannot see it anywhere except in the following command and in lspci.

'lshw -C network' returns:


 *-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff

I thought this card is supported by iwlagn... How do I make it use that driver?

---

### Post by rotten777 on 2012-03-15
> **SteveS1949 said:**
> Hi, I have a netbook with an Intel 6300 card in it. However, I cannot see it anywhere except in the following command and in lspci.

'lshw -C network' returns:


 *-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff

I thought this card is supported by iwlagn... How do I make it use that driver?

Running into the same issue with 12.04 and the 6300

---

