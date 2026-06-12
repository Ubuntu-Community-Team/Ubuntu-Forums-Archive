---
title: "Ubuntu server ssh"
date: 2012-03-10
forum: General Help
---

### Post by bender1 on 2012-03-10
]I have installed ubutu 10.04 server on a vbox ,and installed ssh on it so that i can use putty to access it.
This is what i did
```
apt-get install openssh-server
```

Then i went to putty and install the ip that i got from ifconfig ,but it will not connect .

---

### Post by _0R10N on 2012-03-10
You should check that putty is trying to use the right port (22 by default). Additionally, you should try to execute a ping command to the virtualized Ubuntu installation, so you can be sure that there's network connectivity. This is not always the case, it depends whether you're NATing,bridging, etc. the network connectio for your virtual machine.

---

### Post by codemaniac on 2012-03-10
To test that your ssh server working, you can try to ssh into your local host .

```
ssh localhost
```

check if you are getting something like below .
> The authenticity of host ‘localhost (127.0.0.1)’ can’t be established.
RSA key fingerprint is 98:8a:b8:b2:9e:8a:84:e0:d4:08:27:fb:74:f0:de:d4.
Are you sure you want to continue connecting (yes/no)?

---

### Post by papibe on 2012-03-10
The easiest way I know: change the network adapter to bridge:
[LIST]
[*]Turn off your virtual machine.
[*]Select the machine on the list of virtual machines.
[*]Go to Machine -> Settings -> Network.
[*]There, set Adapter 1's field "Attached to" to the value "Bridged Adaptor".
[*]Turn on your VM.
[*]Get the new VM's ip using ifconfig (now it should be in the same network that the rest of the LAN).
[*]Connect from outside using ssh or putty (port 22).
[/LIST]
Hope it helps, and tell us how it goes.
Regards.

---

### Post by bender1 on 2012-03-10
> **codemaniac said:**
> To test that your ssh server working, you can try to ssh into your local host .

```
ssh localhost
```

check if you are getting something like below .

I got this.I ping my host from vbox and it responded but when i ping my vbox(ubuntu) no response.

---

### Post by BertN45 on 2012-03-10
In Virtualbox go to your VM network tab and change the "attached to" selection fron NAT to Bridged Adaptor. NAT blocks all traffic to your VM, only outgoing request/replies are supported. With bridged your VM becomes part of your LAN

---

