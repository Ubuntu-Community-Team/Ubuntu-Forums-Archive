---
title: "change from dhcp to static ip addy"
date: 2011-01-05
forum: General Help
---

### Post by surfmonkee on 2011-01-05
my system is belkin router with dhcp enabled.

connected are: win xp desktop, win7 netbook, ps3 and fujtisu laptop with ubuntu 10.10, advent notebook xp.

right now i have everything getting its ip addy over dhcp but i want to set static ip for each machine. (so the ps3 can run dmz and ocasionally the belkin changes ip address even tho the lease time is set to forever)

i can do this with the windoze machines but i do not know how to set static ip and other info for the ubuntu machine.


any help would be great, i did search for the forum for 'static ip' but the results that appeared were nothing to do with dhcp!

---

### Post by seawolf167 on 2011-01-05
To change to a static IP address:

Backup the interfaces file first"

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```Edit the interfaces file ("ZZ" in vi editor saves and quits, ":q!" in vi editor quits without saving changes):

```
sudo vi /etc/network/interfaces
```Assuming you only have 1 ethernet card and are using the main port on your 1 card:

Change this section:

```
auto eth0
iface eth0 inet dhcp
```to this (and replace the numbers with the values you want & have setup for your network):

```
auto eth0
iface eth0 inet static
address 192.168.1.208
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.2
```then restart the networking service

```
sudo /etc/init.d/networking restart
```also the new way to restart the service

```
sudo service networking restart
```Edit: added backup line for interfaces file, found GUI version to set static IP through GUI [here]("http://www.howtogeek.com/howto/19541/how-to-assign-a-static-ip-to-an-ubuntu-10.04-desktop-computer/")

---

### Post by QLee on 2011-01-05
[QUOTE=surfmonkee]my system is belkin router with dhcp enabled.
...
any help would be great, i did search for the forum for 'static ip' but the results that appeared were nothing to do with dhcp![/QUOTE]

It seems from the way you have phrased your request that what you want to do is have the router hand out the same IP address to the same computer each time, static. 

In my opinion in a situation like yours that is best done by configuring the DHCP of the router to hand out IP addresses by the MAC of the interface requesting connection, that will be unique for each computer interface (as long as we are not discussing MAC spoofing). You'll have to consult the documentation for your router for how to do that and it may not be available for all routers. I haven't yet seen one that couldn't but I have not seen all routers. Doing it that way you can just let all the computers request an address from DHCP and you only have to configure the addresses you want for each computer in one place, the router.

---

### Post by dandnsmith on 2011-01-05
Since OP said he knows how to do it with Windows, but not with linux, he obviously wants to set a static IP at each PC.

It can be effected fairly simply in Ubuntu by editing the 'connection' which you approach thru the System Menu on the taskbar and use the Preferences submenu to get to Network Connections.

HTH

---

### Post by MrGreenTea on 2011-01-13
[SIZE=4]I think you have to reserve IP in your router first then set static in each PC. You can change to static IP in GUI, I think it's easier then thru command line. I saw Mr. Seawolf gave you a link to How-to-geek, take a look.[/SIZE]

---

### Post by kongfuzi on 2011-04-11
> **seawolf167 said:**
> 
Change this section:

```
auto eth0
iface eth0 inet dhcp
```to this (and replace the numbers with the values you want & have setup for your network):

```
auto eth0
iface eth0 inet static
address 192.168.1.208
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.2
```

Hi, I'm pretty new at this and found this thread which I know will help with my issue. I just have a question as to what the different numbers above are referring to. Is "addresses" my server's IP address? The netmask I'm good with. Network, is that my routers IP? Broadcast, is that my IP address that I can find on let's say ipchicken.com? And what is gateway? 

~KF

---

