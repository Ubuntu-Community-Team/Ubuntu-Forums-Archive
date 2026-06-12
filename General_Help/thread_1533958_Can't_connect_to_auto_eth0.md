---
title: "Can't connect to auto eth0"
date: 2010-07-18
forum: General Help
---

### Post by djyoung4 on 2010-07-18
so I used to be able to connect through auto eht0 through a wired connection but after I edited my fstab file to add a drive auto eth0 no longer shows up in my connection options.  If I go edit connections it is there but I cannot connect to it.  Any help is greatly appreciated

---

### Post by djyoung4 on 2010-07-18
I tried changing cables and plugging it directly into the cable modem but no dice.

---

### Post by Iowan on 2010-07-18
Does **eth0** show up in (from a terminal) **ifconfig -a** ?

---

### Post by etdsbastar on 2010-07-19
> **djyoung4 said:**
> so I used to be able to connect through auto eht0 through a wired connection but after I edited my fstab file to add a drive auto eth0 no longer shows up in my connection options.  If I go edit connections it is there but I cannot connect to it.  Any help is greatly appreciated

Will you please tell us that what changes have you made in your fstab file, copy and paste the code here.

---

### Post by djyoung4 on 2010-07-20
eth0 does show up when I type ifconfig -a in a terminal and the only thing I did was use pysdm to add a new hard drive to auto mount

---

### Post by prodigy_ on 2010-07-20
> **djyoung4 said:**
> eth0 does show up when I type ifconfig -a in a terminal
Check if the network cable is properly connected and if the LED indicator is on. If this doesn't help, then post what exactly **ifconfig -a** says about eth0. Might also want to do ```
sudo ifdown eth0
``` and ```
sudo ifup eth0
``` to see if any error messages appear.

---

### Post by djyoung4 on 2010-07-20
> **prodigy_ said:**
> Check if the network cable is properly connected and if the LED indicator is on. If this doesn't help, then post what exactly **ifconfig -a** says about eth0. Might also want to do ```
sudo ifdown eth0
``` and ```
sudo ifup eth0
``` to see if any error messages appear.
I tried changing network cables but I don't think the LED indicator is on.  either that or I can't find it.  heres ifconfig stuff:
```
home@home-desktop:~$ sudo ifdown eth0
[sudo] password for home: 
ifdown: interface eth0 not configured
home@home-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
home@home-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:f4:5d:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4304503 (4.3 MB)  TX bytes:4304503 (4.3 MB)

```

---

### Post by prodigy_ on 2010-07-20
> **djyoung4 said:**
> I tried changing network cables but I don't think the LED indicator is on.  either that or I can't find it.
Network LED should be right next to the socket where you plug the network cable (usually in a corner). And usually it should come up as soon as you connect the cable.

> ```

ifdown: interface eth0 not configured
home@home-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.

```

I believe that's normal if you use 10.04. Everything points to the lack of physical connectivity so far.

What device is on the other end of the network cable? Can you reset it?

---

### Post by djyoung4 on 2010-07-20
> **prodigy_ said:**
> Network LED should be right next to the socket where you plug the network cable (usually in a corner). And usually it should come up as soon as you connect the cable.



I believe that's normal if you use 10.04. Everything points to the lack of physical connectivity so far.

What's on the other end of the network cable? Can you reset it (I mean the device your PC is connected to)?

The light does not come on and I have tried reseting my linksys WRT54G broadband router which is connected to a motorola SB5101N cable modem but to no avail.  There are also two seperate XBOX's hooked up to the router and they both work fine.  Thats why I figured it was a software problem.  Could my mobo be fried or something.  Everything else seems to be working fine except for the ethernet port which the light doesn't come on.  [Here]("http://ubuntuforums.org/showpost.php?p=9250871&postcount=1") is my setup in case your interested.  maybe its a hardware issue.  I can tell you though that as soon as i closed pysdm after adding my new hard drive I lost connection and it hasn't come back since

---

### Post by prodigy_ on 2010-07-20
> **djyoung4 said:**
> Thats why I figured it was a software problem.
Try to boot from a LiveCD to see if the problem persists. Also you can use ```
ip link show eth0
```command to get more specific info about network link status.

---

### Post by djyoung4 on 2010-07-20
So I unhooked all cables from my pc and opened it up and repositioned some cables and let it sit for like an hour and then plugged everything back in and it works now.  I swear I unplugged and replugged the network cable in about 50 times.  FRUSTRATING.  anyways thanks for the help prodigy_.  Ill mark it as solved for now but if it happens again then ill post it back here.  I like your 15 things i hate about today's linux though.  Pretty funny but I agree on most of them.

---

### Post by maxschock on 2010-11-29
Hi, i am sorry to dig up this old thread but i am new to ubuntu and i am having a very similar problem that djyoung4 had. i am trying all sorts of things but nothing i do gets eth0 to connect. the led is lighting up and ifconfig does see eth0.

any help would be appreciated

---

