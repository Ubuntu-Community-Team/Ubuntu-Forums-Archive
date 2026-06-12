---
title: "Beginning pointers"
date: 2012-09-13
forum: General Help
---

### Post by hawk007 on 2012-09-13
Hi, im very new to ubuntu ive just installed v9 and upgraded using do-release-upgrade and it upgraded to 10.04.4.

I tried to upgrade again but got the error:
mkdir()failed {Errno 2] no such file or directory. The page just stops there. 

After a restart i login ok again until i try to do an upgrade again then same thing happens.

That was the initial problem. Heres my main issue:

The server as given me a static ip 192.168.1.3 and i need to use: 192.168.1.7. How do i change this because ive followed instructions and tried /etc/network/interfaces and access is denied. i try using sudo /etc/network/interfaces and still no joy. (not sure how to use the sudo though).

Ive tried auto eth0  and sudo auto eth0 that doesnt do anything either. Command not found error.

the DHCP server issues an ip but i dont want it to do that on the server i want to use the static address mentioned. Any help appreciated, but please dont just point me to a page giving instructions how to do tis because ive followed them and they dont work.

---

### Post by steeldriver on 2012-09-13
> **hawk007 said:**
> i try using sudo /etc/network/interfaces and still no joy. (not sure how to use the sudo though).


You need to specify an editor for the sudo command to use - nano is probably the easiest if you are not used to vi / vim

```
sudo **nano** /etc/network/interfaces
```That's assuming (a) you have sudo permission (member of the admin/sudo group) and (b) your interface is managed via the networking service (rather than /etc/Network-Manager)

Post back if you are still having problems

---

### Post by hawk007 on 2012-09-13
Thanks i actually found something using the vi editor so will stick to that but thank you very much for your responce. Appreciated. Il have to try nano too some day. thanks again.

---

### Post by kjohri on 2012-09-14
It is much easier to use the NetworkManager applet in the top panel as compared to editing the /etc/network/interfaces file. Although I am not sure whether it is available in the version you are using.

I think you need something like this in /etc/network/interfaces

```
auto eth0
iface eth0 inet static
        address 192.168.1.7
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
```

---

