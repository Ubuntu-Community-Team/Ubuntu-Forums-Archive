---
title: "Trouble with internet connection in ubuntu 9.10"
date: 2010-05-12
forum: General Help
---

### Post by amature_moghli on 2010-05-12
I use a broadband connection to connect to the internet powered by BSNL. I have issues with my modem and hence cannot configure it for pppoe over the bsnl site. So in win7 i use ' boradband connection which requires username and password' to connect to the net. Can anyone suggest a work around for this?

---

### Post by dineshs on 2010-05-13
Try this
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
ie first run this command in a terminal to configure the connection with username and password
```
sudo pppoeconf
```
Now to connect use
```
pon dsl-provider
```
and to disconnect,
```
poff dsl-provider
```
> I have issues with my modem and hence cannot configure it for pppoe over the bsnl siteYou mean you are not able to configure your modem in pppoe mode with the username and password given by BSNL?What is the problem and what is the modelname of your modem?

---

### Post by amature_moghli on 2010-05-23
I tried the above mentioned code but I couldnt still fix the problem. 

I have got a certain 'Device not managed' status in the network connection toolbar. 
I tried installing drivers given with the hardware, no luck with that as well..

The modem I use is SmartAx MT841 of Huawei, provided by BSNL themselves..

---

