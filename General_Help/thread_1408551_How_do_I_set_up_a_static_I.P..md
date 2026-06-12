---
title: "How do I set up a static I.P.?"
date: 2010-02-16
forum: General Help
---

### Post by Zynon on 2010-02-16
So I am fairly new to Ubuntu and I am wanting to set my Ubuntu box up with a static IP. When I say static I.P. I mean a local static I.P.   I have done some looking from google and found that I have to use the sudo vi /etc/network/interfaces  command to edit the file.

Here is where I am having the problem. I have a basic Linksys home network and I do not know or understand what network or broadcast mean? 
I understand IP SUBNET and gateway but have no clue what those values are supposed to be.

Here is my network Information if someone would be so kind as to tell me what to put there and what they mean and for.

I.P 192.168.1.104
Subnet 255.255.255.0
gateway 192.168.1.1


Thank you in advance

---

### Post by dalitso on 2010-02-16
```
sudo nano /etc/network/interfaces
iface eth0 inet static
        address 192.168.1.104
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1

```

Then press ctrl and o to save changes. Then ctrl and x to exit
then run
```
/etc/init.d/networking restart
```

---

