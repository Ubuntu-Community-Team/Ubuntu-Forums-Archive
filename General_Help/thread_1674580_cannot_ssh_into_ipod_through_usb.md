---
title: "cannot ssh into ipod through usb"
date: 2011-01-24
forum: General Help
---

### Post by Mesqueeb on 2011-01-24
So I have wired internet on my ubuntu 10.10, wireless on my Ipod touch.
I go to places > connect to server > SSH, fill in port 22,  ipod's ipaddress, "root"

and it gives me the error:
cannot find host "sftp://root@*ipod's ip*/" could not be shown (or something like that)
make sure your proxy settings are correct (or something like that)
every time I try to connect to ipod...
anyone knows the problem?

(jailbroken > open ssh ok!)

---

### Post by djeikyb on 2011-01-24
(1) Your post title is confusing. What has usb got to do with anything?

(2) Try tunneling to the ipod on the command line. Open a terminal and run:
```
ssh -vv user@ipod.ip.addy
```

---

### Post by Mesqueeb on 2011-01-24
> **djeikyb said:**
> (1) Your post title is confusing. What has usb got to do with anything?
Because I have no wireless internet on my computer I need to plug in my ipod with usb right? No? =S

> **djeikyb said:**
> (2) Try tunneling to the ipod on the command line. Open a terminal and run:
```
ssh -vv user@ipod.ip.addy
```

```
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname ipod.ip.addy: Name or service not known
```

Arrr!! ^^ What shall I do?

---

### Post by djeikyb on 2011-01-24
Ahmm..k. To be sure, I have absolutely no experience with jail-broken ipods, much less an ipod running openssh. I'm limited to music with my fifth generation ipod. That said..

(1) When you use the ipod cable to connect the ipod to your computer, my experience is it puts the ipod into a special usb-connected-to-the-computer mode that limits you to charging and presents the ipod to your computer as an external usb hard disk. If this is the case for jail-broken ipods, it is impossible to ssh while in connected to your computer with the ipod cable.

(2) You posted the output of the ssh command, but it is not clear to me if you ran my command verbatim. If you did run it exactly as I typed it, please try again, substituting "ipod.ip.addy" with the ip address of your ipod. It's important you use the ip address and not the hostname, because hostnames are not reliable for troubleshooting.

(3) If I am correct on 1, your solution is to create a Local Area Network (LAN) with a wireless router. The ipod connects to the router wirelessly, and you can plug your desktop in directly to the router. Apologies if this is obvious to you, I'm currently unaware of your skill level.

---

### Post by Mesqueeb on 2011-01-24
(1) Yes I can see pictures and charge. But I want to edit OS files. So I should unplug my iPod then?

(2) replaced ipod.ip.addy with the ip address of ipod and got:

```
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.4 [192.168.2.4] port 22.
debug1: connect to address 192.168.2.4 port 22: No route to host
ssh: connect to host 192.168.2.4 port 22: No route to host
```

(3) Create a local area network... o_O I'll look into this on how to do it.

Thanks for the help! I hope I get get into my ipod!!

-Mesqueeb

---

### Post by Mesqueeb on 2011-01-24
when I look at local area network now suddenly I see my ipod there......
but when I press it it says:
"cannot mount the location
there is no &#32076;&#36335;", which I guess means there is no route/there is no road/no process/no course

---

### Post by djeikyb on 2011-01-24
I'm curious. Can you access google.com from both your desktop and your ipod? What is the ip address of your desktop?

And yes. If your ipod behaves as I described, it must be unplugged for ssh to work.

---

### Post by Mesqueeb on 2011-01-24
```
mesqueeb@Poliwhirl:~$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:15:f2:09:bb:89 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.5/24 brd 192.168.2.255 scope global eth0
    inet6 fe80::215:f2ff:fe09:bb89/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:15:f2:09:aa:79 brd ff:ff:ff:ff:ff:ff
```

so I guess 192.168.2.5 or 192.168.2.5/24 ?

---

### Post by djeikyb on 2011-01-24
Apologies. The command you want is: ipconfig
EDIT: ne'er mind, you did fine. I just learned a new command! : D

Can you try the ssh command I gave you again, now that your ipod is disconnected?

---

### Post by Mesqueeb on 2011-01-24
you mean ifconfig? ^^
inet address: 192.168.2.5

---

### Post by Mesqueeb on 2011-01-24
Omg it works

I don't know why, but suddenly it works!?!?!?!  o_O

---

### Post by djeikyb on 2011-01-24
Bugger. Yes, ifconfig is what I meant. Heh, had a relapse to Windows cli.

Anyway, it works because your computer and your ipod are on the same Local Area Network. You can tell by the ip address. Both start 192.168.2, which means they're on the same network. The last number distinguishes different devices on the same network.

It also works because you unplugged your ipod, letting it function in normal ipod mode instead of usb-harddisk mode.

---

### Post by Mesqueeb on 2011-01-24
> **djeikyb said:**
> Bugger. Yes, ifconfig is what I meant. Heh, had a relapse to Windows cli.

Anyway, it works because your computer and your ipod are on the same Local Area Network. You can tell by the ip address. Both start 192.168.2, which means they're on the same network. The last number distinguishes different devices on the same network.

It also works because you unplugged your ipod, letting it function in normal ipod mode instead of usb-harddisk mode.

It's so awesome that I can mess with the OS so easily now! xD
I actually only use it to install better and asian fonts... to use with a study program

thanksssssss!

(you happen to know anything about skype? xD [http://ubuntuforums.org/showthread.php?t=1657671](http://ubuntuforums.org/showthread.php?t=1657671) )

---

### Post by Mesqueeb on 2011-02-12
I don't get it... Sometimes it works and sometimes it does not... >,<

---

### Post by djeikyb on 2011-02-12
You're making sure to always have it unplugged before trying ssh, yes?

---

### Post by Mesqueeb on 2011-02-15
yes. It's funny, last time I tried it 4 times right after each other, and the 4th time it worked. xD

---

