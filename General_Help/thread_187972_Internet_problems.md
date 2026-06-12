---
title: "Internet problems"
date: 2006-06-03
forum: General Help
---

### Post by jether on 2006-06-03
Ok heres the problem
I installed 5.10 on the same machine as a Windows XP installation. The windows xp works fine on the internet. No problems. When I try to connect to the internet on the ubuntu it dosen't like it.
The weird thing is I can ping anyhting from it and get a reply through ubuntu. I can also type IP address into firefox and it works ok (only tried for google actually but i assume everyhting else is ok). 
Also, when i telnet google port 80 it says "Trying 1.0.0.0". I then ping google, it works and get the ip address. I telnet again and it tries the right address and connects. I don't think theres anyhting wrong with the router because its working in windows XP however, the make is "Surecom". 
Is there anything anyone knows that will sort this out?
Thanks
Jether

---

### Post by jether on 2006-06-04
And it dosen't seem to be only 5.10 i downloaded 6.06 and tried it in live mode and i can get to google if i type the ip address in, but not if i type "www.google.com".

---

### Post by Disty on 2006-06-04
Dude, i posted about this too. I am having EXACTLY the same problems. I can actually get on the google website but NOTHING else on any web programs. Im using VNC to control the ubuntu box, which works fine. It can resolve ip addresses also.

Using 5.10 instal on i386. I'll link my post in a minute, theres a few screenshots etc... (but no useful replys!)

---

### Post by Disty on 2006-06-04
The thread i have posted due to this issue is:

[http://www.ubuntuforums.org/showthread.php?t=184217](http://www.ubuntuforums.org/showthread.php?t=184217)

Is it the same problem? I run a Safecom router although no DHCP. My default gateway device is eth0.

Appreciate any help guys?!?

---

### Post by Disty on 2006-06-04
Hi there again, just been speaking to my mate, and he went through it with me.

The problem for me is that the router wasn't forwarding on the ip addresses, so ubuntu couldn't resolve the websites i was trying to access.

To fix it, go onto the network settings part on administration, and change the DNS to that of your connection. That skips the router entirely :)

Worked for me, and i had an identical problem :)

Hope that helps!

Ditsy

---

### Post by jether on 2006-06-05
[QUOTE=Disty]
and change the DNS to that of your connection. 
Ditsy[/QUOTE]

Sorry what do you mean by this part? Do you mean something to do with the ISP?

---

