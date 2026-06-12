---
title: "Giving VirtualMachine an IP"
date: 2010-02-19
forum: General Help
---

### Post by Muscovy on 2010-02-19
I set up a VM in VirtualBox to do some testing and give a few people pseudo-root access. However, the VM doesn't have a unique IP. How can I set one?
  Guest is just Ubuntu Server.

---

### Post by GolemXIV on 2010-02-19
You need to set up a network bridge.

[https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)
> Connecting a virtual machine  through NAT will allow the guest to connect to systems on the network  (including the host or some website). A machine on the network will not  be able to initiate a connection to the guest though. But typically, one might want to connect from the host  to the guest (as is the case when the guest runs a web server or an ssh  server). For this use case, bridging can be used (one must be aware that  bridging will make a virtual machine visible to the network so it must  be secured beforehand)

---

### Post by Muscovy on 2010-02-19
I tried setting the Bridged Adapter, but I see no changes.

---

### Post by San_SS! on 2010-02-19
What is the netowork environment? If you have a private network to connect to, you should set the VM to bridge, and set up a static IP in the guest.

---

### Post by Muscovy on 2010-02-19
It's a private network (but with no connection password). I did the bridge, no result. Nit sure what you mean by assign static IP, I thought that was the end result.

---

### Post by pirateghost on 2010-02-19
virtualbox assign network as network bridge and make sure your host has network access.

in the guest:
```
sudo nano /etc/network/interfaces
```
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 1.1.1.9
        netmask 255.255.255.0
        gateway 1.1.1.1

```

substitute the addresses for addresses in your subnet

---

### Post by Muscovy on 2010-02-19
I'm guessing "address" is the host's address, but where do I get the other two?

---

### Post by pirateghost on 2010-02-19
> **Muscovy said:**
> I'm guessing "address" is the host's address, but where do I get the other two?
address will be the address that you want your guest to have.

netmask depends on your network.  most of the time it will be 255.255.255.0
 
gateway is the ip address to the router

dont think of your virtual machine having ANYTHING to do with your HOST.  it is a machine ALL its OWN.  it just happens to share hardware, thats it.

---

### Post by Muscovy on 2010-02-19
I've put the numbers in. I picked an unused IP, gave it the gateway IP, and found the netmask (255.255.255.0) with ifconfig. However, now the guest has no connection. Do I need to reboot the router?

---

### Post by pirateghost on 2010-02-19
> **Muscovy said:**
> I've put the numbers in. I picked an unused IP, gave it the gateway IP, and found the netmask (255.255.255.0) with ifconfig. However, now the guest has no connection. Do I need to reboot the router?
no.  you need to do nothing with your router at this point

give us a layout of your host system.
did you reboot the guest after making the network adapter bridged?

---

### Post by Muscovy on 2010-02-19
The host is Ubuntu 9.10, 64bit, on two cores. And yeah, I rebooted the VM, since it's easier than finding the specific method the reload the file.

---

### Post by pirateghost on 2010-02-19
> **Muscovy said:**
> The host is Ubuntu 9.10, 64bit, on two cores. And yeah, I rebooted the VM, since it's easier than finding the specific method the reload the file.
reloading the file consists of 

sudo /etc/init.d/networking restart

you might want to learn some commands if plan on using ubuntu server

but what is the network set up?

is your vbox guest bridged to eth0?

---

### Post by Muscovy on 2010-02-19
It's bridged to wlan, I would assume because my connection is wireless.

I do know general commands, like sudo, ls, chmod, halt, and so on.

---

### Post by pirateghost on 2010-02-19
bridged to wlan might be the problem.  i havent had any luck bridging with my wireless in VBox.  maybe someone else has?

---

### Post by Muscovy on 2010-02-19
Later on I'll try plugging in an ethernet cable and see if it works.

---

### Post by pirateghost on 2010-02-19
> **Muscovy said:**
> Later on I'll try plugging in an ethernet cable and see if it works.


wait,

you are assuming that its bridged to wlan because that is how you are connecting to the network, but vbox assumes you will be bridging with eth0 by default....wlan is a secondary or tertiary connection in most cases

---

### Post by Muscovy on 2010-02-19
It claims to be using wlan. When I bridged it, I kept that setting.

---

### Post by pirateghost on 2010-02-19
> **Muscovy said:**
> It claims to be using wlan. When I bridged it, I kept that setting.
ok.  just checking.  like i said, the last time i messed with trying to get vbox or vmware workstation working with wlan as the bridged network, it didnt work out so well.

---

### Post by GolemXIV on 2010-02-19
What version of vbox are you using, I just set up a bridged wifi connection for my xp vm 
using vbox 3.0.8_OSE r53138 and it worked without any fuss.

---

### Post by Muscovy on 2010-02-20
Somehow, I managed to get it to show up with a unique LAN IP just by playing with the bridge setting. But I tried checking whatismyip.com in Lynx, and my world IP is the same as my host.

---

### Post by pirateghost on 2010-02-20
your world IP should be the same no matter what computer you are on in the same network.  it should be the public IP of your router.  everything behind the router is NAT'ed which means that everything behind the router should be in a private subnet (192.168.1.0/24 for example).  nothing beyond your router on the outside world will be aware of anything behind your router on your private network unless you advertise it as a service and forward a port.

---

### Post by Muscovy on 2010-02-20
Right. :rolleyes: 255^3 IPs isn't that many.

---

