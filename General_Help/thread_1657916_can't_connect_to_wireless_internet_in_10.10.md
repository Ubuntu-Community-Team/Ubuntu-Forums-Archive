---
title: "can't connect to wireless internet in 10.10"
date: 2011-01-01
forum: General Help
---

### Post by eulnuj on 2011-01-01
Ubuntu 10.10
AT@T
DSL
Wireless
2WIRE modem 


i cannot connect to the web with the above services. Even when it says "connection established" it still would not work. there is always a lock next to the server name.

help

---

### Post by gordintoronto on 2011-01-01
I'm sorry, but I can't understand what you are trying to say. You have a wireless router, but you can't browse the web? What do you mean by "server name"?

---

### Post by coldraven on 2011-01-02
Firstly connect to you router with a network cable and check that you can get online.
If you can then type "gateway.2wire.net" into your browser and login to the router.
In the wireless section check that the encryption is set to "WPA" and the access key is something you know. By default it is the 10 digit number in square brackets that is printed on the label.
You can also change the SSID to something more friendly like "JoeBloggsNetwork".
Then disconnect from the network cable, you should see JoeBloggsNetwork, click it to connect.
Then check that the settings in the Ubuntu network manager are the same as your router. Namely, WPA and the same 10 digit number or whatever you have changed it to.

On my 2wire router the default encryption was set to "WEP" which is insecure and should no longer be used.

---

