---
title: "logic vs time...."
date: 2006-05-13
forum: General Help
---

### Post by kaph on 2006-05-13
Hello all :) Yep another newbie... I don't really have a problem yet, but i think after someone replies i will. I have recently installed Ubuntu on a standalone box and placed in my network (192.168.2.*). Everything is working fine :). But i realised that i should have put the box on before my router (192.168.2.*) because it makes no sense at all to have it there and run an IDS (snort) because i can't reach/get any other traffic that is going outside of my LAN because there aren't any sensors to catch anything from any other address to the outside. So here is my dilema.... I have a wireless modem (10.0.0.*) which goes straight to my router (192.168.2.*)...and yes i see straight away what i should have done....I should have placed my IDS/Server (Ubuntu) box after my modem and before my router so my IDS/Server (ubuntu) box will be on 10.0.0.* and capture everything that goes through it to my 192.168.2.* network.
Does this seem right?? Also can someone please tell me what other packages i will have to install? My server runs Apache2, php5, mysql, ssh, Proftpd and mail servers etc... or would it be easier just do do a reinstall?
Any help would be great as my hair is getting thinner as i get older and i don't have enough to pull out as i used to :)
Cheers, Kaph.

---

### Post by skippy81 on 2006-05-13
Ok heres the deal. 

Your modem will be assigned an IP address by your ISP, or whoever runs the wan outside your network.  You will only get 1 IP, so therefore you would need to share that IP out over an internal network so each machine gets an internal ip 192.168 etc, but those machines can also have their outbound traffic routed out over the modem.

If you connect your linux box straight to the modem, then the linux box would have to act as a router.  This would mean that the linux box would 'see' all the traffic flowing though it.  It would also mean that the linux box would be vulnerable to attack.  You would also have to buy at least 1 extra network card for the linux box so that traffic can get through it.  It goes without saying that the linux box would have to be on 24 hours a day.  You would need a switch to split the traffic from the linux box to your internal hosts (but you could use the hardware router for this if you just ignore its WAN port - most routers have a seperate 4 port switch built in).  

The main things that come to mind is that you will have to set up a DHCP server and IP forwarding on the linux box.  This is not too difficult to do.  Just google "linux routing" or "linux dhcp".  

At the end of the day, what you want to do will be a fun project, and it would give you a lot more control over the traffic going between your internal network and the internet.  If however you just want to experiment with packet sniffing, then this will be a lot of work, and connecting a linux box straight to the internet is not for the faint hearted.  While linux CAN be far more secure than Windows, you need to do your research and make sure you have strong passwords, minimal services running and ideally a decent firewall setup.

---

### Post by skippy81 on 2006-05-13
Also could you state your aims please?

Do you want a webserver?
Experiment with packet sniffing? 

etc

---

### Post by kaph on 2006-05-14
Thanks Skippy :) My aims.....well i am really doing this for a bit of research and experience. I am currently studying for these:

CISSP (CERTIFIED INFORMATION SYSTEMS SECURITY PROFESSIONAL)
 
ISSEP (INFORMATION SYSTEMS SECURITY ENGINEERING PROFESSIONAL)
 
SSCP (SYSTEMS SECURITY CERTIFIED PRACTITIONER)
CCSP (CISCO CERTIFIED SECURITY PROFESSIONAL)

Plus a few more...and i am amazed at my dopeyness :) that i only realised what i should have done now. I started off with wanting a web server and am now trying to make it absurdly obscure and still function. I guess it's all of the work that comes with setting it all up and making sure that it runs correctly is what i'm after, i just wondered if it was a viable option.Thanks again Skippy :)
P.S i dropped Fedora for Ubuntu.... am i crazy? no, I am happy :)
P.P.S Sorry about all of the smillies.

---

