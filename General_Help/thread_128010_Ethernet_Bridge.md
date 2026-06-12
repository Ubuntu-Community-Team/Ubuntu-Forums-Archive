---
title: "Ethernet Bridge?"
date: 2006-02-10
forum: General Help
---

### Post by IanWright on 2006-02-10
I was wondering if anyone could provide me with some assistance regarding Ethernet bridges? I'm new to Linux and am trying to set up a transparent bridge between a Win2k machine and the Uni campus network.

I've been using the guide from ([http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)) and basically used the following commands:

 # ifconfig eth0 0.0.0.0
 # ifconfig eth1 0.0.0.0
 # brctl addbr comms
 # brctl addif comms eth0
 # brctl addif comms eth1 
 # ifconfig comms up

This sets up fine, and initalises the bridge, however it doesn't work correctly. The Win2k machine works fine directly plugged into the network, but through the linux bridge machine I don't get anything, and using (#brctl showmacs comms) command I only get the local MAC address, no Win2k machine.

I was wondering if anyone could give me a few pointers or maybe suggest what could be wrong?

Thanks :)

Ian W

---

### Post by dcstar on 2006-02-10
[QUOTE=IanWright]I was wondering if anyone could provide me with some assistance regarding Ethernet bridges? I'm new to Linux and am trying to set up a transparent bridge between a Win2k machine and the Uni campus network.

I've been using the guide from ([http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)) and basically used the following commands:

 # ifconfig eth0 0.0.0.0
 # ifconfig eth1 0.0.0.0
 # brctl addbr comms
 # brctl addif comms eth0
 # brctl addif comms eth1 
 # ifconfig comms up

This sets up fine, and initalises the bridge, however it doesn't work correctly. The Win2k machine works fine directly plugged into the network, but through the linux bridge machine I don't get anything, and using (#brctl showmacs comms) command I only get the local MAC address, no Win2k machine.

I was wondering if anyone could give me a few pointers or maybe suggest what could be wrong?

Thanks :)

Ian W[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by IanWright on 2006-02-12
I might be blind but couldn't really see much of any relevance regarding Ethernet bridges.

I don't believe that link you suggest is any good, it appears to be routing rather than switching...

---

