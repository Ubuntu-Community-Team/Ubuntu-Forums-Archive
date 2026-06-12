---
title: "if i dont have wirless card, icant sniff packets from laptops ?"
date: 2011-06-08
forum: General Help
---

### Post by Mashvv on 2011-06-08
well guys im sniffing some packages and im connected by a wired connection and i dont have a wireless card, would that prevent me from sniffing laptops on my network ?

---

### Post by Habitual on 2011-06-08
```
tcpdump -X -s0 -i eth0 dst host ipa.ddr.ess -w /root/mydump.pcap
```
will sniff out everything on **your** eth0 going to ipa.ddr.ess
and save it as /root/mydump.pcap

```
tcpdump -r /root/mydump.pcap
``` "plays" it back

or
```
sudo tcpdump -s0 -i eth0 -X > file.log & tail -f file.log
```


[http://www.tcpdump.org/tcpdump_man.html](http://www.tcpdump.org/tcpdump_man.html)

---

### Post by grahammechanical on 2011-06-08
Would an MP3 player let you to listen to a radio station when it does not have the electronics to receive radio transmissions?

If these laptops are connected to the router by wireless and your computer does not have a wireless card (in effect a wireless/radio transmitter/receiver) then how are you going to receive the wireless transmissions between the laptops and the router? Besides which they might be (should be) encrypted transmissions.

Regards.

---

