---
title: "configure network through terminal"
date: 2006-02-19
forum: General Help
---

### Post by sublime on 2006-02-19
ok im trying to get ubuntu running on a buddies computer but hes running it with an nvidia 7800 gt card and its giving us the problem where we cant get into gnome, so i cant set up the network through administration>network settings, i have to do it through the terminal. it is also not through dhcp, we need to do a static ip address.  so i know about ifconfig and the basics of the terminal but i cant get the ip address, dns server and gateway address setup.  any help would be awesome.  thanks

---

### Post by bscbrit on 2006-02-19
When you say that "i cant get the ip address, dns server and gateway address setup" I assume you have the information but do not know where to put it on the Ubuntu machine.  Is this correct?  Without knowing your gateway address or dns server addresses it will be difficult to set up - but not impossible :) 

While I wait for your answer, the files that you will need to modify are

/etc/network/interfaces
/etc/resolv.conf

and perhaps

/etc/hosts

While you are waiting for my reply, you can look at 

man ifconfig
man resolv.conf
man hosts

which will explain how we will set it all up.  :-D

EDIT:  I would also suggest that you look at the nano editor ('nano') - it is probably the easiest editor that will be installed. Although there are better editors available there is also a lot to learn to get to use them properly.

---

### Post by nanotube on 2006-02-19
well, first you want to bring up the interface, like this:
```
sudo ifup eth0
```
(insert whatever you have instead of eth0)
then, to set a static ip address, you issue
```
ifconfig eth0 inet xxx.xxx.xxx.xxx
```
that would set up a statit ip on your nic (again, replace eth0 with your nic, and xxx.* with your ip address that you want). the gateway and netmask will automatically be set based on ip address you give.
then, to set dns server, edit /etc/resolv.conf file, and put in a line "nameserver xxx.xxx.xxx.xxx" with the ip of your nameserver... and it should work. :)

---

### Post by sublime on 2006-02-19
awesome, thanks guys.  yes i do have dns, ip add, and gateway.  just needed to know the commands or files to edit.  i dont have access to the comp now but i should be able to get it working with this. thanks again

---

### Post by bscbrit on 2006-02-19
You're welcome - see you around the forums.

---

