---
title: "iptables look good but can't login via ssh"
date: 2009-08-19
forum: General Help
---

### Post by krraleigh on 2009-08-19
I did some surfing through your forum and I was only able to find one thread on iptables, and I don't think that applies to my situation. Now I have worked through a wiki and a few videos on the subject of configuring my iptables on my ubuntu intrepid server sitting out on rackspace.
 
If you check out this address: 
[http://cloudservers.mosso.com/index.php/Ubuntu_Intrepid_-_Setup#User_administration](http://cloudservers.mosso.com/index.php/Ubuntu_Intrepid_-_Setup#User_administration)
 
You will see the steps that I have taken thus far to secure my server.
Right now I am stuck at the part where the wiki has me reload  
```
[inet.d/ssh reload] 
``` and then I try to log back in to my server via putty.
 
For some reason my server accepts the connection but states that I
have "No supported authentication methods available". I have tried to login as root and as me, but I get the same error message.
 
I went back and used nmap -sS localhost to find out what ports where open
and it shows that the only port that I have open is 10000 for perl:
 
Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-08-19 06:04 UTC
Interesting ports on localhost (127.0.0.1):
Not shown: 1714 closed ports
PORT STATE SERVICE
10000/tcp open snet-sensor-mgmt
Nmap done: 1 IP address (1 host up) scanned in 1.248 seconds
 
 
however when I check iptables -L it clearly shows that I have tcp port 54321 open
for ssh.
 
Chain INPUT (policy DROP)
target prot opt source destination
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT all -- anywhere anywhere
ACCEPT tcp -- anywhere anywhere multiport dports www,https
ACCEPT tcp -- anywhere anywhere tcp dpt:54321
Chain FORWARD (policy DROP)
target prot opt source destination
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
 
As the wiki stated I have changed the nano /etc/ssh/sshd_config
file to show me as allowed. 
AllowUser me 
and it has the correct port of 54321, 
which should all be o.k. because when I use putty
to connect to the server it does allow the connection on port 54321;
it just dosen't seem to have anyway to verify who I am. 
"No supported authentication methods available". 
At least that is what I think the problem is.
 
I have been working on this for 2 days now and can't seem to make any headway.
Can anyone advise?
 
Thank You
Kevin

---

### Post by krraleigh on 2009-08-19
I solved the problem.
My iptables were fine.
my problem was that the wiki I listed above was a little vague on dealing with the key-gen. Once I loaded my key putty could connect. Once the correct keys were in place on both workstation and server everything worked great.
 
I am acutally logging in from a win station. And there weren't any decent directions for taking care of business from this perspective
I talked to support over RackSpace and they are going to upgrade the wiki with the appropriate information.
 
Kevin :popcorn:

---

