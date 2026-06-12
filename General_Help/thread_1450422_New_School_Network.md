---
title: "New School Network"
date: 2010-04-09
forum: General Help
---

### Post by leewiest on 2010-04-09
I have the opportunity to present Edubuntu as a solution to replace a school's network. Currently the school has 2 Windows 2000 servers, which really do nothing but one is a DHCP server and the other is a DNS server, connected to a T1 line through Cisco 2850 router (Sonic Wall between the router and T1 line). About 50 windows xp machines, but none of them connected to the server.
 
This school is an elementary school with 43 students (63 counting PK and KG), 50 xp pro machines, 12 vista home cpus. They have 53 ethernet drops.
 
They are now, on the advice of a "consultant" replacing the old ethernet with 164 drops! The current 3Com (one each - 48 and 24 port) switches with 2 48-port switches ($12,000 @) and 3 24-port Cisco switches ($6,000 @). And, of course, the standard -- a DHCP server and a DNS server, each with Windows Server 2008 (each server costs in excess of $3000). The new drops already cost the school $48,000+.
 
In my opinion, they, because of lack of knowledge, are being taken to the cleaners!
 
If anyone can point me to where I can find information on setting up a school network - I would sure appreciate it. I am not totally ignorant, but am new to Ubuntu/LTSP.
 
What I want to present is (stuck with the 2 windows servers, but not opposed to not using them at all - purchased with eRate so I am willing to just let them sit for 5 years! LOL) a linux solution, from the T1 on. I am thinking:
 
2 servers - failover - DHCP, DNS, etc. A firewall - DansGuardian (can be on same server as DHCP???) - an application server (and I know I will need to run a windows server as well for a couple of applications), and DAS storage would be nice. I am looking to save the school some money, yet give them a state-of-the-art solution using LTSP, security, and storage with failover (as opposed to just plain backup) for staff and students (in this case, only about 20 students).
 
Can I do all of this using Ubuntu/Edubuntu on 4 servers? (2 DHCP/DNS etc, 1 Firewall/Proxy, and 1 Application/File/DAS storage server)? Can I be pointed to somewhere on Ubuntu/Eduntu forums that have this sort of info? (I tried, but didn't seem to come up with anything, readily anyway. These are large and deep forums and perhaps I didn't ask the right things when searchinig, for which I apologize).
 
Thanks.

---

### Post by akakingess on 2010-04-09
Hi leewiest, I don't really have any answers for you, but just wanted to clarify, are you going to run edubuntu on all of the 'students' computers as well as replacing or reusing the servers? If so, you are on the right track with edubuntu, but if all you are going to be replacing are the server then I would definitely just stick with the straight Ubuntu Server distro. I'm hoping that by clarifying you might get some more responses and I am interested in some of this information as well. Good luck to you, I hate to hear about educational institutions being taken advantage of, which is what appears to be happening at this point.

---

### Post by leewiest on 2010-04-09
Hi. Thanks for responding.
 
Actually, I have carte blanche. My main thing is I don't know how many servers and what I should put on them (from a linux perspective) etc. I plan on an LTSP network though, for all the students, utilizing the old (P4, 2.9Ghz, 512-2G RAM) Dell - small desktops as terminals. I may or may not have staff have dual booting -- my inclination is to put them on the linux network as well -- thus the application and file server question. This would be my first full-scale network implementation -- hardware, infrastructure, training, online/remote support, on-site support, etc.
 
The school will do what I recommend -- I have the principal and the school board on my side. All I have to do is show that it is a better solution for them, and it is, not only immediately but over the next 5 years. So, costs (hardware and support) will be amortized.
 
Once I do this, I will duplicate it at another school that has about the same number of staff but 20 more students. Then, I have another school with 3-400 students that is interested in some sort of solution along these lines (LTSP). 
 
If I can successfully implement these 3, I have a very good chance at getting upwards of 60 more schools -- all at about the same place re. school budgets, upgrading old networks, etc. I know I am going to need help! LOL

---

