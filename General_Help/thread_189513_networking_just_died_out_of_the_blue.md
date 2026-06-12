---
title: "networking just died out of the blue"
date: 2006-06-05
forum: General Help
---

### Post by mrweirdo on 2006-06-05
I had been using my newly setup server perfectly configured for about 3 hours or so now as a making use of iptables using Nat to route and share an internet connection with other computers on my network. 

Well all of a sudden right now my networking completely dies on me. The external interface that goes to the cable modem will no longer get a dhcp request so it wont come up with an sudo ifup eth0.  The internal is setup with a static ip of 192.168.1.1 and I have another computer on the lan with 192.168.10 and neather can ping each other.

And yes I have checked my iptables rules using an iptables -L after completely flushing them out to get that out of the equation and it does no good so its not related to iptables. Then after that I tried rebooting multiple times to no avail.  

I'm at a complete loss and not liking dapper to much although I must say I have saw it coming because networking was flakey from the day i installed it from the installation cd. 

I'm using two Intel pro 10/100 PCI nics if that maters.  Hopefully someone has some ideas because otherwise looks like I'm going to have to switch back to breezy or to another distro :/

---

### Post by deadgobby on 2006-06-05
Try this simple thing. Boot down your PC. Turn off the Cable modem and if you have a router. Turn that off too. Wait at least a minute and turn back on the Cable modem and Router. Boot up you Dapper PC while the cable modem is on and/or router too. See if this simple solution fixes you problem.
Gobby

---

### Post by mrweirdo on 2006-06-05
nope didnt work. however it doesnt matter I decided just go out ahead and do a clean install of dapper to try it again. Its posible the last thing i installed before having trouble was snort and that might have had something to do with it and it took time for the networking to break. otherwise hopefully it was a fluke.

For now though Im just gona setup my iptables rules and see how it goes. then I might try installing snort again later down the road. I'm glad i made copys of my iptables script ;)

---

### Post by mrweirdo on 2006-06-07
arg here we go again. I was using it fine for the past day or so even after reboots multiple times untill tonight. I discovered that my dell poweredge bios needed updating so I powered down the system to do that. No mater I fire ubuntu back and low and behold I have once again lost network conectivity.

what is odd about it this time is that the external interface  seemed to still be working. from a terminal on the box I was able to ping outside address like google for example. Now if i try pinging internal addresses it would give me something along the lines of sendmsg: operation not allowed.

so anyways I thought mayby i can repair this: first i went through the process of once again clearing iptables, stoping restarting, nics. Then after that didnt work i decided to try completly uninstalling iptables and iproute. Which didnt seem to do any good so lastly I tryed to disable everything everything but my staticly assigned internal nic in /etc/networking/interfaces. that seemed to do no good eather as i still could not ping on the internal network.

---

### Post by xenblend on 2006-06-08
My network went down right after installing snort as well.  Also KDESU doesnt work for me.  can anyone relate?

---

