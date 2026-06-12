---
title: "Network troubles"
date: 2006-04-18
forum: General Help
---

### Post by JohnnyHaff on 2006-04-18
i can't seem to get ubuntu to recognize my lan connection... haven't even tried to get it to recognize my wireless... heard that was difficult?  anyway... and suggestions?  i enabled the connection...and set it to dhcp, but still no recognition.](*,)

---

### Post by Ramses de Norre on 2006-04-18
If he recognizes the ethernet card it's probably a mallconfigured dhcp server or some other setting that isn't ok.
Whether the wireless is easy or not depends on the chipset, mine worked out of the box but some other cards need a lot of tweaking..

---

### Post by JohnnyHaff on 2006-04-18
it tells me in the Network Settings that "The interface ra0 is active"  and "The interface eth0 is active"  but that's as far as i've gone... do i need to type something in the DNS section?  if so, i don't know what...

---

### Post by ericholte on 2006-04-18
[QUOTE=Ramses de Norre]If he recognizes the ethernet card it's probably a mallconfigured dhcp server or some other setting that isn't ok.
Whether the wireless is easy or not depends on the chipset, mine worked out of the box but some other cards need a lot of tweaking..[/QUOTE]

I'm a newbie with network trouble also. My connection is fine after I type in  "sudo route add default gw 192.168.0.1". Which file do I add this line to so it will get executed automatically. Please explain why it's needed and why it was not done by Ubuntu previously. I want to be able to pass your knowledge onto someone else. Thanks.

---

### Post by Ramses de Norre on 2006-04-18
You'll need to add a line to /etc/network/interfaces in the section of the right device: ```
gateway 192.168.123.254

``` and change it to your gateway.
It's needed because ubuntu can't find your gateway itself..

---

### Post by Ramses de Norre on 2006-04-18
In the DNS section you'll need to specify the name servers if you don't use dns.
If you have a router you can find them at the status page, otherwise you'll need to check your isp manual.

---

### Post by JohnnyHaff on 2006-04-18
how do i add that line to /etc/network/interfaces??

---

### Post by oberoc on 2006-04-18
There are a bunch of editors that you can use, nano being the easiest. 

Applications > Accessories > Terminal

In the window, type:

sudo nano /etc/network/interfaces

(and follow the instructions at the bottom of the scren

---

### Post by Ramses de Norre on 2006-04-18
sudo gedit /etc/network/interfaces
gives you graphical editor.

---

### Post by brousch on 2006-04-18
I often have network connectivity problems when I have both a wireless and wired interface enabled. The best way I have found to fix these problems is to disable the one I am not currently using, then reactivate the one I am using. So if you are trying to use your wired connection (eth0), disable ra0 through the network config, then reactivate eth0. Also make sure eth0 is selected as the default route in the network config.

The non-gui method is to do:
[FONT="Courier New"]sudo ifdown ra0
sudo ifdown eth0
sudo ifup eth0[/FONT]
and sometimes it needs:
[FONT="Courier New"]sudo dhclient eth0[/FONT]

When you are ready to use your wireless, disable eth0 and enable ra0. The initial wireless setup is much easier through the network config gui, but once it is saved in there the command line method is quicker for me.

---

