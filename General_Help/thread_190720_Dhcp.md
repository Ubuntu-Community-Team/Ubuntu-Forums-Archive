---
title: "Dhcp"
date: 2006-06-06
forum: General Help
---

### Post by kdxrider9262 on 2006-06-06
I'm using a server installation version of 6.06. I was wondering if anyone knew a good DHCP server that I could use?

Thanks,
Steve

---

### Post by ape on 2006-06-06
apt-get install dhcp3-server

---

### Post by kdxrider9262 on 2006-06-06
Ok i did that......Its failing to start any ideas??

---

### Post by ape on 2006-06-07
Have you defined any zone and shared-network entries in your dhcpd.conf file?  Do you get any error messages on the console or the logs?

---

### Post by kdxrider9262 on 2006-06-07
Im sorry as you can tell Im a big n00b with linux.....I have to create a dhcpd.conf file. I did a man dhcpd.conf and read some of that...........Is there a template i can follow anc edit to my needs???

---

### Post by kdxrider9262 on 2006-06-07
Ok I got my server to work properly.....Is there a way I can use address reservation?? I have several servers that I have special ports open on my router...it would be nice if they kept the same IP.....

---

### Post by Thiesen on 2006-06-08
[QUOTE=kdxrider9262]Ok I got my server to work properly.....Is there a way I can use address reservation?? I have several servers that I have special ports open on my router...it would be nice if they kept the same IP.....[/QUOTE]

Would you please tell another newbie (me) how you managed to start the dhcp3-server? I installed the graphic frontend "gdhcpd" so that I could hopefully configure the dhcp server in a graphical way, but the server doesn't even start on my computer.

Edit: Sorry for my total newbie-ness... naturally I had to run gdhcpd as sudo... *sigh*... had a hard time figuring out what to put where in gdhcpd... but with a little help from Firestarter I figured it out... :-)

---

### Post by ape on 2006-06-10
You can add an entry like this to your shared-network, subnet section:

```
host foo {
                        default-lease-time 172600;
                        hardware ethernet 00:00:00:00:00:00;
                        fixed-address 192.168.24.50;
                }
```

of course you will want to replace "foo" with the hostname of the machine that you want to reserve the address for and replace the "00:00:00:00:00:00" with the MAC address of the adapter in the defined host.

--Ape--

[QUOTE=kdxrider9262]Ok I got my server to work properly.....Is there a way I can use address reservation?? I have several servers that I have special ports open on my router...it would be nice if they kept the same IP.....[/QUOTE]

---

