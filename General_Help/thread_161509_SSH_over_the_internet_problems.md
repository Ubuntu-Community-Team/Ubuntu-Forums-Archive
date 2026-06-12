---
title: "SSH over the internet problems"
date: 2006-04-17
forum: General Help
---

### Post by bumfrog on 2006-04-17
Hi

I've done a search but not found an answer....

I have an ubuntu box set up with ssh server on it.  I can ssh to the box from a windows machine, a linux machine and localhost within their local network.  However, the second I try to connect via my external ip address it keeps knocking back my password with permission denied.  And if i try to connect via the windows box with putty on the external ip I get a connection refused error.

Can anybody help?

My sshd_config file hasn't been altered except to remove root login. I have ports forwarded on the firewall on the ubuntu box and on the router.

---

### Post by localzuk on 2006-04-17
What ports have you got forwarding?

---

### Post by nic886 on 2006-04-17
if the ubuntu box with the SSH server is not the one connected to the internet then the problem is likely to be that you need to forward port 22 (or whatever your SSH server runs on)  on your firewall/router to your SSH server ubuntu box. look in your firewall/router docs on how to do this. you cannot simply connect to your PC behind a LAN from the outside internet, because to the internet your LAN looks like 1 computer. i had the same problem running a small Jabber IM on a linux box a while ago and i was ](*,)

---

### Post by localzuk on 2006-04-17
Also, when you say you have ports forwarded on your ubuntu box, do you mean you have opened them?

Have you tried disabling the firewall on the ubuntu box?

---

### Post by bumfrog on 2006-04-17
got port 22 forwarded on the router (a port scan of my public ip detects this) and have tried disabling the firewall on the ubuntu box.

Like I say, it's connecting via the public ip on the ubuntu box, and i've just tried installing cygwin and it connects as well.  The problem I am having is that it's not accepting my user password, which is strange because it's accepting it as an ssh connection on the local network.

---

### Post by localzuk on 2006-04-17
Take a look in your sshd_config file. It may have some sort of config which disallows access from external IP's?

---

### Post by bumfrog on 2006-04-17
my sshd_config looks like this...

Port 22
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
#IgnoreUserKnownHosts yes
PermitEmptyPasswords no
ChallengeResponseAuthentication no
#PasswordAuthentication yes
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no
#KerberosTgtPassing yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no
#MaxStartups 10:30:60
#Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes


don't know if anybody can see anything obvious for external access?

---

### Post by localzuk on 2006-04-17
I've just thought of something - does your router normally have anything running on port 22? Try logging in using a username and password that work on the router. The config seems fine. The only thing I can think of is the router causing issues.

---

### Post by bumfrog on 2006-04-17
[QUOTE=localzuk]I've just thought of something - does your router normally have anything running on port 22? Try logging in using a username and password that work on the router. The config seems fine. The only thing I can think of is the router causing issues.[/QUOTE]

ooooo, i think you're onto something here.  Tried the login details for my router and the fecker is still there hogging port 22 even when it's got a rule telling it to use it for ssh.  arghhh.

may have a spare router round here somwhere......

cheers localzuk.  Will report back later :)

---

### Post by bumfrog on 2006-04-17
arse.  Changed me router and shields up tells me port 22 is open, but all i ever get is connection refused messages.  sshd: ALL is set in my hosts.allow all my firewalls and configs are wide open.

---

### Post by localzuk on 2006-04-17
You could attempt to change the port that forwards - ie. change the port in sshd_config to something like 222 and work with that instead?

---

### Post by harisund on 2006-04-17
By any chance, do you have any machine on the DMZ of the router? Having that may make some routers not immediately port forward. I would suggest you try disabling the DMZ, and try logging in from outside the LAN (Just a suggestion, that is how it is for me .. that is why ). At best you could have your Ubuntu box itself on teh DMZ

---

### Post by Huike on 2006-04-17
What authenticatin method you are using? RSA key or password? In the ssh_config file try remove the # in the PasswordAuthentication line to enable it.

---

### Post by bumfrog on 2006-04-18
thanks for all your help so far.  I'm starting to think I#m being very unlucky with routers.  Checking the auth.log doesn't bring up any attempts for any requests other then internal networks, so I'm guessing it's a router problem, well two routers in fact.

all port scans indicate that i'm open as open can be and even when i change the port to forward (the port forwarding works fine) for bittorrent, it just keeps giving me connection refused.

I don't have anything on a dmz either.  I'm going to borrow me another router from work and see if that makes any difference.

I got a freind to have a look at stuff last night and he couldn't understand it either.

Will post back later after trying a different router.

---

### Post by bumfrog on 2006-04-18
ok, tis getting beyond a joke now.  I have tried an origo, belkin and now onto a netgear router.

It doesn't matter what port I try, what ports I open, what port scanners return or how I stand on my left foot, everytime I try to connect to my external IP I just get connection refused.

This leaves me with the prospect that pipex (my isp) are blocking ssh.

I'm going away to cry now...

---

### Post by oberoc on 2006-04-18
Ok, this is what I want to see. Do a tcpdump on your ubuntu server, and see if there is any traffic coming to your port 22. The syntax for tcpdump will be:

sudo tcpdump -i eth0

Tell me what you get
Tino

---

### Post by bumfrog on 2006-04-18
managed to sort it.  I tried levelling my original router, then got the latest latest firmware/os for it.  Kept it nice and simple.  Then installed ssh on my newly formatted laptop (different machine from the original one in the problem) as a kinda of virgin test.

It all worked... grrrr :)

so I'm just in the process of levelling the original problem box just incase something had gone awry with the install.

Cheers to everybody who has helped :)

---

