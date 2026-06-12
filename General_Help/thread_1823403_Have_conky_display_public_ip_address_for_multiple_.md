---
title: "Have conky display public ip address for multiple interfaces"
date: 2011-08-12
forum: General Help
---

### Post by ububeginner on 2011-08-12
I have script to get the public ip address
```
#!/bin/sh
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

and I call it in conkyrc
```

Wan IP:$alignr${execi 600 ~/.scripts/wan-ip}
```

and it works fine.
However, I got 2 nics and I am connected to 2 networks, both with access to the internet. 
The script only gets the public ip for eth0, as this is the default route to the internet.
Is there any way to modify the script to send the wget out eth1 instead?

---

### Post by ububeginner on 2011-08-15
Ok I have an idea on how to do this,
I'm thinking I add another script and call it wan-ip_eth1 wich should contain something like

#!/bin/sh 
set default route to eth1
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
set default route back to eth0

Would this work if I had the actual command to change the default route and what is the command to to this?

---

### Post by aeiah on 2011-08-15
> **ububeginner said:**
> Ok I have an idea on how to do this,
I'm thinking I add another script and call it wan-ip_eth1 wich should contain something like

#!/bin/sh 
set default route to eth1
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
set default route back to eth0

Would this work if I had the actual command to change the default route and what is the command to to this?

it would work, but during the execution of the script, your IP would change. this would be pretty awkward if you're uploading or downloading anything. why have you got two external IP addresses anyway?

---

### Post by ububeginner on 2011-08-15
I'm in a school/work environment where we are running some severs purely for educational purposes, those servers need to be seperated from the actual school network as we run our own DHCP etc.However I do need access to the school network as well, therefore two network cards.

I know it seems silly, but as I said, educational purposes.

I could run the script only once during startup, couldn't I?

---

### Post by aeiah on 2011-08-15
ah right, well maybe something like this will work:

```

#!/bin/sh
route add default gw your.eth1.gateway.ip dev eth1
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
route add default gw your.eth0.gateway.ip dev eth0
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

but your conky line repeats the execution, no? if you're only doing this once at startup its probably best to pipe the information into a text file or two, and then just execute a cat in conky:

```

#!/bin/sh
route add default gw your.eth1.gateway.ip dev eth1
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' > ~/eth1.ip
route add default gw your.eth0.gateway.ip dev eth0
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' > ~/eth0.ip

```

in conky
```

eth0 IP:$alignr${exec cat ~/eth0.ip}
eth1 IP:$alignr${exec cat ~/eth1.ip}
```

---

