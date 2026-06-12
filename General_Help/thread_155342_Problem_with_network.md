---
title: "Problem with network"
date: 2006-04-04
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-04
I'm on Dapper and my wireless network starts but I have to go under networking and activate it. I am using Initng and have it set to autostart but how can I make it so I don't have to do that.

Another problem: At boot I get "Network Manager could not find all the dependincies" even though I un-installed it.

---

### Post by xXx 0wn3d xXx on 2006-04-05
Would Network Manager work ? I'm going to try it and see what happens.

---

### Post by p0liX on 2006-04-05
I've got this same problem on breezy.  Once I activate wlan0 it works fine but i have to manually activate it every time I boot.  Anyway to automate this?

---

### Post by AndyCooll on 2006-04-05
You might well need to add some wireless network details to your network interfaces file.

```
sudo gedit /etc/network/interfaces
```

I add "map wlan0". And make sure there is a line which says "auto wlan0" at the end of the details about my wireless network. I also use static IP addresses so put all the details in there for gateway, network, broadcast etc. And once I'm happy that everything is working I hash out the eth0 details to prevent any conflicts

Also, under administration-->network is your wireless lan set as the default?

:cool:

---

