---
title: "[Help] SSH"
date: 2006-05-12
forum: General Help
---

### Post by jhorner on 2006-05-12
I have posted this question before, but didn't get much of an answer previously; either way the problem is still unresolved.

I installed the SSH and OpenSSH packages on my Breezy box.  I enabled the SSH service and opened the 22 port on my Router.  Recentley I ran the "netstat -tuna" command to make sure that the port was open and the service was running on my box.  And it showed up, :22...SSH.  However, I am still unable to remotely access my box via SSH.  I have tried through Putty on XP_SP2 and my friend has tried on his ubuntu box to no avail.  Does anyone have any suggestions?  

Thank you

---

### Post by Ramses de Norre on 2006-05-12
Do you use a firewall? You'll need to open port 22 there too.

---

### Post by cgjones on 2006-05-12
Do you have the port forwarded to the right computer? Who are you trying to log in as? Can you access the computer from another computer on the LAN? What kind of errors, if any, are you getting?

Yeah, and the firewall thingy. (Thanks Ramses, I almost forgot about that)

---

### Post by jhorner on 2006-05-12
[QUOTE=cgjones]Do you have the port forwarded to the right computer? Who are you trying to log in as? Can you access the computer from another computer on the LAN? What kind of errors, if any, are you getting?

Yeah, and the firewall thingy. (Thanks Ramses, I almost forgot about that)[/QUOTE]

Sorry forgot to mention.  No software firewall.  Yes, the port is fowarded to 192.168.2.2 my box.  I am trying to log in with my username, but with Putty, I do not have to enter this info.  I haven't tried accessing it from any other computers on the Lan; I will try that this evening.  I did however try ssh justin@localhost and connected w/ no problems. As far as errors, with Putty it is  "Network Error : Connection Timeout".  Also, checked the Log on the firewall and I am not receiving error messages about this particular IP being blocked by the firewall.  Thanks for the replies.  Justin

---

### Post by cgjones on 2006-05-12
Why don't you have to enter your username with PuTTY? Have you ever been able to access the computer via SSH, or has it never worked? When you say you checked the logs on the firewall, you mean the hardware router/firewall?

---

### Post by m.musashi on 2006-05-12
[QUOTE=jhorner]Sorry forgot to mention.  No software firewall.  Yes, the port is fowarded to 192.168.2.2 my box.  I am trying to log in with my username, but with Putty, I do not have to enter this info.  I haven't tried accessing it from any other computers on the Lan; I will try that this evening.  I did however try ssh justin@localhost and connected w/ no problems. As far as errors, with Putty it is  "Network Error : Connection Timeout".  Also, checked the Log on the firewall and I am not receiving error messages about this particular IP being blocked by the firewall.  Thanks for the replies.  Justin[/QUOTE]
I had a very similar problem and discovered that I had to forward port 22 on my router AND my modem. If you have a broadband modem it likely has a firewall as well.

---

### Post by jhorner on 2006-05-12
[QUOTE=cgjones]Why don't you have to enter your username with PuTTY? Have you ever been able to access the computer via SSH, or has it never worked? When you say you checked the logs on the firewall, you mean the hardware router/firewall?[/QUOTE]

Yes, one time.  At the Apple Store, which completely baffles me.  The mac would connect but Ubuntu will not.  Yes, I checked the logs on the Hardware firewall; I do not have a software firewall on the computer.  I will check out the Modem this afternoon when I get home.  Thanks again.

---

### Post by jhorner on 2006-05-12
[QUOTE=jhorner]Yes, one time.  At the Apple Store, which completely baffles me.  The mac would connect but Ubuntu will not.  Yes, I checked the logs on the Hardware firewall; I do not have a software firewall on the computer.  I will check out the Modem this afternoon when I get home.  Thanks again.[/QUOTE]

Update :  Checked the modem, doesn't even have an option to open / close ports.

---

### Post by m.musashi on 2006-05-12
[QUOTE=jhorner]Update :  Checked the modem, doesn't even have an option to open / close ports.[/QUOTE]
I don't know that this is the root of your problem but on my modem the port forwarding was called something very different and at first I didn't know that that's what it was. I can't remember at the moment but it was something like application permissions or security or something. If your modem has a hardware firewall, I'd be surprised if it didn't offer a way to port forward. What modem do you have? Do you have access to a manual? Mine is an Actiontec DSL.

---

### Post by jhorner on 2006-05-12
[QUOTE=m.musashi]I don't know that this is the root of your problem but on my modem the port forwarding was called something very different and at first I didn't know that that's what it was. I can't remember at the moment but it was something like application permissions or security or something. If your modem has a hardware firewall, I'd be surprised if it didn't offer a way to port forward. What modem do you have? Do you have access to a manual? Mine is an Actiontec DSL.[/QUOTE]

Thanks for the reply.  It is a Motorola SBV4200 VOIP Cable Modem.  What I really don't understand is how I could access it from the Apple Store but not from anywhere else.?  ](*,)

---

### Post by skippy81 on 2006-05-12
Why dont you try a bit of troubleshooting?  Temporarily take the router out of the network.  Connect your linux box directly to the modem, it should get a proper ip (ie not a 192.160.x.x) one through DHCP.  Then try to telnet in with putty from elsewhere on the net. [http://checkip.dyndns.org](http://checkip.dyndns.org) is a good way to check the new IP of your linux box.  

If this works then you can concentrate on your router.  Reconnect it.  I personally set up my router so it always assigns the same IP to my linux server.  You need to port forward 22 to the mac address or IP of the linux box, you also need to completely drop the firewall on 22. Again use dyndns to get the IP address of your router, get a mate to use nmap and portscan your router to check that the ports you think are open ARE open.

---

