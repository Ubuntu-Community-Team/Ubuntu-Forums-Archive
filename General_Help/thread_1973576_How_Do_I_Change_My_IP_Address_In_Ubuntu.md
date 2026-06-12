---
title: "How Do I Change My IP Address In Ubuntu"
date: 2012-05-05
forum: General Help
---

### Post by thehumangod1 on 2012-05-05
i was using this guide...
[http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/](http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/)

But when i open the Network Administration Tool, i'm missing the Connections tab.
Screenshot for example.
[img]http://img9.uploadhouse.com/fileuploads/16046/160468492a9b52bd5f52dd6e458a267db40851ed.jpg[/img]

What should i do?

---

### Post by thehumangod1 on 2012-05-05
bump

---

### Post by spiky001 on 2012-05-05
Hi  Why dont you just do the 2nd part of tutorial  open /etc/network/interfaces and edit the file

---

### Post by thehumangod1 on 2012-05-05
> **spiky001 said:**
> Hi  Why dont you just do the 2nd part of tutorial  open /etc/network/interfaces and edit the file

i don't understand how to do that. do you know what could be the reason why the connections tab isn't showing

---

### Post by spiky001 on 2012-05-05
If you open gedit ```
gksudo gedit /etc/network/interfaces
```  Then copy   auto eth0 iface eth0 inet static address 192.168.2.1 netmask 255.255.255.0 network 192.168.2.0 broadcast 192.168.2.255  save the file.  Just make a backup of interface file incase you need it

---

### Post by thehumangod1 on 2012-05-05
> **spiky001 said:**
> If you open gedit ```
gksudo gedit /etc/network/interfaces
```  Then copy   auto eth0 iface eth0 inet static address 192.168.2.1 netmask 255.255.255.0 network 192.168.2.0 broadcast 192.168.2.255  save the file.  Just make a backup of interface file incase you need it

so doing that will change my ip address? there's nothing else i need to do?

---

### Post by robwilkens on 2012-05-05
> **thehumangod1 said:**
> i was using this guide...
[http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/](http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/)

But when i open the Network Administration Tool, i'm missing the Connections tab.
Screenshot for example.
[img]http://img9.uploadhouse.com/fileuploads/16046/160468492a9b52bd5f52dd6e458a267db40851ed.jpg[/img]

What should i do?
\
That tutorial might be outdated..   On my ubuntu install you click the network icon (near the clock) then click 'edit connections'.. And from there it's pretty obvious how to do it from the gui i think.

---

### Post by spiky001 on 2012-05-05
Add
 iface eth0 inet dhcp
 at the end

```

auto eth0 iface eth0 inet static address 192.168.2.1 netmask 255.255.255.0 network 192.168.2.0 broadcast 192.168.2.255
iface eth0 inet dhcp

```

It works on mine, and IF thats the correct IP add.
Otherwise substitute the correct IP

---

### Post by thehumangod1 on 2012-05-05
> **spiky001 said:**
> Add
 iface eth0 inet dhcp
 at the end

```

auto eth0 iface eth0 inet static address 192.168.2.1 netmask 255.255.255.0 network 192.168.2.0 broadcast 192.168.2.255
iface eth0 inet dhcp

```

It works on mine, and IF thats the correct IP add.
Otherwise substitute the correct IP

ok so it should look like this?
[img]http://img0.uploadhouse.com/fileuploads/16048/1604845083433ccc2415b013be169febc3ba0b84.jpg[/img]

---

### Post by thehumangod1 on 2012-05-05
> **robwilkens said:**
> \
That tutorial might be outdated..   On my ubuntu install you click the network icon (near the clock) then click 'edit connections'.. And from there it's pretty obvious how to do it from the gui i think.

ok, i went there (i removed my MAC Address from the image). What do i do now

[img]http://img8.uploadhouse.com/fileuploads/16048/1604847821a9a2f01cef060e135abf5772294013.jpg[/img]

---

### Post by steeldriver on 2012-05-05
go to the ipv4 settings tab

- if you are already using a static address, just change it to your new settings

- if you are currently using DHCP, you will need to select 'Manual' from the drop down list first

fwiw, if your router supports it, a cleaner solution imo is to stick with DHCP but mimic static assignment by telling the router to always serve it the same address to that device (based on MAC) - if you start allocating static addresses manually on the client side you have to be careful to exclude them from the DHCP pool

---

### Post by thehumangod1 on 2012-05-05
> **steeldriver said:**
> go to the ipv4 settings tab

- if you are already using a static address, just change it to your new settings

- if you are currently using DHCP, you will need to select 'Manual' from the drop down list first

fwiw, if your router supports it, a cleaner solution imo is to stick with DHCP but mimic static assignment by telling the router to always serve it the same address to that device (based on MAC) - if you start allocating static addresses manually on the client side you have to be careful to exclude them from the DHCP pool

ok, i wen there. what do i put into the Address, Netmask, Gateway and DNS Servers:, Search Domain slots.
[img]http://img2.uploadhouse.com/fileuploads/16048/160487324c1f178025aea33243d459c590097698.jpg[/img]

---

### Post by Abrer on 2012-05-05
Address:
Enter the IP Address you want to use (192.168.2.12) for example.

Netmask:
Subnet Mask for the network (generally 255.255.255.0 for home networks)

Gateway:
This is your router IP. If you don't know what this is, open a terminal and type in 'route -n' without the quotes. Look for the destination line that says 0.0.0.0 and it's gateway. The gateway IP for the 0.0.0.0 line is your gateway address.

DNS Server:
Again, for home networks this is generally your router (gateway IP)

Just curious, why do you need to change your IP?

---

### Post by thehumangod1 on 2012-05-05
> **Abrer said:**
> Address:
Enter the IP Address you want to use (192.168.2.12) for example.

Netmask:
Subnet Mask for the network (generally 255.255.255.0 for home networks)

Gateway:
This is your router IP. If you don't know what this is, open a terminal and type in 'route -n' without the quotes. Look for the destination line that says 0.0.0.0 and it's gateway. The gateway IP for the 0.0.0.0 line is your gateway address.

DNS Server:
Again, for home networks this is generally your router (gateway IP)

Just curious, why do you need to change your IP?

ok, i did all that and hit save. but google is still saying i have the same ip address. what should i do? does changing this ip address not change my Public IP Address?

---

### Post by Abrer on 2012-05-05
It changes the IP Address on your eth0 interface which is probably connected to a router connected to your ISP.

It looks like this

Your machine |------| Router | ------- ISP

On the left side of the router is your home network and the | character represents interaces (points that require an IP address). When your machine goes through the router (the 3rd | ), it changes your network's private IP address to an address provided by your ISP, which is your PUBLIC address. This process is called NAT (Network Address Translation).

So no, it doesn't change your public IP. I hope that makes sense. Regardless, if you want to know if the changes were made to your machine's IP, you can type in ```
ifconfig | grep "inet addr:"
``` into a terminal. That'll list your addresses for each interface. You can ignore the 127.0.0.1 entry.

---

