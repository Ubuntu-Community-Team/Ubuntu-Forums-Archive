---
title: "Setting Up Static IP Tutorials"
date: 2011-12-17
forum: General Help
---

### Post by adamantasaurus on 2011-12-17
Hello,

I am trying to setup a static IP address (one that doesn't change) is there any tutorials you can point me to or any advice you can give me?

Thanks

Adamantasaurus

---

### Post by mikewhatever on 2011-12-17
What environment? Serer? Desktop (Ubuntu, Kubuntu)???

---

### Post by adamantasaurus on 2011-12-17
> **mikewhatever said:**
> What environment? Serer? Desktop (Ubuntu, Kubuntu)???

Ubuntu Server 10.04 sorry should have put that in before.

---

### Post by Dangertux on 2011-12-17
You can do this a couple of different ways.

```

sudo ifconfig eth0 192.168.0.5 netmask 255.255.255.0 up

```This will change the ip address for eth0 to 192.168.0.5 and the netmask to 255.255.255.0.

Alternatively since this has no persistence (meaning it goes away at reboot) you can edit the  /etc/networking/interfaces file

and add something (or change what's there) like this

```

iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1

```

then restart your network

```

sudo /etc/init.d/networking restart

```For more advanced interface tweaking check out the ip command : [http://linux.die.net/man/8/ip](http://linux.die.net/man/8/ip)

Hope this helps.

---

### Post by adamantasaurus on 2011-12-17
> **Dangertux said:**
> You can do this a couple of different ways.

```

sudo ifconfig eth0 192.168.0.5 netmask 255.255.255.0 up

```This will change the ip address for eth0 to 192.168.0.5 and the netmask to 255.255.255.0.

Alternatively since this has no persistence (meaning it goes away at reboot) you can edit the  /etc/networking/interfaces file

and add something (or change what's there) like this

```

iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1

```

then restart your network

```

sudo /etc/init.d/networking restart

```For more advanced interface tweaking check out the ip command : [http://linux.die.net/man/8/ip](http://linux.die.net/man/8/ip)

Hope this helps.


Sorry I am very new at this,

When i want to open that file to edit it should I put

sudo nano /etc/networking/interfaces 

Or is there another/better way to do it? 

Thanks so much you really helped me out.

---

### Post by MG&amp;TL on 2011-12-17
> **adamantasaurus said:**
> Sorry I am very new at this,

When i want to open that file to edit it should I put

sudo nano /etc/networking/interfaces 

Or is there another/better way to do it? 

Thanks so much you really helped me out.

*nano* is fine, you can also use any other command-line editor like *vi* or *emacs*

---

### Post by adamantasaurus on 2011-12-17
> **Dangertux said:**
> You can do this a couple of different ways.

```

sudo ifconfig eth0 192.168.0.5 netmask 255.255.255.0 up

```This will change the ip address for eth0 to 192.168.0.5 and the netmask to 255.255.255.0.

Alternatively since this has no persistence (meaning it goes away at reboot) you can edit the  /etc/networking/interfaces file

and add something (or change what's there) like this

```

iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1

```

then restart your network

```

sudo /etc/init.d/networking restart

```For more advanced interface tweaking check out the ip command : [http://linux.die.net/man/8/ip](http://linux.die.net/man/8/ip)

Hope this helps.


I found another tutorial and it gives me code similar to yours but a little different

I'm wondering if I should use your code or the one in the tutorial

Here is the code

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 208.88.34.106
        netmask 255.255.255.248
        broadcast 208.88.34.111
        network 208.88.34.104
        gateway 208.88.34.110

Here is the tutorial.... (if you scroll down to where it says ubuntu/debian ip configuration files).

[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

Thanks for your help.

---

### Post by adamantasaurus on 2011-12-17
> **Dangertux said:**
> 

```

iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1

```



I tried entering your code and when I go to write out the file (cntrl O) and hit enter it gives me 
```

[Error writing /etc/networking/interfaces: No such file or directory]

```

Is there something I'm doing wrong?

---

### Post by Dangertux on 2011-12-17
Sorry I typoed it's /etc/network

---

### Post by lisati on 2011-12-17
There are more ways than one to achieve a static IP address, the editing of the "interfaces" file is one way. Each has its own pros and cons. My preference is to use my router to reserve static/fixed IP address on my own network.

---

### Post by perspectoff on 2011-12-17
Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Set_a_static_IP_address)

or Kubuntuguide:

[http://ubuntuguide.org/wiki/Oneiric#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Oneiric#Set_a_static_IP_address)

---

### Post by redmk2 on 2011-12-17
> **lisati said:**
> There are more ways than one to achieve a static IP address, the editing of the "interfaces" file is one way. Each has its own pros and cons. My preference is to use my router to reserve static/fixed IP address on my own network.

The term *static ip address* traditionally does not pertain to the addresses immutability (that it does not change), but rather to its method of configuration.  Like this ```
static = configured via a file
dynamic = configured via a DHCP server (including reserved addresses that are non-changing
```

Think of it this way: if the DHCP server stops working a static IP address will still work as it is configured via file.  A dynamic address will fail if the DHCP server fails regardless of whether it it is reserved or not.

---

### Post by redmk2 on 2011-12-17
> **adamantasaurus said:**
> I found another tutorial and it gives me code similar to yours but a little different

I'm wondering if I should use your code or the one in the tutorial

Here is the code

```
auto lo
iface lo inet loopback

auto eth0      [COLOR="Red"]# this sets the interface to come up upon bootup (see Dangertux's comment)[/COLOR]
iface eth0 inet static
        address 208.88.34.106
        netmask 255.255.255.248
        broadcast 208.88.34.111  [COLOR="Red"]# Last number in the network[/COLOR]
        network 208.88.34.104   [COLOR="Red"]# this is not strictly needed as it is set by the netmask[/COLOR]
        gateway 208.88.34.110
```

Here is the tutorial.... (if you scroll down to where it says ubuntu/debian ip configuration files).

[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

Thanks for your help.

There really is not any difference.  More like enhancement.  See my comments in red above

---

