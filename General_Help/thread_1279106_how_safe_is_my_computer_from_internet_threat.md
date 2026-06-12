---
title: "how safe is my computer from internet threat?"
date: 2009-09-30
forum: General Help
---

### Post by abhilashm86 on 2009-09-30
when there are more than 4000 ports(to access) and establish connection, if a person can snatch our or root password? how safe is our system? 

What stops from a tcp/ip packet from our system when it tells a different protocol? like if i don't open ssh port for example......

i just want to know if someone knows which port is open on my computer system and ip address, will they be able to gain access??
i've disable remote login in login window, i can easily connect through terminal-server client tool........
do ask again if you don't understand my question :)

---

### Post by badger_fruit on 2009-09-30
An internet hacker will port scan mass numbers of IP addresses; if there are any ports found open they will then attempt "brute force" attacks.

For example, if you have SSH port 22 open on your firewall and forwarded to your ubuntu machine, you can do:-

```
tail -f /var/log/messages
```

and actually watch them trying to break your passwords using a set of "standard" passwords - eg "password" and so on.

If your port is not forwarded on your router/firewall to your PC then no such attack will happen as the port just replies "Closed".

It's recommended to change the default ports for important things such as SSH to something different or close totally unless needed.

**They can never "snatch" your root password, only guess at it.**

In other words, RELAX!! Sure, there may be 4,000+ ports open but unless you used a simple root password then you've nothing really to worry about.

Certain ports need to be open - for example if you host your own FTP server - and they ***will ***be attacked, make sure you have strong passwords and you'll be OK.

A great password strength checker can be found here --> [http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by Commander_Keen on 2009-09-30
the Root account by default is turned off.
You should have a pwd of 15 char. and not less.
the only reports of the OS being hacked is when the hacker is sitting at the keyboard.
Most hackers, and virus and addware attach windows, because its easier.
Linux on the other hand, Is much harder...
Go to [www.sheildsup.com;](www.sheildsup.com;) Dslreports.
It should tell you how safe you are.

---

### Post by 3rdalbum on 2009-09-30
> **abhilashm86 said:**
> when there are more than 4000 ports(to access) and establish connection, if a person can snatch our or root password? how safe is our system?

Firstly, Ubuntu doesn't have a root password, or it's deactivated and unusable. One of the two. So getting the root password is quite daft on Ubuntu, unless there is one.

Secondly, if you try to access a port that doesn't have anything listening to it, the only response you can get is "Sorry, wrong address". There's no way an attacker can just suck the contents of your hard disk through a closed port.

> What stops from a tcp/ip packet from our system when it tells a different protocol? like if i don't open ssh port for example......

SSH only listens on what, port 22? Something like that? (can't be bothered to Google). If the incoming header says port 22, then the program listening at port 22 will recieve the incoming connection. I don't know what happens if you had more than one program listening on a single port or if that is possible.

> i just want to know if someone knows which port is open on my computer system and ip address, will they be able to gain access??

Let's say you have Apache running, and listening on the standard Port 80 (HTTP port). And let's say that there's an attacker who knows your IP address, and port 80 is not protected by your firewall. If the attacker tries to connect to port 80, then Apache will respond. The attacker would need to find a way to trick Apache into executing commands on a shell, in order to have an effect on your computer. This requires some skill, and there are certain barriers in the way of doing this on a modern Linux system. Plus, Apache is one of the most tested and hardened programs available to mere mortals today!

Even so, Apache doesn't even run as root, not does it run as your user account. It runs under a very limited user account called "www" that basically only has read access to /var/www and write access to wherever it keeps its logs. So if the attacker got Apache to execute some shell commands, they would only execute as the "www" user, which is worthless because the www user can't do anything interesting. The attacker would need to also find a way around the whole Linux security system... oh forget it, why not just install some trojans on a Windows machine?

I recommend looking on Google for the site "Shields Up" which is an online port scanner. It will tell you what ports your system is listening to. By default, Ubuntu doesn't listen to any incoming ports. If you install servers, then those will listen. If Shields Up shows that you have open ports, then remove the servers, configure your firewall to block those ports or ensure that the servers are configured to be as tightly secure as possible.

---

### Post by credobyte on 2009-09-30
```
sudo ufw enable
sudo ufw default deny

```All ports closed ( stealth ). Problem solved.

---

### Post by badger_fruit on 2009-09-30
[FONT=Verdana][SIZE=2]> **3rdalbum said:**
> Firstly, Ubuntu doesn't have a root password, or it's deactivated and unusable. One of the two. So getting the root password is quite daft on Ubuntu, unless there is one.

By default is is turned off in ubuntu but in other distros, it's not the case. I know this is an Ubuntu forum so chances are the guy's running it but you never know ;)

> **3rdalbum said:**
>  Secondly, if you try to access a port that doesn't have anything listening to it, the only response you can get is "Sorry, wrong address". There's no way an attacker can just suck the contents of your hard disk through a closed port.


Correct.

> **3rdalbum said:**
>  SSH only listens on what, port 22?[quote]

Yes, SSH is on port 22 by default but can (and SHOULD) be changed to something else; **/etc/ssh/sshd_config** (if I recall correctly) will allow you to change the "Listen port" to something else. just remember what you change it to!

[quote=3rdalbum;8030841]I don't know what happens if you had more than one program listening on a single port or if that is possible.

Although it's possible, only one of the two (or more) apps would work; most firewalls will only allow a single instance of a specific port to be forwarded to a single IP address - I can't say I have tried running multiple services on a single port, I can't say it would produce good results though!

> **3rdalbum said:**
>  I recommend looking on Google for the site "Shields Up" which is an online port scanner. 

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)


[/SIZE][/FONT]

---

### Post by Slim Odds on 2009-09-30
> **badger_fruit said:**
> [FONT=Verdana][SIZE=2]Yes, SSH is on port 22 by default but can (and SHOULD) be changed to something else; **/etc/ssh/sshd_config** (if I recall correctly) will allow you to change the "Listen port" to something else. just remember what you change it to![/SIZE][/FONT][FONT=Verdana][SIZE=2]
[SIZE=2]This is a common problem on the interwebs. Some people might read this and think that there is actually more security in changing the port number for SSH. Problem is, it's just not true.

There is never security through obscurity. If you think that you're "hiding" the SSH server by changing the port, you are sorely mistaken.

The scanning scripts that the hackers on the net are running are much smarter than that. They will find any service running on any port. Unless the services themselves are secure, you have a problem.

When I run an SSH server that I expose the Internet, I completely disable username/password access. I allow only key based access. You should too.[/SIZE]   
[/SIZE][/FONT]

---

### Post by cdenley on 2009-09-30
Online port scanners like "Shields Up" will scan the device connected directly to the internet, which for most people is their router. This will usually not tell you anything about your computer, but if no ports are "open", then there is no service to attack from the internet. Those online scanners often warn about ports being "closed" or "filtered" instead of "stealthed". The difference is "stealthed" ports simply ignore packets instead of sending a rejection response. There is very little if any benefit to "stealthing" your ports.

---

### Post by abhilashm86 on 2009-09-30
thanks a lot friends, i have a overall idea now what's happening:)

---

### Post by abhilashm86 on 2009-09-30
> **cdenley said:**
> Online port scanners like "Shields Up" will scan the device connected directly to the internet, which for most people is their router. This will not usually not tell you anything about your computer, but if no ports are "open", then there is no service to attack from the internet. Those online scanners often warn about ports being "closed" or "filtered" instead of "stealthed". The difference is "stealthed" ports simply ignore packets instead of sending a rejection response. There is very little if any benefit to "stealthing" your ports.

i see many people using nmap to detect opened ports, but i don't know whether they test web-servers or they also allowed for scanning local computers based on ip address...........

---

### Post by 3rdalbum on 2009-09-30
> **Slim Odds said:**
> [FONT=Verdana]
This is a common problem on the interwebs. Some people might read this and think that there is actually more security in changing the port number for SSH. Problem is, it's just not true.

It does tend to lower the number of attempted logins, which makes it less likely that the correct port will be attacked, but not actually more secure. It's a very fine line concept and difficult to understand unless you think it through... so I let people say that it's "more secure", the difference is narrow :-)

> The scanning scripts that the hackers on the net are running are much smarter than that. They will find any service running on any port. Unless the services themselves are secure, you have a problem.

Obviously, not all attackers will have such smart scanning scripts, because using a different port for SSH does reduce the number of failed logins.

Also, it's like the old "let's work together against scammers" argument. The argument is that if everyone pretends to fall for "419" scams and co-operates with the scammers but doesn't send money or bank details, then the scammer's time is just completely wasted - lots of work for no reward, so they quit trying to scam people, and then EVERYONE is safe.

Well, if everyone changes their SSH port number, then the attacker's computer time is spent trying to connect to each person's computer over 65,000 times. This takes a couple of minutes, right? Well, if everyone randomises their SSH port numbers, then attackers get 65,000x less return on the effort spent. Attacking SSH no longer becomes profitable and so people stop doing it, thereby making everyone safer.

Yeah, pick holes in that :-)

---

### Post by cdenley on 2009-09-30
> **abhilashm86 said:**
> i see many people using nmap to detect opened ports, but i don't know whether they test web-servers or they also allowed for scanning local computers based on ip address...........

Using port scanning tools like nmap can be misleading when you run it from the computer you're scanning, since it will often show services which aren't actually visible over the network. If you scan your WAN IP from another computer on the internet, then it would be the same as "shields up". Using nmap from another computer on the LAN would give you useful results for testing the computer itself. The best way to check for "open" ports, or listening services, is this command.
```

sudo netstat -tulnp

```
This shows all processes listening to any TCP or UDP port. By default, there should be cups listening to 127.0.0.1:631 (127.0.0.1 means only local connections) and avahi listening on some UDP port (nothing to be concerned about). Services filtered by any firewall will still show in this output, though.

---

### Post by 3rdalbum on 2009-09-30
> **cdenley said:**
> There is very little if any benefit to "stealthing" your ports.

If I was writing a malicious port scanner, it would attempt to scan a couple of hundred well-known port numbers. If there was no reply at all, it would assume that the IP address was not in use and move on.

I don't know if that actually happens, but it's just what I assumed the whole difference was.

Also, if your ports are stealthed during a port scan, your outgoing internet connection isn't bogged down by sending back 65,530-odd "wrong number" replies :-)

---

### Post by cdenley on 2009-09-30
> **3rdalbum said:**
> If I was writing a malicious port scanner, it would attempt to scan a couple of hundred well-known port numbers. If there was no reply at all, it would assume that the IP address was not in use and move on.

I don't know if that actually happens, but it's just what I assumed the whole difference was.

Also, if your ports are stealthed during a port scan, your outgoing internet connection isn't bogged down by sending back 65,530-odd "wrong number" replies :-)

Port scanners, including malicious ones, will usually scan the ports it intends to scan regardless of whether previous scans resulted in the packet being dropped or rejected. Besides, if you don't have any services, a port scan will be of no use to an attacker anyway.

Rejection packets won't bog down your network any more than the port scan itself. It would be very trivial.

---

### Post by Giblet5 on 2009-09-30
Any computer is perfectly safe when it is powered off, disassembled, and all of the disk drives melted to ash.

Other than that, there is risk.

That's how it is. Anyone who says otherwise is selling something.

---

### Post by credobyte on 2009-09-30
> **Giblet5 said:**
> Any computer is perfectly safe when it is powered off, disassembled, and all of the disk drives melted to ash.

Other than that, there is risk.

That's how it is. Anyone who says otherwise is selling something.

No matter what you do, you can't be "perfectly safe" - physical damage will apply, no matter in what state your computer is.

---

### Post by underyourskin on 2009-09-30
Thank you for those threads. I found them usefull. Call me paranoid, but I was a victim of identity theft a few years ago and it caused no end of problems. Some of which still exist!! this was an over the shoulder (carelessness) attack and not related to internet. I dread to think what might have happened if it had been a few years later when everyone uses gate's powered pc's for financial transactions. Thankfully, I use and support systems such as Ubuntu. A greater comfort is the community that is on hand to give advice and guidance on personal computer privacy. After much investigating, I have found that using a linux based laptop, used for everyday internet with mobile broadband gives better security than any other domestic alternative. No VPN's, remote desktops fixed IP's etc. If you need to access other systems, use a machine that's not domestic and has no link to any personal banking or credit card transactions. People are strange, people are smart. Never underestimate the scope of greed.

---

### Post by Slim Odds on 2009-09-30
> **3rdalbum said:**
> Well, if everyone changes their SSH port number, then the attacker's computer time is spent trying to connect to each person's computer over 65,000 times. This takes a couple of minutes, right? Well, if everyone randomises their SSH port numbers, then attackers get 65,000x less return on the effort spent. Attacking SSH no longer becomes profitable and so people stop doing it, thereby making everyone safer.

You seem to think that there is a hacker person just sitting there typing away at a keyboard. The ones that will actually score on your computer are automated. They are running on multiple systems (even botnets). They have the time. A couple of minutes per host is nothing to them. They run 24/7 and report back when they get a hit.

Changing your port may fool the stupid hackers. It's the smart ones that you should be worried about.

---

### Post by abhilashm86 on 2009-10-01
> **underyourskin said:**
> Thank you for those threads. I found them usefull. Call me paranoid, but I was a victim of identity theft a few years ago and it caused no end of problems. Some of which still exist!! this was an over the shoulder (carelessness) attack and not related to internet. I dread to think what might have happened if it had been a few years later when everyone uses gate's powered pc's for financial transactions. Thankfully, I use and support systems such as Ubuntu. A greater comfort is the community that is on hand to give advice and guidance on personal computer privacy. After much investigating, I have found that using a linux based laptop, used for everyday internet with mobile broadband gives better security than any other domestic alternative. No VPN's, remote desktops fixed IP's etc. If you need to access other systems, use a machine that's not domestic and has no link to any personal banking or credit card transactions. People are strange, people are smart. Never underestimate the scope of greed.

i'd also same problem 8 months back!! now i'm freedom with no firewalls n stuff, we can enjoy full internet with no threat in just LINUXXXXXX!!!

:guitar:

---

