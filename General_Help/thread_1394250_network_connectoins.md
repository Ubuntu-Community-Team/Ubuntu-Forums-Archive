---
title: "network connectoins"
date: 2010-01-30
forum: General Help
---

### Post by drdob on 2010-01-30
When I boot my computer tries to automatically start my network card, but with a new ‘network’ if I disconnect and try to connect manually it try to look for a new network, when I have one that does work, but it ignores it and try looking for a new one. In the “network connections box” it comes up auto and my network. What have I switch on , or not switched off ?? any of you good people out got a answer?? . thank you.

---

### Post by blueshiftoverwatch on 2010-01-30
Are you talking about the NetworkManager Applet?

---

### Post by drdob on 2010-01-30
blueshftoverwach.
                    yes that is what you call it. but why does it try to make a new connection each time, i should have said i am running 9.10   thank you for replying Dr Dob

---

### Post by blueshiftoverwatch on 2010-01-31
I don't know the answer to your problems. NetworkManager worked fine for connecting to the network automatically using DHCP. I just edited a text file and gave my computer a static IP address instead of using DHCP.

Long story: I posted a [thread]("http://ubuntuforums.org/showthread.php?t=1389347") about it here.

Shory story: Amend */etc/network/interfaces* with whatever your information is:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address xxx.xxx.xxx.XXX
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
```

---

### Post by drdob on 2010-01-31
thank you for your reply. i will give it a try.if that does not work..... i will swear at it...:-\"
thank you Dr Dob

---

### Post by blueshiftoverwatch on 2010-01-31
> **drdob said:**
> thank you for your reply. i will give it a try.if that does not work..... i will swear at it...:-\"
thank you Dr Dob
Just make sure that you either:
1. Set your router's DHCP settings to start at a number above the statically assigned IP of your computer.
2. Set your computer's static IP to above the range of your router's DHCP assignable addresses

Otherwise you might find that you can't connect to the Internet one day because your computer's IP address is already in use by another device.

---

### Post by bakegoodz on 2010-01-31
I apologize if I didn't follow you correctly. I think your saying that you set a static ip on a network that has a dhcp server. Very annoying function of just about every automatic network manager on linux, it will dump your static setting after it sees a dhcp server. The only way I could find to fix it is to kill the dhclient.

---

### Post by blueshiftoverwatch on 2010-01-31
> **bakegoodz said:**
> I apologize if I didn't follow you correctly. I think your saying that you set a static ip on a network that has a dhcp server. Very annoying function of just about every automatic network manager on linux, it will dump your static setting after it sees a dhcp server. The only way I could find to fix it is to kill the dhclient.
I have NetworkManager installed and it hasn't doing anything to my static IP yet. I think if it sees that you've manually modified the text file (as I did) it won't try to change your settings.

---

### Post by bakegoodz on 2010-02-06
For a couple years now Network manager just ignores the /etc/network/interfaces file. You can probably manually tell it to use setting in that file with tools like ifup, ifdown, ifconfig. If you want to use that configure file instead of Network Manager you will need to uninstall Network Manager.

---

