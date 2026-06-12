---
title: "Help!"
date: 2010-04-14
forum: General Help
---

### Post by sh0wtym3 on 2010-04-14
**Help! With NAT Port Forwarding**

This is another part of my homework assignment I need a little help on:

> Configure your virtual machine to be accessible from your host machine (the machine the VB is installed on). This requires you to configure your forwarding ports for your virtual machine. I suggest you read the virtualbox documentation here: [http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation). You should read section 6.3.1 Configuring port forwarding with NAT. If this is working you should be able to access your virtualbox server by typing your IP address of your host machine into the browserI opened up the command prompt on my Windows host machine and typed the following:

> 
VBoxManage.exe setextradata minime "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol" TCP
VBoxManage.exe setextradata minime "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort" 22
VBoxManage.exe setextradata minime "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort" 2222
This is what I'm assuming I was supposed to do, according to so some random googling and [http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation). But when I type in the IP address of my windows machine into the Mozilla browser both on the host machine (and even inside the Ubuntu virtual machine), nothing happens?


EDIT: Sorry for the vague thread title I hit submit too soon, I meant to type more

---

