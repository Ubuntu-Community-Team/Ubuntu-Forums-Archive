---
title: "Ubuntu and Windows on network"
date: 2009-08-02
forum: General Help
---

### Post by satish_j on 2009-08-02
Ok,I need to access my website(developed on a Linux server) to be accessible on windows machine.
i.e how can i access linux sever from a windows machine(XP or vista)??
Currently my Linux server does not have any static IP.Pls tell me the steps to assign one if required.(Iam assuming that i can access the server by providing the IP address on win m/c)..somewhat like this:
[http://Ip_addr_](http://Ip_addr_) of_ Lin_Srvr/Login.php
Any help seriously appreciated?

---

### Post by MTGap on 2009-08-02
Well here's how to configure a static ip address on Ubuntu: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/)

Once you have that you should be able to access your website on the windows machine through your local network.

---

### Post by satish_j on 2009-08-03
Even after assigning random static IP,iam not able to ping windows machine(destination host unreachble).The network icon is showing as disconnected.

---

### Post by satish_j on 2009-08-15
Ok,it was the cable i was using that was the source of problem.I needed the crossover cable to connect 2 pcs together.
Now,atleast the 2 systems are connected,but iam not able to ping any of the systems with each other.
Firewall on xp system is OFF.Ubuntu system gives foll for iptables
```

satish@TITAN:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
satish@TITAN:~$ sudo ufw status
Firewall not loaded
satish@TITAN:~$ 

```
I read somewhere that some samba server would b required to be setup on ubuntu,so i installed it thro synaptic manager(Just installed it,no configuration),but still no success.
what should i do to get both systems in network?help reqd urgently...

---

### Post by Iowan on 2009-08-15
Are the IP addresses of the two machines in the same subnet? What are the IP addresses, netmask, and gateway settings on each machine. **ifconfig -a** should help on Ubuntu machine - **ipconfig** on Windows.

---

### Post by satish_j on 2009-08-15
Ubuntu specs:
Ip: 10.12.70.112
Subnet mask: 255.255.255.0

Win XP specs:
Ip: 10.12.70.113
Subnet mask: 255.255.255.0

Gateway on both systems is blank.
pinging gives 'Request timed out'

---

### Post by satish_j on 2009-08-16
still looking for sol...ok,can anyone tell me how to check whether samba is running in background by looking at the processes??
I really doubt the samba thing since after starting by _sudo /etc/init.d samba start_,i cannot find any new process getting created in background.
:confused::confused:
....<<Frustration building up>>....
edited..
just found 1 more anoyance...i cannot even ping the ubuntu box on itself by IP address.
```

ping localhost or ping 127.0.0.1 works fine

```
but
```

ping 10.12.70.112 does not..

```
??

---

### Post by Iowan on 2009-08-16
Samba shouldn't affect the pinging. I'll need to check one of my Ubuntu boxes (at home... instead of here at work) to get details of how to "route add default gw...". Dunno if that can be added to */etc/network/interfaces* file.
 The gateway can be configured on the Windows machine in the same window you set the static address - try making that the Ubuntu box address. Hopefully, that'll let Windows ping Ubuntu...

---

### Post by satish_j on 2009-08-17
Does gateway need to be configured for this??i mean is it mandatory setting?If iam not wrong,2 PCs on same subnetmask does not require gateway..

---

### Post by satish_j on 2009-08-22
Very disappointing...i was out of town for some days.i thought this thread would definitely solve my problem by the time i will return.But,not a single post...:(:(.
I cannot imagine networking windows and Ubuntu will take this much of time.Maybe I should look for other ways or join new forums..

---

### Post by longtom on 2009-08-22
> **satish_j said:**
> Very disappointing...i was out of town for some days.i thought this thread would definitely solve my problem by the time i will return.But,not a single post...:(:(.
I cannot imagine networking windows and Ubuntu will take this much of time.Maybe I should look for other ways or join new forums..

This is a forum from users for users.  Support is therefore not a must but a service of the friendly community when possible.

I have numerous threads which go unanswered - because nobody can help or sees the thread.

I don't think anybody will shiver in fear because you go to another forum.  That's what people do...

However, to avoid further disappointment I suggest to use the fantastic and reliable service of Canonical.  Rates can be found on their website.

Good Luck.


BTW:  I write this from an Ubuntu PC within a windows only network.  Read some online documentation, did what was suggested and of I go.  No jumping through hoops, no ip configuration...and I can see and exchange with everybody.

---

### Post by satish_j on 2009-08-22
> **longtom said:**
> This is a forum from users for users.  Support is therefore not a must but a service of the friendly community when possible.

I have numerous threads which go unanswered - because nobody can help or sees the thread.

I don't think anybody will shiver in fear because you go to another forum.  That's what people do...

However, to avoid further disappointment I suggest to use the fantastic and reliable service of Canonical.  Rates can be found on their website.

Good Luck.


BTW:  I write this from an Ubuntu PC within a windows only network.  Read some online documentation, did what was suggested and of I go.  No jumping through hoops, no ip configuration...and I can see and exchange with everybody.

Very right said..

---

### Post by satish_j on 2009-08-25
well,prob is resolved.It was some settings issue.Thanks anyway for your replies..

---

