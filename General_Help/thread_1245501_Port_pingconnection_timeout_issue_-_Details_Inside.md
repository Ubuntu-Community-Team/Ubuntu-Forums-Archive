---
title: "Port ping/connection timeout issue - Details Inside"
date: 2009-08-20
forum: General Help
---

### Post by silentsnake7 on 2009-08-20
I am trying to setup a simple sockso/wordpress server, installed the basic LAMP stack and then got everything up and running. I forwarded all the ports through the router and checked to make sure my ISP doesn't block common ports, they don't. I tested everything through the network, all worked, got my brother to hit the server with SSH and the connection timed out. Tried all the ports that I had opened up and everything kept timing out. BUT everything works in a local environment and through the network. For some reason I can't get outside traffic to hit the ports, I can ping the IP of the machine just fine. I have triple checked to make sure ports are all good and dandy but it still won't go through, I've also turned off the firewall of the router and tried, same result. I tried setting everything through a wired connection, didn't work. And I tried alternative ports, didn't work either. For some reason everything works though the network only, and everything outside the network times out. Which leads me to believe ports are forwarded right, and that it's something on the ISP end, but without them blocking ports I'm lost. It's probably something stupid but I can't figure it out, if you guys have any suggestions it would be greatly appreciated.

tl;dr: ISP doesn't block ports
ports forwarded correctly for all I can see
the wordpress and sockso setup **_WORKS THOUGH THE NETWORK ONLY_**. Nothing can hit the ports from the outside without timing out.
Turned off the firewall, same thing.
Tried a wired connection, same thing.
The machine can be pinged from the outside just fine, ports keep timing out.

Hardware:
Router: Linksys WRT400N dual Band N router, connected to G transmitting end.
Modem: Zyxel 660 series embarq standard modem
ISP: Embarq 5mb/s down 768kb/s up package
Speedtest results: 4.6mb/s down, 690kb/s up
Wireless Card: EDIMAX EW-7128G IEEE 802.11b/g PCI Wireless Card

---

### Post by jtholb on 2009-08-29
Unfortunately I'm experiencing essentially the same thing, but without any luck.  The only ray of sunshine I had was when I would restart firestarter, after opening the incoming ports, it would give me a 1-2 minute window where I could successfully connect with my ports, but then it would give it up after that.  I'm running jaunty as well.  

Any help or suggestions would be fantastic!

---

### Post by Gareth83 on 2009-10-28
sorry that i cant be of any help. i just wanted to say that i have essentially the same problem as well :-/
altho i cant even ping from outside - i get the timed out problem. inside the network is fine. i think i need to learn more about networking in general first and come back to this later. its sad tho, because i was really looking forward to streaming some music...

---

### Post by cariboo on 2009-10-28
You may not be able to access your external ip address from inside your own network. Get one of your friends to try and connect, or take a laptop to a wifi hot spot and try to connect yourself.

---

### Post by Gareth83 on 2009-10-28
i had heard of that. So i used logmein.com to remote connect to my office pc and tried to ping/connect using that. its a really weird loop i guess, but it works and i dont have to leave my desk ;-)

---

### Post by Gareth83 on 2009-10-28
actually, i think it might have something to do with the router's port forwarding (at least partially). I dont have direct access to the router, or its setup page, so it might take some time before i sort things out. will let you know what i manage.

---

### Post by sickly on 2009-10-28
is your phone through your isp?

---

### Post by Gareth83 on 2009-10-29
I only have cable internet, no phone line. I use a cell phone for calls and texts.

---

### Post by sickly on 2009-10-29
you have done a port scan and the ports **are **open? If not try here
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
or use nmap

---

