---
title: "Static IP problems"
date: 2010-09-14
forum: General Help
---

### Post by bardic on 2010-09-14
Hey all,
I know there are 100's of thread and posts out there that describe how to do this, but none of them are working for me :( 

I've tried using the network manager as described here : [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/) 

and doing it via cli : [http://www.jonathanmoeller.com/screed/?p=1669](http://www.jonathanmoeller.com/screed/?p=1669)

No dice on either of them. Any help would be great. And just in case, here's the output from ifconfig on my active connection : 

```
eth1      Link encap:Ethernet  HWaddr 00:1d:60:de:a2:49  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fede:a249/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4791140 (4.7 MB)  TX bytes:1102682 (1.1 MB)
          Interrupt:16 Base address:0xcc00 

```

---

### Post by e79 on 2010-09-14
It looks like you do have an IP address, probably assigned by DHCP from your router. Now if you are using Ubuntu Server (command line only) and wanted to change that IP address, the instructions you followed at [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)  should have worked.

 If you are using Ubuntu Desktop on the contrary, simply click on System --> Preference --> Network Connetions, select your Network Card, click on 'Edit' and then go to IPV4 Tab and set your informations manually; it worked for me every time.

Hope this helps.

---

### Post by bardic on 2010-09-14
Tried that and still no luck :(

---

### Post by e79 on 2010-09-14
> **bardic said:**
> Tried that and still no luck :(

Have you tried :

```
$ sudo ifdown eth0
```
```
$ sudo ifup eth0
```
```
$ sudo /etc/init.d/networking restart
```

or rebooting the computer for that matter after applying your changes ?

---

### Post by bardic on 2010-09-14
Yes to all :(

---

### Post by e79 on 2010-09-14
Do you still see the changes you have made to your **/etc/network/interfaces** file when attempting to set it manually or nothing else appears there than you 'loopback' (lo) connection ?  If affirmative, please post the output of the file so we can check at it.

---

### Post by asmoore82 on 2010-09-14
If you're on a desktop with Network Manager, you have to actually select the static IP profile after creating it.

You will have to reselect it every time you plug/unplug ethernet as Network Manager will default back to DHCP.

If you are trying to convert a desktop into a Home Server,
I would just disable the Network Manager service and then follow server procedures.

---

### Post by dcstar on 2010-09-15
> **asmoore82 said:**
> If you're on a desktop with Network Manager, you have to actually select the static IP profile after creating it.

**You will have to reselect it every time you plug/unplug ethernet as Network Manager will default back to DHCP.**
.......

Rubbish, I have an IPv4 Static IP set by Network Manager "Manual" and it stays there exactly as it should.

---

### Post by dineshs on 2010-09-15
I suggest you to ensure that  /etc/network/interfaces contains only
```
auto lo
iface lo inet loopback

```
Then configure NM as in
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by bardic on 2010-09-15
Hey all.
Thanks for the replies!
After I make my changes through the network manager my interfaces files still just says 

```
auto lo
iface lo inet loopback
```

@dineshs I followed that thread. I think my biggest issue here is I don't know what to put in for the DNS. when on windows I've always just used 192.168.1.1 or something like that. I've been trying to find the address to the dns server from my isp but no luck yet. Any suggestions?

Thanks

---

### Post by Vaphell on 2010-09-15
your router status page should show dns server - DNS info is sent to your router with the assigned IP. Either way you can use some public DNS IP if you want.
What is your configuration anyway?

---

### Post by bardic on 2010-09-15
Sorry for asking the dumb question, but what is meant by my configuration?

---

### Post by QLee on 2010-09-15
[QUOTE=bardic]... I think my biggest issue here is I don't know what to put in for the DNS. when on windows I've always just used 192.168.1.1 or something like that. I've been trying to find the address to the dns server from my isp but no luck yet. Any suggestions?
[/QUOTE]

Well, if your memory is correct then it makes some sense. That 192.168.1.1 IP address is often used for DNS on a gateway. The DNS will be the same as you used on Windows if you haven't changed anything. Nothing bad happens if you get the number wrong, it just won't be able to resolve addresses.

Note: Many gateway/routers have the ability to assign static addresses by MAC through DHCP (it's a configuration in the router), that would be another way to assign the static IP and I consider it the best way but people's needs differ and the choice is yours.



Or, I suppose, you might choose to use the Google public DNS IP addresses:
8.8.8.8 or 4.4.4.4

---

### Post by dineshs on 2010-09-16
+1 to QLee
You can try [COLOR="Blue"]192.168.1.1[/COLOR] or [COLOR="Blue"]4.2.2.1[/COLOR] or [COLOR="Blue"]8.8.8.8[/COLOR]

---

### Post by asmoore82 on 2010-09-24
> **dcstar said:**
> Rubbish, I have an IPv4 Static IP set by Network Manager "Manual" and it stays there exactly as it should.

There is that "Connect Automatically" checkbox that I couldn't use because I was static IP at only 1 site but DHCP everywhere else. Your mileage may vary.

---

