---
title: "Noob at Ubuntu(Linux)"
date: 2006-04-25
forum: General Help
---

### Post by HiJinks on 2006-04-25
the only time I've dabbed into linux is with fedora, and I couldn't get on the internet.

So I'm ready to try again and hopefully ubuntu will be more friendly :D

anyways, what steps should I take after I install to get on the internet? thanks

---

### Post by tsumi on 2006-04-25
[QUOTE=HiJinks]the only time I've dabbed into linux is with fedora, and I couldn't get on the internet.

So I'm ready to try again and hopefully ubuntu will be more friendly :D

anyways, what steps should I take after I install to get on the internet? thanks[/QUOTE]

Hey HiJinks-

My experience with Ubuntu so far as been that most things just work.. For example, installed on my compaq presario r3000, the first boot goes into X, in a widescreen resolution, network, audio, etc all functioning fine.

Give it a whirl. Come ask again if it gives you any lip. ;)

Cheers

---

### Post by mips on 2006-04-25
[QUOTE=HiJinks]the only time I've dabbed into linux is with fedora, and I couldn't get on the internet.

So I'm ready to try again and hopefully ubuntu will be more friendly :D

anyways, what steps should I take after I install to get on the internet? thanks[/QUOTE]

What modem ??? Analog, ISDN, ADSL, Cable, Satelite etc.
Brand and Model ?
Serial, USB, Ethernet cable ?
ISP ?

Please supply more info.

---

### Post by HiJinks on 2006-04-25
What modem ??? ADSL
Brand and Model ?SpeedStream 5100
Serial, USB, Ethernet cable ? Ethernet
ISP ? SBC Yahoo DSL :x

Done

edit: what if it dont work after I install how do I get help lol

---

### Post by Jagot on 2006-04-25
My ethernet modem worked automatically with Ubuntu - no set up required.  However, if you're not connected when you start up, go to System -> Administration -> Networking.  Select the ethernet connection and go to the properties, then click enable this connection.  Most people use DHCP so select that in the same window, unless you're aware otherwise.  Click OK then hit activate.

---

### Post by mips on 2006-04-25
As per above advise.

How was it setup in windows, did it use a pppoe/dialer cient or just DHCP ???

If you still have windows you can copy and paste output of **ipconfig /all** command here, that should give us some idea.

---

### Post by HiJinks on 2006-04-25
Well On windows, I cannot get online unless I install my mobo drivers, so I always have to use the mobo disk, will this be a problem?





Windows IP Configuration



        Host Name . . . . . . . . . . . . : mike

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : domain_not_set.invalid



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : domain_not_set.invalid

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-04-61-92-9F-F5

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 68.21.6.87

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 68.21.6.88

        DHCP Server . . . . . . . . . . . : 192.168.0.1

        DNS Servers . . . . . . . . . . . : 192.168.0.1

                                            192.168.0.1

        Lease Obtained. . . . . . . . . . : Tuesday, April 25, 2006 2:15:46 PM

        Lease Expires . . . . . . . . . . : Tuesday, April 25, 2006 2:25:46 PM

---

### Post by mips on 2006-04-25
Ok, your speedstream is operating in bridged mode.

You have two options:
1. Configure it for routed mode and let the router do the authentication & pppoe stuff. This way your pc just needs dhcp.

2. Configure pppoe on the pc.

1 is the better longterm option. Choice is yours.

---

### Post by HiJinks on 2006-04-25
I do not have a router connected, why is 1 better for longterm, and can you explain or give links to ways to do it? thanks :D

---

### Post by stabface on 2006-04-25
why not try this, 

either download and burn or order for free from shipit the Ubuntu Live CD, and pop that baby in and see what happens. if everything seem to work ie connected to internet and drivers blah blah blah, if everything is good.  through the install disk in and delete windows and never look back

---

### Post by HiJinks on 2006-04-25
yea I was going too make a new partion and install it to that.

I checked my modem settings and it's not checked to run in bridge mode.. so I don't know :<

---

### Post by Zyphrexi on 2006-04-25
hey I've got sbc yahoo dsl also, but i've got a wireless card that connects to a router which connects to the same modem you have. The only problems I usually have is when dhcp doesn't assign me an ip on our local network. You should have absolutely no problems at all getting online. the things I needed to get online were an essid, wep-key/passphrase. I will say this though, I put a live cd into my stepdads comp, it found everything automatically and set it up, and I was able to use the internet. I found this especially funny since it took him hours to get it set up. yeah so pop in a live cd and see what happens.

---

### Post by mips on 2006-04-25
[QUOTE=HiJinks]I do not have a router connected, why is 1 better for longterm, and can you explain or give links to ways to do it? thanks :D[/QUOTE]

It's better because you will never have to worry about PPPoE again in your life. Why should the PC do this function if the router is capable of doing it ?

try enter the address (one at a time) in a web browser and see if it grants you access to the router:
192.168.254.254 or 192.168.0.1
username:admin
password:admin

I need to find a .pdf manual for this device

SBC might have locked the device down but it can always be reset to factory defualts. Need to find out your ISP info: Username/Password(which you have), VPI/VCI, Encapsulation type (PPPoE PPPoA etc)

But for now just try a livecd and see what happens.

Bottom line: It CAN be made to work.

[http://subscriber.communications.siemens.com/subscriber_networks/faq.shtml](http://subscriber.communications.siemens.com/subscriber_networks/faq.shtml)

The Speedstream 5100 and 5200 can be configured as either a bridge or a router by the Internet Service Provider (ISP). After being configured as a Bridge there are no user controlled settings so the Web Management Interface is not used. If configured as a Router the Web Management interface should be accessable. Regardless of the configuration the Router documentation is included because some ISPs install a Router upgrade.
Most SpeedStream 5100 are configured as a Bridge (but not always) and most SpeedStream 5200 are configured as a router (but not always).
Bridge or Router?  To see if your product is configured as a Bridge or Router check your Default Gateway. If your Default Gateway is 192.168.254.254 your unit is a Router should have access to the Web Management Interface. Otherwise your product is configured as a Bridge and will not have access to the Web Management Interface.
If your Default Gateway shows that your product is configured as a Router and you cannot access the Web Management Interface contact your ISP for troublshooting assistance.

---

### Post by mips on 2006-04-25
Found a manual:
[www.alltel.net/downloads/links/SpeedStream211.pdf](www.alltel.net/downloads/links/SpeedStream211.pdf)

---

### Post by HiJinks on 2006-04-25
Im downloading the live cd right now, if it works I'll posting from my new OS :D

---

### Post by HiJinks on 2006-04-25
ok it works, thanks for all the help i will be doing a full install in a few minutes, wish me luck :p

---

### Post by Zyphrexi on 2006-04-25
gratz, good luck, and welcome to ubuntu!

---

### Post by the_guy1 on 2006-04-25
my Microsoft mn-520 wireless card for my notebook will not work it doesnot reconize that threr is a wireless card ](*,)

---

### Post by ubuntu27 on 2006-04-25
[QUOTE=the_guy1]my Microsoft mn-520 wireless card for my notebook will not work it doesnot reconize that threr is a wireless card ](*,)[/QUOTE]

Hmm. Try the Ubuntu Dapper Drake BETA Live CD: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

and see if it supports your W. Card "Out of box" 

if not. Don't worry. 

Just create a NEW thread and let the guys/girls show you how to "fix" it ;)

EDIT: By the way, do you see your Laptop lsited under this page? [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

