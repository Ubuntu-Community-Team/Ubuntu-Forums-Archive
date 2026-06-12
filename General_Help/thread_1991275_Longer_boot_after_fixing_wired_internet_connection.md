---
title: "Longer boot after fixing wired internet connection"
date: 2012-05-30
forum: General Help
---

### Post by Nando88 on 2012-05-30
I'm using Lubuntu 12.04, and I wasn't able to connect to the internet via a wired connection, but I finally found a fix in this page:
**  **

       
   
 [Show Details]("http://36ohk6dgmcd1n-c.c.yom.mail.yahoo.net/om/api/1.0/openmail.app.invoke/36ohk6dgmcd1n/11/1.0.35/us/en-US/view.html/0#") 
         [http://ubuntuguide.net/fix-cannot-connect-to-wired-internet-problem-in-ubuntu-or-ubuntu-vmware-guest](http://ubuntuguide.net/fix-cannot-connect-to-wired-internet-problem-in-ubuntu-or-ubuntu-vmware-guest)
The thing is that now I have to wait from 2-3 minutes every time I turn on my computer,.
Can someone please tell me how to fix this problem, because I don't want to have that long boot time?
Thanks in advance!

---

### Post by idoitprone on 2012-05-30
> **Nando88 said:**
> I'm using Lubuntu 12.04, and I wasn't able to connect to the internet via a wired connection, but I finally found a fix in this page:


       
   
 [Show Details]("http://36ohk6dgmcd1n-c.c.yom.mail.yahoo.net/om/api/1.0/openmail.app.invoke/36ohk6dgmcd1n/11/1.0.35/us/en-US/view.html/0#") 
         [http://ubuntuguide.net/fix-cannot-connect-to-wired-internet-problem-in-ubuntu-or-ubuntu-vmware-guest](http://ubuntuguide.net/fix-cannot-connect-to-wired-internet-problem-in-ubuntu-or-ubuntu-vmware-guest)
The thing is that now I have to wait from 2-3 minutes every time I turn on my computer,.
Can someone please tell me how to fix this problem, because I don't want to have that long boot time?
Thanks in advance!

you add connecting to internet to your boot path. Now the os must wait for the internet to be connected to continue

perhaps change the default network manager to dhclient


```
sudo sh -c 'echo "dhcp=dhclient" >> /etc/NetworkManager/NetworkManager.conf'
```remove those /etc interface changes

usee the network manger to connect to internet

---

