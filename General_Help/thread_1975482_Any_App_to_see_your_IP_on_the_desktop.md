---
title: "Any App to see your IP on the desktop???"
date: 2012-05-07
forum: General Help
---

### Post by gurrunaki on 2012-05-07
Hi, I'm looking for some application or something that can show ur ip in the panel desktop, like the time or the weather, I tried install giplet, but doesn't install, gave many errors.

Thanks in advance!!!

---

### Post by ivex001 on 2012-05-07
Hi gurrunaki, you can always use screenlets. I know a very usefull screenlet, but its only on desktop although.His name is Sysmonitor.

---

### Post by gurrunaki on 2012-05-07
Thnx for your fast reply, I'm going try with it and I will let u something soon, but my idea is have the option to see all the time it

---

### Post by davidvandoren on 2012-05-07
right click your connection icon and click on Connection Information.

---

### Post by gurrunaki on 2012-05-07
I didn't know about it, and is good and easy, but... I'm running firefox like a browser and I downloaded the application called Anonymox that change your IP, plus I'm running a VPN which is connected in a server in Sweden let's say... When I make right click in my icon connexion and select connection information is giving me an IP, that is always the same even if I disconnect both vpns, the anonymox one from firefox and my private one, but if I check in the websites tracemyip.org or whatismyip.com this are giving me different IP's...

Which one is the good one and how can I know that I'm surfing anonymously???

---

### Post by stinkeye on 2012-05-07
If your familiar with conky you can use it under
a 100% transparent unity panel.

The line in your conkyrc would be
```
${execi 300 curl ifconfig.me}
```
[ATTACH]217479[/ATTACH]

or you could save this script as **whatismyip** and
bind it to a shortcut key.
It will show your IP in the notification bubble.(May need to install curl)
```
#!/bin/bash

ip="$(curl ifconfig.me)" &&
notify-send "IP ADDRESS" "$ip"
```
[ATTACH]217481[/ATTACH]

---

### Post by gurrunaki on 2012-05-07
Thanks a lot I just installed it and show me the ip for some seconds, probably will back later :p
But, do you know anything how find out if the IP that shows there, is the fake one? I mean, I will not leave traces in other web pages?

---

### Post by stinkeye on 2012-05-07
You can go to  **ifconfig.me** in your web browser.
This will show your public ip everyone else sees.
You will notice it changes when you enable Anonymox in firefox.

You can also run it in the terminal
```
curl ifconfig.me
```

---

