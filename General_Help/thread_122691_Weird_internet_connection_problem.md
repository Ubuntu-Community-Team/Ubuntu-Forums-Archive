---
title: "Weird internet connection problem"
date: 2006-01-28
forum: General Help
---

### Post by ld99 on 2006-01-28
Hi, I am having some problem with my internet access.

Basically I have my computer set up to access the internet via my ADSL router/modem (IP: 10.1.1.1). It connects to the router by an ethernet cable. The DHCP server has been configured to assign the IP 10.1.1.2 to this computer (based on the MAC address of the ethernet card).

Ok, so I never had any problem accessing the internet while this computer runs Windows or when I use another Windows-based computer on the network.

Anyway, even though my freshly-installed Ubuntu seems to detect the network card without any problem, it seems to choke a bit when it tries to use the internet. I am only able to access certain sites (e.g. official Ubuntu websites, slashdot.org), but even then, it sometimes seem to hesitate a bit. I am unable to access most of the other websites (e.g. google.com, gmail.com, yahoo.com,). The error message is either time-out or refused.

During my research I discovered if I change the DNS setting in the network setting of my ethernet card (eth0) from 10.1.1.1 to the DNS of my ISP, I _sometimes_ would be able to access the internet without any problem. But even then, the relief is only temporary, because the DNS setting kept reverting back to 10.1.1.1, and my internet access becomes limited once again.

I guess I can keep changing the DNS setting, and that IS what I've been doing all night. And, well, it is getting a little frustrating. :???: 

I am really not too sure what is going on. My questions are:
1. Why does my internet only work for certain sites when the DNS is 10.1.1.1?
2. Why did the DNS change solve the problem?
3. Why did the DNS setting keep on reverting back?

Any insight would be appreciated!! Thank you very much.

PS. Oh yes, I am a linux n00b.

---

### Post by ld99 on 2006-01-28
Well, I found another post in the forum which helped me in this problem. ([http://www.ubuntuforums.org/showpost.php?p=681288&postcount=4](http://www.ubuntuforums.org/showpost.php?p=681288&postcount=4))

Basically I edited /etc/dhcp3/dhclient.conf by the command
> sudo gedit /etc/dhcp3/dhclient.conf

Then just before "request [blah blah blah]", I added the line:
> prepend domain-name-servers [my ISP's primary DNS],[my ISP's secondary DNS];

There is no "#" at the start of the line, for obvious reason (though it wasn't obvious when I first did it).

Then restart the ethernet card by typing (in terminal window):
> sudo ifdown eth0
sudo ifup eth0

Then internet worked!!

(At least it has been for the last 10 minutes... Let's hope it will last.)

Thank you to stream303 who probably didn't even realise his post helped me. :)

Still, just for curiosity, does anyone know why the internet worked only for some sites, but not others? When I was having the problem, I could still ping, say, google.com, but the page would never load. Anyone?

---

### Post by stream303 on 2006-01-28
Glad I could help.

Actually, in many cases it might be even easier to go into your router's setup page and add those isp nameservers there, but it's generally safer publicly to just edit some text files you can revert back to if things go haywire. :)

When you reboot, or when your dhcp lease time is up, the dhclient scripts usually end up overwriting your working /etc/resolv.conf.  This is caused by the **make_resolv_conf()** function found in either dhclient-enter-hooks, or dhclient-script.

One other solution that could be used would be to create a working resolv.conf, and then find and rewrite the make_resolv_conf() function do nothing, but I find it easier to use the prepend directive in dhclient.conf instead.

---

### Post by ld99 on 2006-01-29
[QUOTE=stream303]Glad I could help.
[/QUOTE]

LOL... I didn't think you'd see this post. :-D 

I think the prepend command seem to work well enough. But I think when the DNS assigned by my ISP changes (I only get dynamic DNS), I will have to change the dhclient.conf again.

> Actually, in many cases it might be even easier to go into your router's setup page and add those isp nameservers there, but it's generally safer publicly to just edit some text files you can revert back to if things go haywire. :)


Anyway, I didn't quite understand what you said about adding the nameserver (I assume that is the same as the primary/secondary DNS) in the router's setup. The router already knows the DNS... that's where I copied the DNS from initially. So how does adding the DNS to the router help?

And does anyone know why when the network setting has only my router's IP, internet would still work, but only for limited sites? I also thought it was curious that ubuntu website works, but google.com doesn't work? Conspiracy theory, anyone? ;)

---

### Post by stream303 on 2006-01-29
> 
I think the prepend command seem to work well enough. But I think when the DNS assigned by my ISP changes (I only get dynamic DNS), I will have to change the dhclient.conf again.

Good point!  Its definitely something to keep in mind if all the resolutions fail in the near future.  I've been lucky that my isp hasn't changed addresses in a few years.

> 
Anyway, I didn't quite understand what you said about adding the nameserver (I assume that is the same as the primary/secondary DNS) in the router's setup. The router already knows the DNS... that's where I copied the DNS from initially. So how does adding the DNS to the router help?

In the case of my netgear router, it only provided it's own dns services via a default private ip address (172.16.0.254) and that was the only one that dhclient latched on to.  It didn't seem to work well, and usually caused dns timeout delays, so I manually put in the public ip address of my isp's servers in the netgear config.  Now my /etc/resolv.conf has the proper isp nameservers instead of just the one internally defaulted to the netgear.  The result is the same as manually editing the dhclient.conf file.

> And does anyone know why when the network setting has only my router's IP, internet would still work, but only for limited sites? I also thought it was curious that ubuntu website works, but google.com doesn't work? Conspiracy theory, anyone? ;)

I'd like to know this too.  Vendors not following the dhcp specs?  dunno...

---

