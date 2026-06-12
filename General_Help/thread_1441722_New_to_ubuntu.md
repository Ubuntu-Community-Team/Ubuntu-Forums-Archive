---
title: "New to ubuntu"
date: 2010-03-29
forum: General Help
---

### Post by Jonesy45 on 2010-03-29
hey everyone first post here so im putting out the "NOOB ALERT"
so firstly hello =)

well im a recent convert ubuntu after loosing it with windows haha
but im having some trouble...
i have a DELL dimension 1100 pentium 4 machine.
i cant get the internet to work i suspect that its driver related and i downloaded some drivers but have no idea how to install them so if someone could point me to a post that'd be great =)

secondly i have a Microsft Elite Blueltooth Keyboard and mouse and i managed to connect them but they tend to disconnect themselves every now and again
i suspect this is also driver related but i also secrelty think its cause its made by microsoft ;) 


thanks in advance for any help given 
Jonesy

---

### Post by NickJones on 2010-03-29
How are you connecting to the Internet? Wireless? Through Ethernet?

---

### Post by Jonesy45 on 2010-03-29
sorry i meant to put its connecting through a 10/100 intel integrated network port thingo haha

---

### Post by 3rdalbum on 2010-03-29
> **Jonesy45 said:**
> sorry i meant to put its connecting through a 10/100 intel integrated network port thingo haha

Then it's not lack of drivers; Ubuntu comes with drivers built-in for pretty much everything Intel makes.

What's probably happening is that your router is not sending the DNS addresses to the computer. You can manually put those in - go to the Network Manager applet on your panel (it's a little to the left of the clock).

Right-click it and choose Edit Connections. Click on your wired connection there and hit Edit, then go to the IPv4 Settings tab. Under Method, choose "Automatic (DHCP) Addresses Only". Under the DNS Servers field, put:

```
208.67.222.222,208.67.220.220
```

Apply your changes, disconnect and reconnect and you should be able to surf the web again using the OpenDNS server. You can now look on your ISP's website to find out their DNS addresses and use them instead of OpenDNS... or stick with the OpenDNS service if you want.

---

### Post by ibuclaw on 2010-03-29
[QUOTE=3rdalbum;9044060]Then it's not lack of drivers; Ubuntu comes with drivers built-in for pretty much everything Intel makes./QUOTE]

Further testing that you don't have a function DNS server for name resolution would be to check the contents of:
```
/etc/resolv.conf
```

And to try pinging a location by name and IP address.

Regards
Iain

---

### Post by Jonesy45 on 2010-03-30
> **3rdalbum said:**
> Then it's not lack of drivers; Ubuntu comes with drivers built-in for pretty much everything Intel makes.

What's probably happening is that your router is not sending the DNS addresses to the computer. You can manually put those in - go to the Network Manager applet on your panel (it's a little to the left of the clock).

Right-click it and choose Edit Connections. Click on your wired connection there and hit Edit, then go to the IPv4 Settings tab. Under Method, choose "Automatic (DHCP) Addresses Only". Under the DNS Servers field, put:

```
208.67.222.222,208.67.220.220
```

Apply your changes, disconnect and reconnect and you should be able to surf the web again using the OpenDNS server. You can now look on your ISP's website to find out their DNS addresses and use them instead of OpenDNS... or stick with the OpenDNS service if you want.

hey guys tried this but had no luck..... 
Mozilla doesnt get a signal

---

### Post by shikhar_sharma on 2010-03-30
You forgot to mention that how exactly are u trying to connect.is it a pppoe connection,a dsl,a cable modem?you can tell us the steps that u use to perform in windows to create a connectiion and then it would be much easier for us to troubleshoot.

---

### Post by Chame_Wizard on 2010-03-30
type in```
ifconfig
```

---

### Post by Jonesy45 on 2010-03-31
ok so after Tedious hours following google instructions i just re-installed the whole OS and now internet works fine thanks ppl

just trying to get the bluetooth k/b and mouse working now

---

