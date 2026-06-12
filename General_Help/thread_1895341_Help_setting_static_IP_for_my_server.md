---
title: "Help setting static IP for my server"
date: 2011-12-14
forum: General Help
---

### Post by paraplegicpanda on 2011-12-14
Okay, so I'm not having any major troubles, I just need some help understanding what I'm setting so that I can get my new LAMP server hooked up to the internet.

I've got a Win7 box as my main machine (gotta have my Adobe suite) and it's connected to the internet through my phone wirelessly. The box is also connected to a router via ethernet cable. The router has DHCP disabled so it's essentially a switch. Both the wireless and the ethernet are configured with static IPs and I'm using ICS to share the wireless internet to the ethernet.

I also have a laptop running Ubuntu 11.10 server connected to the router. Here's where my issue lies. I'm not sure what I need to set for the network interface. I'm using the tutorial from [here]("http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html") to set the static IP. It says:
> Edit /etc/network/interfaces and enter your ip address details (in this example setup I will use the IP address 172.19.0.10):
```
sudo vi /etc/network/interfaces
```
Now enter the following, save the file and exit (In vi, ESC, then ZZ to save and exit).

# The primary network interface

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1

Now you need to restart your network services using the following command:
```
sudo /etc/init.d/networking restart
```
You need to setup manually DNS servers in resolv.conf file when you are not using DHCP.
```
sudo vi /etc/resolv.conf
```

What's confusing me is what numbers to put where in [FONT="Courier New"]/etc/network/interfaces[/FONT]. I know that [FONT="Courier New"]address[/FONT] should be my server's static IP and the [FONT="Courier New"]netmask[/FONT] should be the normal [FONT="Courier New"]255.255.255.0[/FONT] but I'm not sure what I'm supposed to put in for [FONT="Courier New"]network[/FONT], [FONT="Courier New"]broadcast[/FONT], or [FONT="Courier New"]gateway[/FONT].

I *think* [FONT="Courier New"]broadcast[/FONT] should be the same as my server's static IP. I assume that [FONT="Courier New"]network[/FONT] should be the same as my [FONT="Courier New"]gateway[/FONT]. My [FONT="Courier New"]gateway[/FONT], however, could be any number of IPs.

It could be the IP of the ethernet connection on the Win7 machine since that's essentially what the server is connected to through the switch. It could also be the IP of the wireless NIC in the Win7 machine since the ICS could be allowing the server to pass straight through the wired connection to get to the connection (I'm not positive how ICS works in this regard, I just know it should allow one network to connect to another).. It could ALSO be the IP of the phone that is essentially the modem in this case.

For reference, here's a list of the IPs I'm using:
(Assume all IPs are 192.168.2.x)
[FONT="Courier New"]Server
- IP:      200
- Gateway: ?
Win7 Box (Ethernet NIC)
- IP:      201
- Gateway: 202
Win7 Box (Wireless NIC)
- IP:      202
- Gateway: 254
Phone (Modem)
- IP:      254
- Gateway: N/A[/FONT]

The connection between the Win7 box and the phone is working fine so there aren't any issues there. I can also ping the ethernet NIC from the server so it seems that the gateway is probably my only issue.


So what should I do? I would be happy with either some help figuring out which numbers go where or a better solution to my problem. Thanks in advance!










P.S. - My Google-fu turned up plenty of results on setting up static IPs, setting up bridges and ICS but none of them covered my specific configuration or anything that would correlate to it. I was also unable to find anything I understood about the gateway/broadcast/etc stuff.

---

### Post by matt_symes on 2011-12-14
Hi

Your network address will be the subnet of your lan

network 192.168.2.0

with zero on the end as you have a class C subnet address.

The broadcast address will be the broadcast address of the LAN.

broadcast 192.168.2.255

IIRC, You need to route to the ip address of the Ethernet card on the w7 box for your client ubuntu machine.

Therefore i think the gateway address should be the IP address of the Ethernet card on the w7 box.

gateway 192.168.2.201

In summation this should work (hopefully)
```

auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.201
```[FONT=Courier New]

[/FONT]Never tried this with a Windows ICS server though, so i hope it works.
[FONT=Courier New]
[/FONT]Kind regards

---

### Post by paraplegicpanda on 2011-12-14
Victory! I'm updating apt right now over the web so your post got me up and running! Thanks so much for the help.

---

