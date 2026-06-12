---
title: "New User Issues"
date: 2010-05-11
forum: General Help
---

### Post by amanda_perkins on 2010-05-11
[IMG]http://ubuntuforums.org/images/editor/separator.gif[/IMG]Okay, I'm a new Ubuntu user and my wireless keeps kicking me off and on and off and on... my connection light is going insane. It's not the network, becuase it has NEVER done this when I connect using vista... what's going on?

Also, in software center, every single software says "not available in this data"? Why?

Last issue, Rhythm Box won't play any of my variously formatted DRM free MP3s. Any advice? 

Thank you so much!

---

### Post by crlang13 on 2010-05-11
Don't know about the network problem, but the MP3 problem should be solved if you install restricted extras

Do a search for restricted extras in the synaptic package manager (not software center) and install that, it should work.

---

### Post by amanda_perkins on 2010-05-11
How do I get there?

---

### Post by warfacegod on 2010-05-11
System> Admin.> Synaptic Package Manager

---

### Post by crlang13 on 2010-05-12
> **warfacegod said:**
> System> Admin.> Synaptic Package Manager

What warface said.

Synaptic has everything the software center has and more, but the GUI is not quite as nice.

---

### Post by efflandt on 2010-05-12
Just one problem, Synaptic is not going to work if networking (wireless) is not working.

Assuming you would normally get an IP address automatically from your wireless, in a terminal (Applications > Terminal), does **ifconfig -a** show an IP address for an interface (what interface and IP)?

If your wireless device is internal what is the output of **sudo lspci -v** related to it?  Or if a USB device what does **sudo lsusb** show for it?

Does **sudo iwlist scan** show the router or AP you are trying to connect it to?

---

### Post by amanda_perkins on 2010-05-12
What do I need to install?

---

### Post by amanda_perkins on 2010-05-12
> **efflandt said:**
> Just one problem, Synaptic is not going to work if networking (wireless) is not working.

Assuming you would normally get an IP address automatically from your wireless, in a terminal (Applications > Terminal), does **ifconfig -a** show an IP address for an interface (what interface and IP)?

If your wireless device is internal what is the output of **sudo lspci -v** related to it?  Or if a USB device what does **sudo lsusb** show for it?

Does **sudo iwlist scan** show the router or AP you are trying to connect it to?

I don't know what any of that means, I'm sorry!

---

### Post by warfacegod on 2010-05-12
Can you use a wired connection?

---

### Post by BoneKracker on 2010-05-12
> **amanda_perkins said:**
> I don't know what any of that means, I'm sorry!

He just wants you to open a terminal, then see what it says when you type in each of those commands (the parts in boldface).

---

### Post by amanda_perkins on 2010-05-13
Okay, thanks.

---

### Post by amanda_perkins on 2010-05-13
No, I'm on a laptop, and I don't have Ethernet or anything either.

---

### Post by amanda_perkins on 2010-05-13
> **efflandt said:**
> Just one problem, Synaptic is not going to work if networking (wireless) is not working.

Assuming you would normally get an IP address automatically from your wireless, in a terminal (Applications > Terminal), does **ifconfig -a** show an IP address for an interface (what interface and IP)?

If your wireless device is internal what is the output of **sudo lspci -v** related to it?  Or if a USB device what does **sudo lsusb** show for it?

Does **sudo iwlist scan** show the router or AP you are trying to connect it to?

Wireless is just being unreliable... here are the responses I got to the commands

ifconfig -a: 
eth0      Link encap:Ethernet  HWaddr 00:1f:16:db:39:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21092 (21.0 KB)  TX bytes:21092 (21.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:56:69:36:51  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe69:3651/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:317632738 (317.6 MB)  TX bytes:13613152 (13.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-56-69-36-51-36-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Sudo lspci v- 
Asks me for a password but won't let me type anything in.

Sudo Iwlist scan-
Also asks me for a password

Thanks

---

### Post by warfacegod on 2010-05-13
By default, the Terminal doesn't display your password or even show any characters. Its a security thing. Partly due to us all posting output from it here. Just type your password and hit Enter.

---

