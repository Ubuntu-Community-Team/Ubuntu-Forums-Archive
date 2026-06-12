---
title: "Getting the IPs of computers in Nautilus &quot;network&quot;"
date: 2011-02-21
forum: General Help
---

### Post by Ernesto RD on 2011-02-21
In the main menu->places->network i can see my workgroup, and all the computers belonging to it, but i only see their names, not their IPs (wich is normal i guess), but sometimes i would like to know the ip adress of a computer in the workgroup (for example to connect to it via tsclient).
Ibe tried right clicking on a computer icon and selecting properties, but the ip is not there.

Is there a way to get the ip of a computer in naultilus->network-><MyWorkgroup>?

thanks

---

### Post by Ernesto RD on 2011-03-11
Anybody? :)

---

### Post by coffeecat on 2011-03-11
Interesting question. I cannot find a nautilus or even a GUI way of doing this - there must be a way - but you can in the terminal with avahi. On my network I have a Western Digital NAS, its device name being "MyBookWorld", but the smb share appears in Nautilus as "MYBOOKWORLD". It has a fixed IP address of 192.168.1.100.

Fortunately, both ways of rendering the device name work so long as I add the .local domain. 

```
$ avahi-resolve -n MYBOOKWORLD.local
MyBookWorld.local    192.168.1.100
```and

```
$ avahi-resolve -n MyBookWorld.local
MyBookWorld.local    192.168.1.100
```But:

```
$ avahi-resolve -n MyBookWorld
Failed to create host name resolver: Invalid host name
```And, in case you've forgotten the hostnames of the devices on your network, this will tell you:

```
avahi-browse -a
```I'd be interested if someone else knows a GUI way.

---

### Post by doas777 on 2011-03-11
well, a ping scan in zenmap would turn up all computers on your network. 

just an aside, for the last 15 years or so, my computer names have always indicated the last octet of their ip address, just to make it easier on me.

---

### Post by dcstar on 2011-03-12
> **Ernesto RD said:**
> In the main menu->places->network i can see my workgroup, and all the computers belonging to it, but i only see their names, not their IPs (wich is normal i guess), but sometimes i would like to know the ip adress of a computer in the workgroup (for example to connect to it via tsclient).
Ibe tried right clicking on a computer icon and selecting properties, but the ip is not there.

Is there a way to get the ip of a computer in naultilus->network-><MyWorkgroup>?

thanks

```
arp -a
```

---

### Post by Ernesto RD on 2011-05-27
thanks guys! 
tried the avahi-browse -acommand, but after it lists the local computer,it just "hangs" there forever till i press ctrl-c

the arp -a
command worked, it lists the ips of all the computers on the network, unfortunatelly without names.
i guess that to connect to a specific pc with tsclient ill have to try connecting to all the ips (assuming a small network), till i find the pc i want to connect to

anyone know a better way?

EDIT/UPDATE:
arp -a only works sometimes, others it just lists the ip of the router, but not the other pcs :(

---

### Post by colin.p on 2011-05-27
To have a network, you more than likely have a router, rather than a switch/hub. Why don't you log into the router, and there you would have all network devices listed, including IPs?

---

### Post by Morbius1 on 2011-05-27
In a terminal:
```
findsmb
```

---

### Post by Rebelli0us on 2011-05-27
You can just log into your router and see all assigned IPs.

---

### Post by Ernesto RD on 2011-05-27
thanks for your answers.
tried findsmb, but just like arp -a it only lists information about the pc i run the command in.

About loggin in to the router to see assigned ips, thats not allways possible for me, let me explain why (and what im trying to acomplish)...

a small part of my job, is to provide tech support to small/medium offices, this most times involves doing some tasks on some (or all) of the computers in those offices, and instead of physically touring the entire office and asking people off their desks so i can work on their pcs, i access those pcs remotely via tsclient.
so i get to the office with my netbook (my netbook has ubuntu 11.04), and connect to the local network via wifi, and from my netbook i use tsclient to connect to the other pcs i need to access.
Now, to login to the router, i need the router password, wich most of the times is in a sticker on the router itself, sometimes i do have physical access to the router, others (for various reasons) i dont.
Back when my netbook had windows xp, i had no problem. i would just open up the "network" icon in explorer to see the computer names,  fire up "remote desktop client", type the target computer name and hit connect.
However, in linux this doesnt work. if i enter the computer name instead of its ip, tsclient doesnt find it. so i need the ip (not just the name) of the computer im trying to access.

**NE way, i think i found a way to do it using the nmblookup command (hope this helps others that need to do the same)...**

1.- once you are connected to the desired network, open naultilus (click on my home folder or whatever)

2.- click on the "Network" icon on the left pane, then on the "Windows network" icon. hopefully you will see all the computers on the network. Note the name of the pc you are trying to access (for example MANAGEMENTPC)

3.- open a terminal, and type nmblookup <name of pc> (for the example name, type nmblookup MANAGEMENTPC)

4.- the command should return the ip of that computer. now go ahead and type that ip in tsclient to connect. :popcorn:
So far I have only tried this nmblookup solution on my own network, and it allways works, but im hoping it will also work when i am connected to other networks.

if anyone has a better method, i would be glad to know it.

---

### Post by apjjr on 2013-01-19
I wanted to see a list of names, ips and shares.  findsmb only lists the computer I run it on like it did for you.  So I did a little research and came up with the following:
> #smblist.sh - Alex Janssen - 1/17/2013
if [ ! -f /usr/bin/smbtree -o ! -f /usr/bin/nmblookup -o ! -f /usr/bin/smbclient ]; then echo -e "samba needs to be installed.  Use 'sudo apt-get install samba' to install it.\nEdit /etc/samba/smb.conf to configure for your network.\nSet the workgroup name, primarily."; exit 1; fi
echo -e "smblist.sh  $(date)\n"; smbtree -SN|grep '\\'|cut -f2|cut -c 3-|sort|while read svr; do echo -ne "$svr\t"; ipname=$(nmblookup $svr|grep '<00>'); cmnt=$(smbclient -NL $svr 2>&1|grep -m 1 'IPC'|cut -c 40-); echo -e "$ipname\t$cmnt"; smbclient -NL $svr 2>&1|grep Disk; done; exit 0 

Let me know how it works for you.
Alex

---

### Post by apjjr on 2013-01-19
doas777,
do you assign ips manually on your network?

---

### Post by lisati on 2013-01-19
[quote=Code of Conduct]
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
[/quote]

Thread closed

---

