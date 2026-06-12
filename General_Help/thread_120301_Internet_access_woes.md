---
title: "Internet access woes"
date: 2006-01-21
forum: General Help
---

### Post by christophermoore on 2006-01-21
Hi,

I recently set up a new ADSL connection and wireless LAN. I've connected two wireless laptops running Windows to the LAN, and they work fine, but for some reason I can't get the internet connection running on Ubuntu. I'm dual-booting Ubuntu and Windows, and it works fine if try to access the internet from Windows, but when I try in Ubuntu I just get "connecting..." status messages and I never connect to anything.

I'm using a Netgear WG311T wireless network card and a Linksys DSL-G604T wireless ADSL modem/router.

I tried disabling the security settings on the router, but that did not yield results.

I tried using a wired ethernet connection instead of the wireless card, but that didn't work either.

I can ping some addresses from the Ubuntu terminal, such as [www.google.com](www.google.com), slashdot.org, and the DNS server my ISP has supplied, 203.0.178.191. However, most sites are inaccessible, and even when I can ping those sites, I can't get access to them in Firefox.

However, for some reason, I can access these sites when they have been recently accessed by another computer on the network. I'm not sure if this means they're being cached somewhere?

The following are the screenshots I took of the networking dialogues:

[Network Settings - Connections]("http://members.optusnet.com.au/theauditors/screenshot1.jpg")
[Interface Properties]("http://members.optusnet.com.au/theauditors/screenshot2.jpg")
[Network Settings - General]("http://members.optusnet.com.au/theauditors/screenshot3.jpg")
[Network Settings - DNS]("http://members.optusnet.com.au/theauditors/screenshot4.jpg")
[Network Settings - Hosts]("http://members.optusnet.com.au/theauditors/screenshot5.jpg")

These are the test screens from my router:

[OAM 4]("http://members.optusnet.com.au/theauditors/screenshot6.jpg")
[OAM 5]("http://members.optusnet.com.au/theauditors/screenshot7.jpg")

I really have no idea what the difference is between 4 and 5, or how to interpret those results, or what it means that the "ATM OAM segment ping" fails in OAM 4.

I would much appreciate assistance in fixing my internet connection under Ubuntu, as I'll be using Windows until I can get it working.

---

### Post by christophermoore on 2006-01-21
I apologise, I have figured out the problem already. I found that my router has conflicts with linux; to fix it, I did the following:

> Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases

Look for the line that reads:
alias net-pf-10 ipv6

Change it to:
alias net-pf-10 off #ipv6


---

### Post by Mustard on 2006-01-21
Thanks for coming back and posting the solution.  It may be very helpful for someone else in the future.

---

### Post by andrewsco on 2006-01-24
Hi guys. 

I have recently solved this problem too (many thanks go to this post as it made me realise what I was doing wrong thanks to the pictures)

I will write a little guide (which I guess works for every version of WG311t who have a linksys AP)

- First go to 'System' , 'Administration', Networking.

From here go into ethernet and disable it and enable the wireless connection (so looks identical to picture posted up)

- Then make sure that DHCP is selected in the Configuration bit (again as picture shows) This is where I think my problem was - I had it as static and had all the boxes filled in. All the other stuff I left alone.

- I also took the posts above advice and changed the line as suggested by Chris Moore.

It not should work.

The illustrations really helped me mate - thanks!

Andrew

---

### Post by Neil Crighton on 2006-01-25
[QUOTE=christophermoore]I apologise, I have figured out the problem already. I found that my router has conflicts with linux; to fix it, I did the following:[/QUOTE]

I have a similar problem accessing many websites in Firefox using a wireless connection to a LAN  with an ADSL connection, and it was also fixed by turning off ipv6.

I did this by creating a file in /etc/modprobe.d/ called bad_list, containing the single line:

alias net-pf-10 off

Then I rebooted.  This has the advantage (?) of not modifying the default aliases file.

Does anyone know what the root cause of this problem is, and how I'd go about fixing it?  Turning off ipv6 seems a bit of a band-aid fix.

---

### Post by RAOF on 2006-01-25
[QUOTE=Neil Crighton]I have a similar problem accessing many websites in Firefox using a wireless connection to a LAN  with an ADSL connection, and it was also fixed by turning off ipv6.

I did this by creating a file in /etc/modprobe.b/ called bad_list, containing the single line:

alias net-pf-10 off

Then I rebooted.  This has the advantage (?) of not modifying the default aliases file.

Does anyone know what the root cause of this problem is, and how I'd go about fixing it?  Turning off ipv6 seems a bit of a band-aid fix.[/QUOTE]
IPv6 **is** the root of the problem.  Some routers just don't handle it right, and so when Ubuntu tries ipv6 first, and doesn't recieve a response, it just doesn't work.  For routers which don't handle ipv6 and **report** that they don't handle it (ie: non-broken routers), Ubuntu falls back gracefully to ipv4.

---

### Post by Neil Crighton on 2006-01-25
[QUOTE=RAOF]IPv6 **is** the root of the problem.  Some routers just don't handle it right, and so when Ubuntu tries ipv6 first, and doesn't recieve a response, it just doesn't work.  For routers which don't handle ipv6 and **report** that they don't handle it (ie: non-broken routers), Ubuntu falls back gracefully to ipv4.[/QUOTE]

Ah, thanks.  So the problem is the code in the router?  Is that usually written by the service provider?

---

### Post by RAOF on 2006-01-25
[QUOTE=Neil Crighton]Ah, thanks.  So the problem is the code in the router?  Is that usually written by the service provider?[/QUOTE]
Yup.  The problem is not with Ubuntu - it merely exposes the problem with the router.

---

### Post by kevh on 2006-01-26
Gentlemen, I would like to thank you for solving my problem. Much as I was enjoying searching the forum and learning, I can now access the internet "in the blinking of an eye". (was 15 to 30 seconds). 
As a newcomer to Ubuntu (loaded to PC 4 days ago) I am truly impressed at the positive and helpful attitude demonstrated in this forum. 
Kindest Regards

---

