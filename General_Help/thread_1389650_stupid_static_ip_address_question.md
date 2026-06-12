---
title: "stupid static ip address question"
date: 2010-01-24
forum: General Help
---

### Post by skibster on 2010-01-24
so i got these instrutions from the 9.10 faq....

[LIST=1]
[*]Right click the NetworkManager icon in the system notification area.
[*]Click *Edit Connections*.
[*]Click the *Wired* tab.
[*]Select the connection and click **Edit**.
[*]Click the *IPv4* tab.
[*]Choose *Manual* from the *Method* drop down.
[*]Enter your details and click **OK**.
[*]Click **Close**.
[/LIST]specific too number 7, i have 3 questions,
 
a) how do i get the subnet mask and gateway? if i already have a static ip adress on windows, will the gateway and mask change?
 
b) if i have two DNS servers, do i just put the primary? can i put the alternate in after a comma or semicolon?

---

### Post by hawthornso23 on 2010-01-24
Experiment. The worst that can happen is that it doesn't work.

However if you are multibooting into windows and have a functional network setup with static IP address there, then copying your network settings (IP address, network mask, DNS servers) from windows will work. The basic network layer doesn't know what operating system you are running.

---

### Post by skibster on 2010-01-24
i plan on dual booting, so shouldnt be any problems
im switching tonight when i get home so i might decide while im partitioning to just install ubuntu and thats it.
my friend says he has done it and can't remember, something with ifconfig to find all the network info?

---

### Post by sisco311 on 2010-01-24
> **skibster said:**
> i plan on dual booting, so shouldnt be any problems
im switching tonight when i get home so i might decide while im partitioning to just install ubuntu and thats it.
my friend says he has done it and can't remember, something with ifconfig to find all the network info?

run
```
ipconfig
```
in Windows to get the network configuration values.

The subnet mask is usually 255.255.255.0, the gateway is usually the ip of the router/modem (192.168.0.1, 192.168.1.1 or 192.168.2.1).

Use a comma to separate DNS addresses.

---

### Post by skibster on 2010-01-24
thank you thank you thank you!
 
should be good now, just a bit skeptical for the change, but thanks to all of the support i think it should be a pretty smooth transition

---

