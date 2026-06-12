---
title: "Internet Traffic Flow Monitor?"
date: 2010-04-27
forum: General Help
---

### Post by bcdudley on 2010-04-27
I need help fast. We have something on our network that is reaking havoc with our content filter. I am trying to track it down, but so far I have been unsuccessful. We have approximately 500 devices in 100+ different locations spread across 9 states. Looking at each computer is not really feasible. 

I need a machine that can sit in between our network and our internet connection and graphically monitor in real time and logs how much traffic each device is sending and receiving. It would need to sit inline so it has to have two nics and be able to pass traffic. The machine also needs to be transparent. Reconfiguration of our routers or workstations is not an option.

I have used ethereal and wireshark before. Ethereal may be a viable option, but wireshark seems to provide lots of information, but no practical way to make use of it. 

Any suggestions better than Etherreal and also how to set up the box to be  a transparent device on the network that will allow internet bound traffic to flow (freely)?

Thank you.

---

### Post by bcdudley on 2010-04-27
Ok, so I am thinking I just need to bridge the two nics together using something like this
```

ifconfig eth0 down
ifconfig eth1 down
brctl addbr br0
brctl  addif br0 eth0
brctl addif br0 eth1
```

Then use a program called bandwidthd. 

Will this work for what I want to do, or will it cause problems?

---

### Post by wirelessmonkey on 2010-04-27
Cacti will do what you want.

---

### Post by bcdudley on 2010-04-27
I will take a look at Cacti again. I looked at it 3 years ago and chose to go with Nagios instead. I do not want to go through a Nagios type configuration again. That took me over a month and, due to our constantly changing topology, it was obsolete by the time it was in place. I need something that is strictly a reporting tool. 

If I have to reconfigure an application every time a new subnet or node is added, it will not really do me much good. I need something along the lines of a connections cache monitor.

---

