---
title: "Firewalls for Ubuntu"
date: 2010-05-08
forum: General Help
---

### Post by 0919005 on 2010-05-08
Hiii all
How are you ??
I hope to be fine 
What is Firewalls for Ubuntu ??
 
How I can install it ??
 
:):)

---

### Post by j7%&lt;RmUg on 2010-05-08
Im not quite sure what you mean, ubuntu comes with a firewall enabled by default.

---

### Post by 3rdalbum on 2010-05-08
Is your computer hooked up to a broadband router? If so, your router has a firewall already and your computer doesn't need one at all.

Have you installed any software that actually listens for **incoming*** connections (such as the Apache web server, Samba file server, or Remote Desktop) and you DON'T want anyone across the internet to be able to connect to those services? If so, then install the "gufw" package, and go to System > Administration > Firewall Configuration and tell it to enable the firewall and block all services.

*Firefox is an example of a program that starts an outgoing connection; merely running a web browser and a torrent client does NOT require you to have a firewall.

---

### Post by dino99 on 2010-05-08
install with synaptic and activate gufw, see also "secured IP" below

---

### Post by john newbuntu on 2010-05-08
Well, Ubuntu comes with a firewall called "ufw".  But I am not sure if it is enabled by default.  You can check the status using the following command in a terminal (Applications->accessories->terminal)
```
sudo ufw status
```Please install a handy GUI for this using the command "sudo apt-get install gufw".  Then open up gufw (System->admin->firewall config) and set/unset status.

(Sorry was a bit late in posting this- did'nt mean to step on dino or 3rd albums suggestions)

---

### Post by 0919005 on 2010-05-08
I mean what is another firewalls for save the system  ??
:grin:
like in windows we have Casper & Norton antivirus   
And how i can install it ??

---

### Post by P4man on 2010-05-08
Short answer: you really dont need it. Not a firewall and definitely not an antivirus (unless you want to scan your windows partition or files for windows virusses)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by 0919005 on 2010-05-08
I feel good when I have new firewall ;)

becuse the hackers do not care about name of your system they just broken your computer . :(

---

### Post by P4man on 2010-05-08
A firewall closes ports. if you are not running any server software like apache, then unlike on windows, on ubuntu there are no ports to be closed (actually, there is no software listening on those ports). If you are running such software, you probably want those ports open anyway, or that software wont work. It may make you feel good, but its really no help (unless you want to allow local PCs and not internet PCs to access those services, but in that case a firewall on your router is a lot easier to setup).

Dont let that stop you to install a firewall, but its probably rather pointless.

---

### Post by michael_schmid on 2010-05-08
Look,

what my fellow posters tried to explain was that ubuntu (and indeed every single linux distribution I know of) comes with a "built-in" firewall called iptables that by default is configured to


[LIST=1]
[*]Block any access from the outside world
[*]Allow all access from your local host to the outside world
[/LIST]
The windows applications that you referred to are nothing more than so called "Personal Firewalls" that might make you feel better, but are pretty useless nowadays as even the windows firewall does a good job if you have a system >= Windows Vista. If you'd like to allow partial access to your system (or restrict some outgoing connections) you can install one of the OSS applications that were already mentioned. If you wan't to go command-line only I'd suggest Shorewall ([http://www.shorewall.net/](http://www.shorewall.net/)) which hides all the complicated iptables stuff under some well-documented configuration files.

---

### Post by 3rdalbum on 2010-05-08
> **0919005 said:**
> I mean what is another firewalls for save the system  ??
:grin:
like in windows we have Casper & Norton antivirus   
And how i can install it ??

Norton Antivirus stops viruses. Viruses are malicious computer programs that get into your computer and run.

Viruses do not work on Ubuntu, so you don't need an antivirus program.

I'm sure it makes you feel safer to be using an antivirus and a firewall, but you really don't need them. If you don't have anything wrong with you, you don't take antibiotics.

---

### Post by 0919005 on 2010-05-08
Can Ubuntu be hack by local PC or not ??
:biggrin:

---

### Post by P4man on 2010-05-08
If you dont have any server services running (apache, ssh, file sharing,..), then no, I dont see how.

---

### Post by 0919005 on 2010-05-08
> **3rdalbum said:**
> Norton Antivirus stops viruses. Viruses are malicious computer programs that get into your computer and run.
 
Viruses do not work on Ubuntu, so you don't need an antivirus program.
 
I'm sure it makes you feel safer to be using an antivirus and a firewall, but you really don't need them. If you don't have anything wrong with you, you don't take antibiotics.
 
I know WINE emulate winodws program can wine emulate viruses byitself?
:p

---

### Post by 3rdalbum on 2010-05-08
> **0919005 said:**
> Can Ubuntu be hack by local PC or not ??
:biggrin:

Unless Ubuntu is listening to incoming ports (which it DOES NOT do by default), then there's no way an attacker can do anything with your computer.

Even if you install a service like the Apache web server, as long as you keep it up-to-date with Update Manager you should not have a problem.

---

### Post by P4man on 2010-05-08
> **0919005 said:**
> I know WINE emulate winodws program can wine emulate viruses byitself?
:p

If you had bothered to read the links given to you, you would have known the answer already. Yes, some windows viruses work on wine. If you intend to run wine and windows apps that might be infected, by all means install an antivirus. That doesnt mean a worm can infect your system though.

---

### Post by 3rdalbum on 2010-05-08
> **0919005 said:**
> I know WINE emulate winodws program can wine emulate viruses byitself?
:p

Wine is just a program. It only runs if you run it. It's not a sentient being, it doesn't run itself and it doesn't get run at startup. Even if it did, there's no reason for it to run some random file, and there's no way for the Windows virus to convince Wine to run it; if the virus could do that, then it would already be running and it wouldn't need Wine.

Please, just trust our system :-)

Ubuntu, and even Wine, have been designed by people with much more security knowledge than both of us put together.

---

### Post by P4man on 2010-05-08
> **3rdalbum said:**
> Wine is just a program. It only runs if you run it. It's not a sentient being, it doesn't run itself and it doesn't get run at startup. Even if it did, there's no reason for it to run some random file, and there's no way for the Windows virus to convince Wine to run it; if the virus could do that, then it would already be running and it wouldn't need Wine..

Thats true, but if you have an infected windows executable and you run it with wine, the virus may run as well. It would likely not be able to do a lot of damage, but its at least a possibility.

---

### Post by 0919005 on 2010-05-18
you have the new information for me 

Thanks for All
:)

---

