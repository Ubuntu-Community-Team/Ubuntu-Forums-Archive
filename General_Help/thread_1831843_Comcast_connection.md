---
title: "Comcast connection"
date: 2011-08-23
forum: General Help
---

### Post by I am Lost101 on 2011-08-23
Hi to all ,
I just recently switch my ISP from a DSL to Comcast. I run a duel boot with Win7. My issue is now Ubuntu will not connect to internet, Win 7 is fine but this is killing me as i like my Linux, its like the difference between driving a Cool 60's Chevy & a New plastic car. Shore new car is nice & runs smooth has plenty of gadgets but hop in the old Chevy rap the gas &, well you know what i mean.
 Issue is i am set up to- net manager see's a connection but just cant make it finial. Can i use setting from windows? 

Here is output from ifconfig:

 eth0      Link encap:Ethernet  HWaddr 00:1b:b9:9f:f9:a5  
              inet6 addr: fe80::21b:b9ff:fe9f:f9a5/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
              Interrupt:19 Base address:0xdead 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:74 errors:0 dropped:0 overruns:0 frame:0
              TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
    [FONT=&quot]          RX bytes:5460 (5.4 KB)  TX bytes:5460 (5.4 KB)[/FONT]   
  Windows ipconfig:

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Family-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : SiS190 100/10 Ethernet Device
   Physical Address. . . . . . . . . : 00-1B-B9-9F-F9-A5
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::81e3:d156:7139:ac66%10(Preferred) 
   Autoconfiguration IPv4 Address. . : 169.254.172.102(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 234888121
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-14-70-D3-ED-00-1B-B9-9F-F9-A5
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{44971C5B-87C2-4A56-818A-9FE2239A149F}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


I know i may have opend my self up to the world by posting this but it pisses me off i cant figure this out.

Thank for any help provided.

---

### Post by llamabr on 2011-08-23
Does it help if you plug right into the router?  You're trying to connect via wireless, I think, right?

Also, what happens with networkmanager?  the little circle just spins?  Do you get a chance to type your password?

Finally, what kind of router are you using?

---

### Post by fragos on 2011-08-24
your ifconfig doesn't include an IPv4 address. Is IPv4 configured?

---

### Post by I am Lost101 on 2011-08-29
Well i think I'm getting closer to making a connection, now it seems i can Google items and get a hit. Web & images, but when i try to pull up a site it just stalls. Also I still can't update the system.
I belive it is due to my router (Netgear WNR 1000) that was supplied by Comcast. When i try to log in to router with any linux web browser i get the log in but nothing further.
I tried going straight through the cable modem same issue. Besides i need the the router due to others using the network in the home.

This is output since making some connection.

ifconfig:

Ubuntu::



eth0      Link encap:Ethernet  HWaddr 00:1b:b9:9f:f9:a5  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fe9f:f9a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5813 errors:793 dropped:0 overruns:0 frame:793
          TX packets:5391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6011936 (6.0 MB)  TX bytes:867906 (867.9 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4260 (4.2 KB)  TX bytes:4260 (4.2 KB)



Thanks again for any help folks! :)

---

### Post by fragos on 2011-08-30
Comcast in CA blocks all but one MAC address. Since Comcast supplied the Router you may need to clone the MAC address of your router on your PC's Ethernet port before connecting to the cable modem.

---

### Post by I am Lost101 on 2011-09-04
Not shore how to to that, I'm already connected. Could you walk me through the way you would do it? If you could keep it in layman's terms.

---

### Post by fragos on 2011-09-04
> **I am Lost101 said:**
> Not shore how to to that, I'm already connected. Could you walk me through the way you would do it? If you could keep it in layman's terms.

Right click the Networking icon in the upper right of your screen and select "Connection Information." Under the "General" section on the line labeled "Hardware Address:" is your Ethernet port MAC address. It will something like 1C:6F:65:B2:63:60. Now we'll need the IP address of the router. On the same display as above there's a section "IPv4", you'll want the IP address of "Default Route" as in 192.168.1.1. Now open your browser and in the location field enter the IP you found. You'll be prompted for ID and Password. For those you'll need to look in the documentation of the router. ID admin and Password admin are common defaults. You'll now be connected to your router's menu structure and again you'll have to depend on the router's documentation or just look through the menus until you find a perhaps a check box for "Clone MAC" which will automatically match your port's MAC or a place to enter the routers MAC.

---

### Post by I am Lost101 on 2011-09-06
Again thank you for your time & help.
I can only try this under Windows.
Under Ubuntu i can not access the router at all.When i try it will ask for user & pass, then it just hangs.
It is a Netgear WNR1000 v.2, which has me puzzled as i have a partial connection?

I will follow your instructions & post back.
Again thank you.

---

