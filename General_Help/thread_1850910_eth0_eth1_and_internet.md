---
title: "eth0 /eth1 and internet"
date: 2011-09-27
forum: General Help
---

### Post by Giancarlo.Pasquini on 2011-09-27
Hi all,
I had a computer connected to a router and internet via eth0.
Eth0 failed (but from Sw point of view is still working) and could not be replaced because it is on the motherboard. I have added another card which is now eth1.
I want to connect to the router and internet via eth1.
I have modified the network  file to give 2 different static address to eth0 and eth1 . Eth1 has the router range of Ip address.
If I restart the networking manually with networking restart. Eth1 connects to the router. If config shows the correct address as well the router web interface but there is no connection to internet.
What else am I missing (peraphs firewall rules?) or what am I doing wrong?
help would be appreciated. Thank you

---

### Post by haqking on 2011-09-27
> **Giancarlo.Pasquini said:**
> Hi all,
I had a computer connected to a router and internet via eth0.
Eth0 failed (but from Sw point of view is still working) and could not be replaced because it is on the motherboard. I have added another card which is now eth1.
I want to connect to the router and internet via eth1.
I have modified the network  file to give 2 different static address to eth0 and eth1 . Eth1 has the router range of Ip address.
If I restart the networking manually with networking restart. Eth1 connects to the router. If config shows the correct address as well the router web interface but there is no connection to internet.
What else am I missing (peraphs firewall rules?) or what am I doing wrong?
help would be appreciated. Thank you

not sure i fully understand what you read.

but from what i think you are saying you will need to edit the following file if you havent already ?

/etc/udev/rules.d/70-persistent-net.rules

as that contains the interface name aliases

---

### Post by Giancarlo.Pasquini on 2011-09-27
Thank you for your reply.
I changed the file as you suggested changing eth0 for eth1 and viceversa. 
There has been no change.
What I mean is that I can ping the router and the other pc on my lan but I can not ping outside my own network.
The web browser says connected to (any site) but  no data is exchanged.
The router monitor shows the Ubuntu PC connected to the router and to the internet.
After the first swap of et0 eth1 I lost the network applet and I can not get back for now.
Can ip tables have something to do with this?
Thanks

---

### Post by wt8008 on 2011-09-27
You do not really need to assign a static IP to your non-working interface. All laptop users have two networking interfaces although one is wireless and the other is ethernet, but it is the same idea.

Can you test with getting a DHCP IP from your router instead of manually setting one, perhaps one of your static configurations has a typo in it.

My laptop's iptables is all empty, I have never set any rules on it before.

---

### Post by pjd99 on 2011-09-27
Looks like you're missing DNS servers for that interface. DHCP, or a correct manual configuration should solve your problems.

To test that dns is the problem, put [http://74.125.237.18/](http://74.125.237.18/) into an address bar and see if you can get to Google.

---

### Post by Giancarlo.Pasquini on 2011-09-28
Thank you for your help. Problem is nearly solved.
What happens is that DHCP is not working and on my manual configuration I have not set the DNS correctly.
The browser navigates to 74.125.237.18

I have tried with a live Ubuntu CD as well and DHCP is not working also. It was working before installing the extra Ethernet.

It seems I am stuck with a manual configuration. Can you tell me how to set up DNS via terminal. 

thank you.

---

### Post by Giancarlo.Pasquini on 2011-09-28
At last I am writing this from my PC.
The proble was cuase by having an Eth0 interface working for the Sw but faulti in paractice. 
In the network file I have put both ETH0 and ETh1 with DHCP but I have inverted their positions in the file . Now it works.
Thank you all for the help and the patience

---

### Post by haqking on 2011-09-28
> **Giancarlo.Pasquini said:**
> At last I am writing this from my PC.
The proble was cuase by having an Eth0 interface working for the Sw but faulti in paractice. 
In the network file I have put both ETH0 and ETh1 with DHCP but I have inverted their positions in the file . Now it works.
Thank you all for the help and the patience

ha sorry didnt get back earlier, been replacing the fan in my thinkpad ;-)

Glad you got it sorted, remember to mark the thread as solved using thread tools.

Cheers

---

### Post by Giancarlo.Pasquini on 2011-09-28
I jumped the gun. Not solved after all.
The only way I have to make it work is to put the following lines in the network configuration file.

auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp

When I issue the network restart command for the first time the eth0 receives the router address range  (the faulty one) and Eth1 a different network. In this case the network does not work.

If I issue the network restart command a second time then Eth0 receives the different network address  and Eth1 the router range. In this case it works.
This process can be repeated at lib.

This means that I can connect to internet only if I send manually a network restart every time.


Removing Eth0 from the network file does not help.

Is there a way to black list the faulty Eth0. The Eth0 is built on the main board and can not find its name with the lspci command. I only know its mac address. ?

Thanks

---

### Post by grahammechanical on 2011-09-28
Can I suggest coming at this from a different direction? Is it possible to disable the on-board ethernet adapter (eth0) in the BIOS? That way only the new ethernet card will be detected. The new card may then become eth0.

Just a crazy idea. I get them sometimes.

Regards.

---

### Post by Giancarlo.Pasquini on 2011-09-28
It has been the first thing that came to my mind also. Unfortunately it is not possible to do it. At least with the bios editor supplied with the PC.
It was worth a try anyway

---

### Post by pjd99 on 2011-09-28
Would you be able to post the output of lspci and lsmod? We might be able to blacklist the driver if we can find it (and it's not the same as the pci adapter).
```

lspci | grep [Ee]thernet
lspci | grep [Nn]etwork
lsmod

```

---

### Post by JKyleOKC on 2011-09-28
> **Giancarlo.Pasquini said:**
> Is there a way to black list the faulty Eth0. The Eth0 is built on the main board and can not find its name with the lspci command. I only know its mac address. ?

ThanksYes, there's a way to do it and it's quite simple, just not extremely obvious. Earlier you changed the udev rules file by swapping the eth0 and eth1 strings but it did not work. You were very close at that time. The trick is to edit the "NAME=" value.

I have two NICs in addition to a built-in adapter on this box, and the built-in developed problems. I had to change the 70-persistent-net.rules file to reassign interface names to the cards. Here's the entry for my non-functional built-in adapter on this box: ```
# PCI device 0x10de:0x03ef (forcedeth) -- unused
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Blue"]00:26:18:70:fb:c5[/COLOR]", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth9[/COLOR]"

```The value in red is the one to change, but you need to verify also that the one in blue is NOT changed.

The address in blue is how the hardware identifies the adapter and the value in red is the name that the software will use for it. Swapping the red values between the two cards, but leaving the blue values alone, will effectively force the name to always apply to the same card, so you don't really need the interfaces file to deal with "eth1" since the new card will become "eth0" because of the 70-persistent-net.rules file's action.

Changes to these files won't have any effect until you restart the system. You don't want to have any entries for eth1 in the interfaces file or anywhere else...

You may see error messages in the logs after doing this, since the built-in card's interface never gets completely initialized. If so, you can comment out the card's entry in the rules file. The renaming of the new card will still take place and make it work. That's how this box is now working for me; I removed the comment character above to explain to you how it works.

---

### Post by Giancarlo.Pasquini on 2011-09-29
This time it is really solved. The persistent rules file did the trick.
Thank you all for your help and support. This time I would not have made it on my own

---

