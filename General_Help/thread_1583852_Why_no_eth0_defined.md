---
title: "Why no eth0 defined?"
date: 2010-09-28
forum: General Help
---

### Post by sim085 on 2010-09-28
Hello, I am installing Ubuntu 10.04 as a guestOS. I must have done something wrong during the installation but I do not know (which is why I am asking). Basically at the moment I have two virtual machines, both with Ubuntu 10.04 (server edition) installed. However one of them correctly has the eth0 connection defined while the other one does not. For the one that does not have the eth0 connection defined I need to run the command dhclient and I get the connection there and ready. However on restart I have to run the command dhclient again in order to get the connection again. On the other hand, on the other virtual machine, connection eth0 comes automatically on start-up. 

Why is one machine realising that there is a connection while the other one does not?

---

### Post by CharlesA on 2010-09-28
What happens when you do this:

```
sudo ifconfig eth0 up
```

---

### Post by sim085 on 2010-09-28
> **CharlesA said:**
> What happens when you do this:

```
sudo ifconfig eth0 up
```

I get the message *eth0: ERROR while getting interface flags: No such device*

However if I do the same with eth2 I get no error message! and afterwards eth2 appears in ifconfig result.

---

### Post by CharlesA on 2010-09-28
Interesting.

Post the output of this please:

```
cat /etc/networking/interfaces
```

---

### Post by sim085 on 2010-09-28
> **CharlesA said:**
> Interesting.

Post the output of this please:

```
cat /etc/networking/interfaces
```

The output is *cat /etc/networking/interfaces: No such file or directory*

The same message appears both if I use the previous command or not.

---

### Post by CharlesA on 2010-09-28
Whoops. It's supposed to be "/etc/network/interfaces"

Are both VMs using the same chipset for the network card?

---

### Post by sim085 on 2010-09-28
> **CharlesA said:**
> Whoops. It's supposed to be "/etc/network/interfaces"

Are both VMs using the same chipset for the network card?

When ifconfig only display the *lo* entry, the command displays the following:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Both at work and home I use the same configuration. The only difference is that at home I am connected to the network through a wireless rooter which has a security key. The vm I did on an another network where working fine (unsecure network). At work my computer is connected with a cable to the network and therefore there are no security key.

I do not know why it is doing so but I think it is realted with the fact that at home the network has a security key.

---

### Post by CharlesA on 2010-09-28
Go into the network settings in VirtualBox and see what it says under "advanced"

Make sure that the adapter type is the same on both VMs.

---

### Post by envygeeks on 2010-09-28
The better question is: are you using DHCP for your network? 
How did you configure VMWare's networking for the Guest?
If you are using DHCP, did you remove Network Manager? Execute the command below which will help us too:

```

sudo ps auxf |grep NetworkManager

```

Should return something like:

```

root      1174  0.0  0.0  94232  4572 ?        Ssl  09:55   0:00 NetworkManager
root     11282  0.0  0.0   6556  1132 ?        S    16:07   0:00  \_ /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-[shortened]-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

```

Notice the keywords in the return :P

---

### Post by sim085 on 2010-09-28
I do not know why this works, but I opened the file /etc/network/interfaces and changes all instances of eth0 with eth1. I restarted and now ifconfig display eth1 immediatly on startup. Howcome it works with eth1 but not with eth0?? 

Please note that just because I have eth1 listed it does not mean I can download from the Internet. In other words apt-get still returns a lot of errors.

---

### Post by sim085 on 2010-09-28
> **CharlesA said:**
> Go into the network settings in VirtualBox and see what it says under "advanced"

Make sure that the adapter type is the same on both VMs.

It is the same, the only difference is that when I was using my laptop on an unsecure network everything works fine. At home however I have a secure network. This is the only reason that comes to mind why the vm all of a sudden do not work.

---

### Post by CharlesA on 2010-09-28
> **sim085 said:**
> It is the same, the only difference is that when I was using my laptop on an unsecure network everything works fine. At home however I have a secure network. This is the only reason that comes to mind why the vm all of a sudden do not work.

That shouldn't have anything to do with it tbh. Not sure why it's not working.

---

### Post by sim085 on 2010-09-29
> **CharlesA said:**
> That shouldn't have anything to do with it tbh. Not sure why it's not working.

Real and truly I do not know if this is an Ubuntu/Linux issue or a VirtualBox issue!! 

Let me change my question for a moment. On my laptop (with Windows7) I have to insert the **network key** in order to access the network (and therefore share internet connection). 

Now, if I set-up Virtual Box as **Bridge Adapter** so that I get an IP from the router, then I think I would need to define the network key as well right? or? if yes, then how can I define a connection eth0 with the wanted setting?

---

### Post by CharlesA on 2010-09-29
> **sim085 said:**
> Real and truly I do not know if this is an Ubuntu/Linux issue or a VirtualBox issue!! 

Let me change my question for a moment. On my laptop (with Windows7) I have to insert the **network key** in order to access the network (and therefore share internet connection). 

Now, if I set-up Virtual Box as **Bridge Adapter** so that I get an IP from the router, then I think I would need to define the network key as well right? or? if yes, then how can I define a connection eth0 with the wanted setting?

It just "piggybacks" off the host's connection, so you don't need to tell the guest what the key is.

Anyway, if it's working with eth1, just use that. I don't know why it's having problems defining it as eth0.

---

### Post by sim085 on 2010-09-29
> **CharlesA said:**
> It just "piggybacks" off the host's connection, so you don't need to tell the guest what the key is.

Anyway, if it's working with eth1, just use that. I don't know why it's having problems defining it as eth0.

Thanks. I finally managed to make it work in the work machine!! But as I said only with the eth1 and only if on bootup I use the command **sudo dhclient**. Could it be that eth0 is defined somewhere else but not properly set up?

---

### Post by CharlesA on 2010-09-29
Could be, but I'm not sure what the deal is with it.

So it says something like this in /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
```

---

### Post by sim085 on 2010-09-29
> **CharlesA said:**
> So it says something like this in /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
```

If I set it equal to eth1 then it will work on start up. So **yes** that would solve my problem (forgot about that option, ups). However I still can't understand what is keeping eth0 busy. I think somewhere eth0 is configured wrongly. But do not know where :(

btw - thanks for all the help, really appreciated.

---

### Post by sim085 on 2010-09-29
> **sim085 said:**
> I think somewhere eth0 is configured wrongly.

This is where it is being set; **/etc/udev/rules.d/70-persistent-net.rules**. I just deleted all that there was in this file and booted up again. Note I set /etc/network/interfaces back to how it was, that is pointing at eth0. Now all is ok :)

---

### Post by CharlesA on 2010-09-29
Glad you got it working. It's puzzling why it switched to eth1.

---

