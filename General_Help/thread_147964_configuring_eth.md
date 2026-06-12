---
title: "configuring eth"
date: 2006-03-21
forum: General Help
---

### Post by ozkan on 2006-03-21
in every startup my ubuntu tries to configuring network and 't waits for a long time so my ubuntu don't start easily how i can change it ? 
secondly in  startup it tries to syncronise the clock  i don't want it ?

---

### Post by akudewan on 2006-03-21
See this thread to stop synchronising the clock: [http://ubuntuforums.org/showthread.php?t=76543&highlight=clock+disable](http://ubuntuforums.org/showthread.php?t=76543&highlight=clock+disable)

As far as the "configuring network" part is concerned, it does take a long time, but I don't know if there's a workaround.

---

### Post by tomski on 2006-03-21
or you can use the 'ctrl-c' to stop a process from starting at boot time

when it ties to configure them at boot time it looks at the file /etc/network/interfaces

so when the pc is up and running as you want it to with the net cards configured just make sure that the settings you want the cards to be configured with at boot time are present in the file above

---

### Post by schilcha on 2006-03-21
I'm using my notebook quite frequently off-line and got really annoyed waiting for one or two minutes. 
I finally switched to ifplugd, which takes care of configuring the network interfaces as soon as the cables are plugged in. I really don't know about wlan-stuff -- it'll probably work similar.

---

