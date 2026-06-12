---
title: "Broadcast ip adress"
date: 2006-01-26
forum: General Help
---

### Post by StrikeRTM on 2006-01-26
If I use Ubuntu, the broadcast adress is not required, or atleast I dont have to type it into anywhere for the internet to work. However Kubuntu requires it. The thing is, I dont know the broadcast ip adress, so Kubuntu is a no go so far.

Since Ubutnu work's It must aquire the broadcast adress automaticaly? :confused:  Is it possible to type some kind of a command in terminal that would give me the broadcast adress that is being used in Ubuntu? Or Ubuntu doesnt require the broadcast adress at all?

Any other ideas how to find out what my broadcast adress is? I've tried the first and last adress => x.x.x.1 & x.x.x.255 && x.x.0.1 & x.x.0.255 and it wont work. The internet provider's papers do not seem to contain any information about a broadcast adress. I'm connected to the internet through 100MBit/s LAN.

-- Thank's! --

---

### Post by heimo on 2006-01-26
It's not actually ubuntu/kubuntu specific issue (maybe the configuration tool you use is different on these), but anyway - you may be able to get the correct subnet mask using online subnet calculator like this one:
[http://www.subnetmask.info/](http://www.subnetmask.info/)

Just enter your ip address to the first row and click [Calculate]. Read the "Subnet Mask:" row. 

OR: Go to the "Ubuntu" (or wherever your network works), open terminal - type ifconfig and check what's your subnet mask for eth0 (first network card, or what ever device you're using for networking). Common subnet masks look like '255.255.255.0', but it may be something like '255.255.255.248' too. If your ISPs papers use CIDR syntax (something like 192.168.0.1/29) where '29' is important number, just post it on this thread and someone will give you correct subnet mask value.

---

### Post by StrikeRTM on 2006-01-26
So, what you're saying is subnet mask ip adress = broadcast ip adress?

---

### Post by heimo on 2006-01-26
[quote=StrikeRTM]So, what you're saying is subnet mask ip adress = broadcast ip adress?[/quote]
OH no! :rolleyes: No no... I messed up. (My excuse is that it was too early morning.) But you can use the online calculator to check your broadcast address too. These are definitely different things (although related).

---

### Post by StrikeRTM on 2006-01-26
Hehe, I'm no better when I've just gotten up :) . I'll try and see if the adress that calculator gave me work's.

---

