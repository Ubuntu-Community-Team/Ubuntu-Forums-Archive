---
title: "turn off evolution alarm notify ( 12.04 )"
date: 2012-05-23
forum: General Help
---

### Post by kingmoffa on 2012-05-23
Hi, 

I recently installed 12.04 with evolution as my main email client (exchange mapi).

How do I turn evolution alarm notifications off?  Every time I start the computer it asks for my calendar password. I dont use calendar and connect to my email server via a VPN that isnt running by default. 

There isn't anything for evolution in the start up applications , where I would expect to find it and I think it lived in previous ubuntu releases.

---

### Post by Ron S on 2012-05-23
Hi 
Evolution alarm notify is still in startup Applications its just that developers decided to keep most of the applications hidden from users. just use the following command in a terminal to show all startup items.
 
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

Hope this helps

---

### Post by kingmoffa on 2012-05-23
Thats great - Thanks.

The command worked and I can now see all the startup applications.

---

### Post by dcstar on 2012-05-24
> **kingmoffa said:**
> Thats great - Thanks.

The command worked and I can now see all the startup applications.

Then **mark** the thread!

---

