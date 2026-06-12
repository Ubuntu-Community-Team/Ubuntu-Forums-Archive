---
title: "Static IP Address Config"
date: 2010-08-08
forum: General Help
---

### Post by madman100 on 2010-08-08
Hi All 

I am having problems setting up static IP address in ubuntu 10.4 32 bit desktop when i go in to the /etc/network/interfaces 

To add my static IP address all i see is auto lo
iface lo inet loopback

and not  The primary network interface
auto eth0 

i have added the infterface to this file

iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

but when i save and restart the network connection my connection is down 

Thanks 
madman100

---

### Post by lisati on 2010-08-08
This is just personal preference, but I tend to set static IP addresses in my router. This is because doing it that way, I'm less likely to run into addressing conflicts and other such difficulties if I connect one of my machines to another network.

---

### Post by dineshs on 2010-08-08
10.04 usesNetwork manager by default.You may setup static IP in NM.Please try this
```
gksudo gedit /etc/network/interfaces
```
Edit the file so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
save the file and close
If your NM icon is not there on top right of the panel(two opposite arrows) [COLOR="Magenta"]Restart your PC[/COLOR]
Now configure NM as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.110 
mask 255.255.255.0 
gateway 192.168.1.1 
[COLOR="Red"]then hit enter [/COLOR]
DNS 4.2.2.1
then click apply 
note:The IP and DNS are examples Please substitute your values

---

### Post by DeMus on 2010-08-08
> **lisati said:**
> This is just personal preference, but I tend to set static IP addresses in my router. This is because doing it that way, I'm less likely to run into addressing conflicts and other such difficulties if I connect one of my machines to another network.

I do more or less the same: the computers are set to DHCP and in the router I combined the MAC address of the network cards of the PC's to an IP address. So, when a computer boots, the MAC address is send to the router, it looks in the list and hands out the IP address. This way for the computer it is DHCP, but still with the same Ip address.

---

### Post by madman100 on 2010-08-08
Hi dineshs

I have done this before in ubuntu 9.10 by the network connection icon but for some reason when i try to set the gate address and save it does not save the gate address that i have entered only saves it as 0.0.0.0

Thanks 
Madman100

---

### Post by dineshs on 2010-08-08
> address 192.168.1.110
mask 255.255.255.0
gateway 192.168.1.1
[COLOR="Red"]then hit enter[/COLOR]
DNS 4.2.2.1
then click apply you should hit enter after typing gateway

---

### Post by georgemc on 2010-08-08
Hi,

with your netmask of 255.255.255.0 the broadcast address should be 192.168.[COLOR=Red]1[/COLOR].255.  Any broadcast sent to 192.168.[COLOR=Red]0[/COLOR].255 would address a different network and most-likely be ignored by the other devices on your network.

I have setup static interfaces on Lucid and I do not include the broadcast or network address in the interface files.  I expect the software to be intelligent enough to understand what the proper broadcast and network should be.

Just make the /etc/network/interfaces file entry look like this:

iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1

Give it as try. 
Hope this helps.

George

---

### Post by madman100 on 2010-08-08
Hi All

Just like to say Thanks for all the help all working now

Thanks 
Madman100

---

### Post by dineshs on 2010-08-09
Please mark the thread as solved (via thread tools)

---

### Post by smith16 on 2010-08-09
Hi dineshs

I have done this before in ubuntu 9.10 by the network connection icon but for some reason when i try to set the gate address and save it does not save the gate address that i have entered only saves it as 0.0.0.0

Thanks
Smith

---

### Post by dineshs on 2010-08-09
smith16,
After typing IP mask and gateway in the respective fields you should hit enter.Now Add DNS and apply.It didnt work in 9.10?

---

### Post by Adem Stival on 2010-08-09
If you correctly configured the Virtual Server port on your router and  have the correct external (routable) IP address then you may not be able  to host a web site on your connection. Your ISP may block incoming web  request or your IP may not really be routable on the internet.  What ISP  do you use? What are the first 2 numbers in your routers external IP  address?

---

