---
title: "How Can I block people from using my wireless network"
date: 2011-01-01
forum: General Help
---

### Post by Florenceblues on 2011-01-01
Hai! I was wondering how can I see who is using my wireless router to connect to my Internet connection, and how can I block them so they can't access it.  THX :)

---

### Post by TeoBigusGeekus on 2011-01-01
Well, have you applied any encryption to your wireless network?
If not, do it now (wpa2 recommended).

---

### Post by ruben_linux on 2011-01-01
set your router up so that only specific MAC Addresses are allowed.
Hide your SSID.

there are many howto in the net:p

---

### Post by Florenceblues on 2011-01-01
Well I have a password on it. However I wanted to block out my brother from using it. He knows the password.

---

### Post by ruben_linux on 2011-01-01
change the pass

---

### Post by TeoBigusGeekus on 2011-01-01
> **Florenceblues said:**
> Well I have a password on it. However I wanted to block out my brother from using it. He knows the password.
Solution 1: Punch him on the nose.
Solution 2: Change wifi password, as well as your router password (so he can't change the wifi password).
Solution 3: As ruben_linux said, whitelist your mac address only and let him wonder why he can't connect.

---

### Post by perspectoff on 2011-01-01
Of course, you always want to use connection security for all connections. Old routers used WEP keys; newer ones use WPA2. The security key prevents secure connections and prevents random passersby from connecting. 

On a Linksys home router, for example, this would often be found in the Wireless -> Wireless Security --> Security mode settings. You can set the key there and then copy your chosen key to each computer that will connect to the network.

You could also stop broadcasting the SSID (which on Linksys home routers is often a Wireless -> Basic Wireless Settings -> Wireless SSID broadcast setting), although this sometimes makes it difficult for your approved computers to automatically connect if they tend to connect to several different routers. (I personally don't do this).

The most secure way (IMO) is to restrict the MAC addresses allowed to connect to your wireless router.

This is a pretty iron-clad way to limit who can connect to your wireless network. I use it on all my wireless networks.

On a Linksys home router, for example, Wireless -> Wireless MAC filter -> Edit MAC filter list.

You will need to find out the wireless networking card's MAC address for each computer and enter it into this list. 

On any Linux computer you can discover the MAC address of the wireless interface (usually wlan0 or possibly wlan1) by using the command-line terminal (Terminal or Konsole) and entering

ifconfig

This will display the Hardware Address (HWaddr) for each networking interface (the HWAddr is the same as the MAC address). Copy the HWAddr for wlan0 (or wlan1, depending on which one is your primary wireless interface) into the MAC filter list on the router.

The MAC address should be entered in the format 12:34:56:78:aa:bb (make sure to include the colons).

Once the MAC addresses for the wireless interfaces of every computer (for which you intend to allow access to the wireless network) is entered, then enable filtering by choosing the "Permit only PCs listed to access the wireless network" option (or something similar.

It is very unlikely that an intruder could spoof one of the MAC addresses on the filter list and also acquire the WPA2 (or WEP) security key for your network as well. The combination of these two security measures would make a wireless network pretty secure. An intruder would have to physically have access to a computer on the network and copy the details onto their computer. (But if they had that type of physical access, they already would be on the network, wouldn't they?)

---

### Post by QLee on 2011-01-01
> **Florenceblues said:**
> Well I have a password on it. However I wanted to block out my brother from using it. He knows the password.

What you have is a social issue, not a software issue. As long as he has physical access to the router and sufficient knowledge, he can just do a manual reset on the gateway (I assume it's an Internet gateway) and then he could lock you out.

You need to be able to agree on boundaries and have him respect your wishes if you have the authority to deny him use of "your" router. If it is a family router, then there still has to be some compromise and agreement.

---

### Post by Florenceblues on 2011-01-01
How can i see wht my network is called?

---

### Post by perspectoff on 2011-01-01
> **QLee said:**
> What you have is a social issue, not a software issue. As long as he has physical access to the router and sufficient knowledge, he can just do a manual reset on the gateway (I assume it's an Internet gateway) and then he could lock you out.

You need to be able to agree on boundaries and have him respect your wishes if you have the authority to deny him use of "your" router. If it is a family router, then there still has to be some compromise and agreement.

Ha ha. Sounds funny but it is a real-world security issue.

I actually have my routers at work (and at home, actually) enabled with a password so that the settings can't be changed without the router password. I then have them locked in an inaccessible cabinet or box. 

I also do this on all my computers, by the way, on which I have both a BIOS password and a lock on all the cases (to prevent a hardware reset from the motherboard). I then restrict bootup to a password-protected hard drive (so that LiveCD's/ LiveUSB's can not be booted and used to alter the hard drive).

Not only do troublesome siblings (or kids in my case) try to screw things up, but also disgruntled or otherwise meddlesome employees.

---

### Post by desnaike on 2011-01-01
Demand half the cost.

---

### Post by sgosnell on 2011-01-01
If he has physical access to the router, and the proper knowledge, you can't keep him out.  But it sounds like neither of you knows much about how routers work, so a new password and MAC filtering might work.  Keep in mind that the admin password for the router and the wireless passwords are different things, although it's possible to use the same password for both.  That is never a good idea.  

As already stated, if he knows how, he can reset the router to factory defaults, then put new passwords on it so that you can't access it until you do the same.  That's a never-ending war.  If you can lock the router inside a secure area, so that he can't get physical access, you're better off, but keeping your brother out of anywhere in the house is probably hopeless.  You need to reach an agreement to let him use the router, but with limited access.  Set a new admin password on the router, so he can't change anything, and live with it.

To see who is on the router, you can access it in your browser.  The usual IP address for a router is 192.168.1.1 or 192.168.0.1.  For Netgear routers, it may be 10.0.0.1.  You can find the default admin username and password through Google, it's different for different brands.  It probably hasn't been changed from the default.  Change both as soon as you can.  Somewhere in the menus, depending on the brand, will be a table of DHCP clients.  You can see every computer that is on the network.  Refresh the list to see current clients, as it may be stale.

---

### Post by Florenceblues on 2011-01-01
Thanks you guys I got it :). I actually don't care if he uses the internet, but my mom wants him off it. So thank you!

---

