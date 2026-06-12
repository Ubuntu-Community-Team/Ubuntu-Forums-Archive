---
title: "switching between network interfaces"
date: 2006-01-24
forum: General Help
---

### Post by dcer on 2006-01-24
Hi,

I have a laptop with which I connect to the net in two ways. Either connecting to my dsl provider directly or thru a nat using the local network - I have only one network card so I switch between them. If I want to switch from the dsl, I disconnect, change the cable, reconfigure eth0 and give it static addresses and it works. But if I try going from using eth0 back to ppp0 it's not working.

Here's what I tried:

switched cables

run sudo /etc/init.d/networking stop

edited /etc/network/interfaces and changed it back to as it was before configuring eth0

run sudo /etc/init.d/networking start

The ppp0 interface is then up, and all looks well, except I can't access the net with any program. I checked eth0 and it still had the same addresses assigned and everything seemed to want to go thru that.

Then I tried networking stop, dissabling eth0, then editing interfaces, and running networking start. This time firefox just froze when I ran it.

But if I reboot after editing, I get the normal ppp0 connection working again. Is there a way to do this without rebooting?

Thanks in advance.

---

### Post by alamba on 2006-01-24
what does "netstat -rn" say after you have reconfigured for ppp0 and disabled eth0. (Note: make sure you disable eth0, ifconfig eth0 down)

Akshay

---

### Post by dcer on 2006-01-24
netstat -rn gives me this:

```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
213.250.19.90   0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.50.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         213.250.19.90   0.0.0.0         UG        0 0          0 ppp0
```


This is my interface file, maybe I did something wrong here:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


# added by pppoeconf
iface eth0 inet manual

```

If I restart then everything is fine if not - no access to the net. Thanks for helping.

EDIT: i did run ifconfig eth0 down and it disabled eth0, after running networking start eth0 was up again. Should I run some other commend to get the connection? When thing are normal eth0 is enabled but doesn't have any addresses assigned, then everything goes thru ppp0. i can't seem to get rid of the addresses :)

EDIT2: I'll restart now and try netstat -rn when ppp0 is working, then I'll post results here.

---

### Post by alamba on 2006-01-24
The netstat output u've posted is after bringing down eth0? 
Run "ifconfig eth0 down"
if the output is still same:
Run "route del 192.168.50.0"
and then "traceroute oracle.com"
post that here.

Akshay

---

### Post by Tiede on 2006-01-24
You may try installing network-manager, it is available in the universe, I believe...
It is not fully implemented, but it cures all my connectivity problems seamlessly...
to install, do a quick ```
 sudo apt-get install network-manager 
```

---

### Post by dcer on 2006-01-24
ok, after I ran ifconfig eth0 down I had no iterfaces at all, pon dsl-provider didn't work, after running networking start, I had both eth0 and ppp0 up, internet not working. Then I tried ifconfig eth0 down again and the ppp0 connectin failed too. No interfaces. After I set both up again with networking start, I ran route del 192.168.50.0 and got "No such process", traceroute oracle.com gives me "command not found". Maybe I'm missing a program or two :)

I'll try the network manager, hope it works.

---

### Post by alamba on 2006-01-24
hmm...interesting...what interface is your modem on? USB? Ethernet? 

Akshay

---

### Post by dcer on 2006-01-24
it's an ethernet card. ifconfig seems to disable the card altogether.

Just tried networkmanager, ran sudo NetworkManager but nothing happens. This is an applet right? But I can't find it anywhere. it didn't give me any error messages, nor can I find it in the process list. it's probably because I tinkered with the gui a while ago. I'd rather have set of commands I know will work in the terminal. I'm such a noob... :(

---

### Post by Tiede on 2006-01-24
although network-manager is installed using sudo apt-get install network manager, it is run as an nm-applet.
try entering nm-applet in a terminal.

---

### Post by dcer on 2006-01-24
thanks it's running now. Wired network is selected in it now, the only other option is connect to modem... If I click it nothing happens. How do I use it?

---

### Post by Tiede on 2006-01-24
I am not sure, but  believe Network manager detects which is better itself, and will always select a wired network over a pppoe modem... Try pulling out your DSL line and see if it reconfigures itself to use the PPP instead.

---

### Post by alamba on 2006-01-24
Stupid of me to suggest ifconfig down eth0 when its an ethernet card. Sorry...did'nt realise it until you told me the error!!

Akshay

---

### Post by dcer on 2006-01-24
Sorry, I forgot to mention that before.

Network monitor didnt detect the ppp0 connection. either running or not (with cable in), it says the active connection is eth0. The applet seems to be more focused on wireless networking which I don't have. I can set it to scan for wireless automaticly. Or  stop all wireless devices. But I don't use any. I'm using the same card to access the local network or for direct dsl access.

---

### Post by Tiede on 2006-01-24
make sure your ppp0 connection is listed in System->Administration->Networking. If it is not there and not active, nm-applet cannot find it.

---

### Post by dcer on 2006-01-24
It's listed, but says it's not configured, even now when I have it working it says not configured.

I tried networking restart this time and it worked, I switchede from eth0 to ppp0. But now I can't switch back. I reconfigure eth0 (after the switch it had no addresses), and no show. I've noticed one thing, under the Network settings, before I had the Default gateway device set to eth0, now it's dissabled and not showing anything.

EDIT: i didn't think networking stop + start were so different than networkin restart.

I used pppoeconf to configure ppp0.

---

### Post by dcer on 2006-01-24
I think I got it now. A few more tries and I'll post how it worked.

EDIT: 

I made two interfaces files - one for when I use ppp0 and the other for eth0. Now I just copy the one I want to use over interfaces and run networking restart. Before I was always running networking stop and then networking start.

Thanks for the help alamba and Tiede!

---

### Post by tekwarren on 2006-01-27
I've just installed network manager after configuring my broadcom wireless device and all seems to be good. I guess a restart will give me this answer but will NM startup now when I re-login? if not how do I set it to auto start?

---

### Post by Tiede on 2006-01-28
yes, it will start itself up every time. Even if you killed it, it would restart during a session... :D

---

