---
title: "Static IP trouble"
date: 2010-08-26
forum: General Help
---

### Post by eriktheblu on 2010-08-26
I had my Mythbuntu box set up for dynamic IP, but then I started having fun with SSH and Mythweb which made static IP appealing. The router forwards port 80 to that box, and the only way I've been able to get shares to mount, or SSH to connect is by IP.

I tried modifying /etc/network/interfaces, but quite honestly I'm nut up to speed on networking (no idea what netmask and gateway mean). The result was that the MythTV frontend stopped communicating with the backend. That of course was unacceptable.

After restoring /etc/network/interfaces, I used the Network Connections interface and set IP to 198.168.1.150, Netmask to 255.255.255.0 (seemed standard enough) and Gateway to 198.168.1.1 (that's what the internet guides had so.....)

Now, ifconfig confirms the intended IP is set, I have no issues with front/backend interaction, and I can connect to the internet. Unfortunately now SSH, Mythweb, and the file shares are not connecting.

I'm happy to do research, but have no idea what to look for.

Potentially useful system info:
Mythbuntu 10.04 (32 bit)
Networking with wireless

---

### Post by dcstar on 2010-08-27
> **eriktheblu said:**
> 
.........
I'm happy to do research, but have no idea what to look for.

Potentially useful system info:
Mythbuntu 10.04 (32 bit)
Networking with wireless

Nothing to do with Ubuntu, fix your Router/Firewall so **it** forwards to the new IP address.

---

### Post by SlugSlug on 2010-08-27
I tend to remove network-manager and bang in /interfaces my settings


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.60
netmask 255.255.255.0
gateway 192.168.1.254
```and then also edit /etc/resolv.conf


```
nameserver 192.168.1.254
```
then config router to forward ports to that .60 address


and then kick it all off with

sudo /etc/init.d/networking restart

---

### Post by alphacrucis2 on 2010-08-27
> **eriktheblu said:**
> I had my Mythbuntu box set up for dynamic IP, but then I started having fun with SSH and Mythweb which made static IP appealing. The router forwards port 80 to that box, and the only way I've been able to get shares to mount, or SSH to connect is by IP.

I tried modifying /etc/network/interfaces, but quite honestly I'm nut up to speed on networking (no idea what netmask and gateway mean). The result was that the MythTV frontend stopped communicating with the backend. That of course was unacceptable.

After restoring /etc/network/interfaces, I used the Network Connections interface and set IP to 198.168.1.150, Netmask to 255.255.255.0 (seemed standard enough) and Gateway to 198.168.1.1 (that's what the internet guides had so.....)

Now, ifconfig confirms the intended IP is set, I have no issues with front/backend interaction, and I can connect to the internet. Unfortunately now SSH, Mythweb, and the file shares are not connecting.

I'm happy to do research, but have no idea what to look for.

Potentially useful system info:
Mythbuntu 10.04 (32 bit)
Networking with wireless

The gateway should be set to the address of your router. If your router has address 192.168.1.1 then what you have done won't work at all (but maybe there was a typo in your post where you wrote 198.168.1.1). First check the configuration of the router to verify what its' address and subnet mask are. You should set the static address of your mythbuntu within the same subnet as the router but it would be a good idea to assign it outside of the dynamic/dhcp range to avoid possible conflict.

---

### Post by eriktheblu on 2010-08-27
> **alphacrucis2 said:**
> If your router has address 192.168.1.1 then what you have done won't work at all (but maybe there was a typo in your post where you wrote 198.168.1.1). Oops, I think the typo may have been on the machine rather than the post.

I'll verify this when I get back on my network.

---

### Post by eriktheblu on 2010-08-27
That was it; I put the wrong gateway IP in.

Thanks for the help

---

