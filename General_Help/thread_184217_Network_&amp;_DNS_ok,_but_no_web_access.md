---
title: "Network &amp; DNS ok, but no web access?"
date: 2006-05-29
forum: General Help
---

### Post by Disty on 2006-05-29
Hi all,

I'm relatively new to Ubuntu, infact only installed it last night, went ok. However, i can't get on the net. I run both a 5 port ADSL wireless router and a 24 port hp procurve 2524 switch. Hoping to run as a server.

I'm just running a cheap NIC, i chose to manually configure this during the setup. It's now plugged into the 5 port router, and runs a serial connection to the procurve (not yet being used just left it connected)

Now i'm up and running- however, i cannot get on the web. I think the DNS settings must be correct as i can get onto the web-based control panel for the router, and even access that pc using a VNC client. DHCP is assigning properly, however i have now changed to a fixed ip. I can even ping google, from a terminal window and using network tools.

Firefox, aim, email, ftp, anything like that simply **CANNOT** access the net! agh! Even the clock during startup is able to sync using the web.

Could anybody point me in the right direction? i have searched these forums and come accross similar problems, but not the same problem! Mostly it is DNS probs.

I am running ubuntu 5.10 install on a p4 i believe. Any help would be greatly appreciated!

Chris

---

### Post by Disty on 2006-05-29
Guys, sorry to bring this back to the top, but seriously, does nobody have an idea? can't you even point me to another post?

Sorry to be a nuisance! ](*,) 

Chris

---

### Post by craigdele on 2006-05-29
I had a similar problem with a Dlink G604T router.

I found a solution from a post about 6 months ago.

What was happening (i am very much a beginner) is that my ISP addresses in /etc/resol.conf were being over written with the address to access the menu of my router(10.1.1.1 in my case).

After restoring the correct addresses in /etc/resolv_conf  I then commented out the code in the following file that was overwriting the addresses in /etc/resolv_conf.

/etc/dhcp3/dhclient_script

ie the code that begins with make_resolv_conf

Dele

---

### Post by Slim Odds on 2006-05-29
[QUOTE=Disty]Guys, sorry to bring this back to the top, but seriously, does nobody have an idea? can't you even point me to another post?

Sorry to be a nuisance! ](*,) 

Chris[/QUOTE]

Can we get some info?

like "route -n" and "ifconfig"

that would help

---

### Post by chambjon on 2006-05-29
having the exact same problem!!
very new to ubuntu and linux.  I am about ready to pull my hair out,
I have tried to use the tools available and entered my IP address, but no dice.
Please help

---

### Post by Disty on 2006-05-30
Ok, now this is even weirider.

I'm currently controlling the computer using VNC, and have taken a few screenshots.

Firefox seems able to access google (for some really weird reason) however it cannot access any other site at all.

I've got a screenshot of 5 successfull ping attemps at [www.mozilla.com](www.mozilla.com) and an unsucessful attempt at reaching it via mozilla. The error message says:

> The operation timed out when trying to connect to [www.mozilla.com](www.mozilla.com)

This picture is PROOF that i can get on the net... (isn't it!?)

[IMG]http://www.fluppet.com/bad_ubuntu1.jpg[/IMG]

And also this, i dunno what to make of it:

[IMG]http://www.fluppet.com/bad_ubuntu2.jpg[/IMG]

> 
Kernel IP routing table
Destination	Gateway		Genmask		Flags	Metric	Ref	Use	Iface
192.168.1.0	0.0.0.0		255.255.255.0	U	0	0	0	eth0
0.0.0.0.	192.168.1.1	0.0.0.0		UG	0	0	0	eth0


The 5 port router is a Safecom one, and seems to be pretty straight forward. No options that would stop it from accessing the web, and the DHCP seems to be working fine, even though im not using it. I can access the control panel from the web fine. The default gateway is 192.168.1.1, and the ip of the pc is 192.168.1.5

Sorry to bother you all, any help really appreciated :)

BTW don't reaelly understand your post craigdele! i'll have a look at /etc/resol.conf now, but it might not make much sense to me!

Thanks a bunch anyway! ;)

---

### Post by Disty on 2006-05-30
ok, so it did connect to google breifly, however it seems this is not available now. It's as if it's on the offline setting, or it's cache is messed up... However msn also does not work, nor ftp.

---

