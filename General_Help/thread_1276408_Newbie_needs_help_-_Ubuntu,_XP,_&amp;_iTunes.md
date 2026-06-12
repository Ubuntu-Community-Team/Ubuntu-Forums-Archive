---
title: "Newbie needs help - Ubuntu, XP, &amp; iTunes"
date: 2009-09-27
forum: General Help
---

### Post by brentdavis29 on 2009-09-27
I want to store all of my music on a Ubuntu machine, so that I can conserve the space on my laptop hard drive (which runs XP). 

Is it possible to have iTunes on my XP machine access a folder on my Ubuntu machine as the main repository of my music?

In particular, I'd like to figure out the following:
[LIST]
[*]When I plug in my iPhone to the XP laptop, will it still sync all of my music, if my music is on a separate machine?
[*]When I rip CDs or purchase music in iTunes on my XP machine, can I set it up to save the new music files directly to the music folder on my Ubuntu machine?, 
[/LIST]

Also... I really don't want to plug in my iPhone to my Linux box to sync it. I want to plug in to my laptop. So, I'm really not looking for Amarok or the like as a solution. I really do want to use iTunes on XP. I just don't want to store all of that music on my laptop.

Any help is much appreciated!!!

---

### Post by etnlIcarus on 2009-09-27
You can try [Ext2 for Windows](http://www.fs-driver.org/), although I personally wouldn't recommend it.

The easiest way to do what you're describing is to use the Live CD (System>System>Partition Manager) to resize your current Ubuntu partition, shrinking it (I wouldn't shrink it below about 10GB - make sure less than 10GB is currently in-use on your Ubuntu install, or you'll lose data/bork your install) and making room for an NTFS partition, to be put next to it. Both Ubuntu and XP will be able to read from the NTFS partition.

---

### Post by boblemur on 2009-09-27
I think that the first post is missing your point somewhat.

what you are trying to do is rather simple in theory.

samba is a linux program you can use to setup windows shared folders so you can make it so your laptop can mount the drive and then have itunes use that as its main music folder, (then make it copy to library option under preferences advanced) 

so have both amarok (or whatever your linux player is) watch its folder for updates, then when you add files on windows they will copy to linux and be updated to your linux library.

now your main problem is your second point (ripping and buying music, because apple like to screw the people doing the right thing they make it so that only itunes can read the files you buy from the itunes store (at least this has always been the case when iv done it) so this means that it will add to your library but amarok wont be able to read them.

unfortunately illegally downloading your music would be a much easier solution, which is really stupid on apples behalf. 

there are plenty of tutorials on the internet for samba but i think that your itunes music will be a much bigger issue for you. 

please read the following for more info:

[https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore]("https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore")

[http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto]("http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto")

hope this helps :)

---

### Post by brentdavis29 on 2009-09-28
Boblemur

Do I need to worry about dynamic IP addresses when using Samba? If so, how do I work around that? 

B

---

### Post by undecim on 2009-09-29
If you have an ubuntu server (or even a desktop that's running samba) and your local network uses DHCP (as most do) then you can try using the host name of your server. For example, my server's host name is "midnight" and I can access my server by the name "midnight.local"

If that doesn't work, then you need to set up a static IP address. Open the file /etc/network/interfaces on your server and find the section that starts like this (though it may be a different interface than "eth0" on yours)

```
auto eth0
```and change that section to look like this:

```
# The primary network interface
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
network xxx.xxx.xxx.xxx
broadcast  xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

```where each instance of xxx.xxx.xxx.xxx is the appropriate information about your network. As an example, mine looks like this (I've added the comments after each line to explain)

```
# The primary network interface
auto eth0
address 192.168.1.35       # The IP address of my server - usually just make the last number somewhere from 2-99 and you are good, because most routers begin DHCP addresses at 100)
netmask 255.255.255.0      # The netmask of my network (in most cases, its that same as shown here)
network 192.168.1.0        # The network (The numbers that all computers on the network share, followed by zeros as placeholders
broadcast  192.168.1.255   # broadcast address (Like "network" except with 255 instead of 0)
gateway 192.168.1.1        # the router IP address ("usually" like network with the last number a 1 instead of 0

```most networks will be similar to this setup.

You can see your current network information (and also determine your interface name) from the ifconfig command. In a terminal, type "ifconfig", and you will see something like this for each network card you have.

```
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:40:4a:f2  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe40:4af2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28681643 errors:0 dropped:39 overruns:0 frame:0
          TX packets:19348045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37905765767 (37.9 GB)  TX bytes:8461406214 (8.4 GB)
          Interrupt:23 Base address:0xe000 

```

using that second line (starting with inet addr) you should be able to figure out the rest of your network options.

---

### Post by boblemur on 2009-10-01
as undecim has said you can try the hostname however, i would be wary trying to get this to work from windows, as it will slow your login down on windows when the host cant be found (with an ipaddress it dosent seem to, im prity sure this is an xp bug).

settings up the static address that undecim describes will work better (note that what he describes can also be achieved from your router. the following dosent apply if you do it on the router). if your router is on DHCP then it is convention to pick an ip address out of the DHCP range when making your ip address static.

if you want to go the extra step and use a hostname after this in windows theres a file:
```
c:\windows\system32\drivers\etc\hosts
```

which is almost the same as the ubuntu:
```
/etc/hosts
``` 
file, you can find out more information about it using:
```
man hosts
```

however here is a small part of mine and it should be self explanitory what you need to do:
```

192.168.1.1	router
192.168.1.10	serverl
192.168.1.11	laptop

```

simply make an entry on _windows_ with the static ip on the left and a name you want to give to your computer. eg (itunes-server)

then run (with itunes as your share name, share_user as your username:
```
net use z: \\itunes-server\itunes /user:share_user /persistent:yes
```

the part (/persistent:yes) means that it will stay mounted even after reboot, so the command needs to be run only once.

if you have anymore problems dont hesitate to post

---

### Post by brentdavis29 on 2009-10-01
It seems as though Samba is set up correctly at this point. Honestly I don't know. In your last response you mentioned to "try using the host name of your server" when setting up Samba, and then gave me instructions on setting up a static IP if needed. I honestly I'm not sure where to apply that info during the setup process.

BUT, whatever reason I can now see my Ubuntu folder from Windows Explorer in XP. (I made some adjustments to the /etc/samba/smb.config file). 

So, here's my final issue (I hope). In iTunes, I've tried to browse to the network folder where my music is stored, and designate it as my main music folder. I click OK. And now... nothing. iTunes doesn't seem to recognize the folder on the network at all. 

Is there anything else I should do? At this point, I'm still wondering if it's an Ubuntu setting, an iTunes setting, or an impossibility.

---

### Post by boblemur on 2009-10-01
yeah try to run the command:

```
net use z: \\itunes-server\itunes /user:share_user /persistent:yes
```

and then tell itunes to use the folder z:

as its main folder, this is probably because itunes dosen't like using a shared folder as its main folder but if you use a drive it wont know that its a network share.

so, currently have you set up a static ip address? because if you have you can run (if your server is at 192.168.1.10):

```
net use z: \\192.168.1.10\itunes /user:share_user /persistent:yes
```


so you can make the ipaddress of the server static at any point you like it just means that the address will never change in future and so your laptop can always point to 192.168.1.10 with confidence that the server will always be whats at that address. because if you restart and the computer is given an new ipaddress (by your router) then when the client (laptop) tries to access its z: drive then the share will no longer be accessible because its now on 192.168.1.5 for example. not .10 anymore.

i hope this is clearer for you, if its not then ask me to clarify a particular part. good luck :)

ps: if this is your last issue remember to mark the post as solved.

---

### Post by brentdavis29 on 2009-10-02
It looks as though I did it wrong, because I do not have a Z folder visible. This is the code that I entered. 

net use z: \\media_server\music /user:share_user /persistent:yes

I tried to use the server name before going to the static IP. Maybe that was the problem. Will I need to "undo" the code that I entered before retrying it the "right" way?

Thanks so much!!!

---

### Post by boblemur on 2009-10-02
ok so the first thing you should try is under windows run:

```
ping \\itunes-server
```

if you see something like:

```

Reply from 192.168.1.??? time ??ms
Reply from 192.168.1.??? time ??ms
Reply from 192.168.1.??? time ??ms

```

then you are fine using the host name however if you get something like:

```

Ping request could not find host ????. Please check the name and try again.
```

that means that windows cannot resolve the name so you will need to setup a static ip address.


to remove a mounted drive use the following:

```
net use z: /delete
```

so if you want to remove the old drive run the above command then try again with the ip address.

are you able to copy paste or show me what it says when you run the command:

```
net use z: \\itunes-server\itunes /user:share_user /persistent:yes
```

because that will give us more information as to whats going wrong.

---

