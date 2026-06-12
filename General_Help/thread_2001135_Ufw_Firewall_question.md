---
title: "Ufw Firewall question"
date: 2012-06-10
forum: General Help
---

### Post by portage on 2012-06-10
So I was reading the forums today and I saw that Ubuntu's firewall wasn't enabled. I enabled it but my question is do I actually need to create rules? If i open the firewall configuration I need to unlock it and when i do it says enabled. The incoming is denied and outcoming is allowed. 

1. Do I actually need to create rules or are all incoming denied even without rules?
2. When I restart my computer, if I don't click "Unlock", is the firewall disabled?

I read the Ufw wiki but I don't really understand any of it :confused:

Thanks.

---

### Post by Paqman on 2012-06-10
You only need to enable it if you're doing something that would put you at risk (ie: install a service that connects to the outside world). The default configuration for Ubuntu is to have no services listening on any ports, which is just as safe as having a firewall shut all the ports. That's why it's not enabled by default; it doesn't need to be.

So unless you've installed some kind of server or service that accepting connections from the internet you don't need to do anything.

---

### Post by portage on 2012-06-10
Oh, so I only use Firefox to download and watch videos, and download software from the software center. I don't need the firewall?

---

### Post by Paqman on 2012-06-10
Nope.

---

### Post by hottarod on 2012-06-10
I find it amazing that Microsoft still doesn't get this.    I guess it creates a great aftermarket software industry for some people though.

---

### Post by portage on 2012-06-10
thanks for the help.

---

### Post by haqking on 2012-06-10
> **Paqman said:**
> You only need to enable it if you're doing something that would put you at risk (ie: install a service that connects to the outside world). The default configuration for Ubuntu is to have no services listening on any ports, which is just as safe as having a firewall shut all the ports. That's why it's not enabled by default; it doesn't need to be.

So unless you've installed some kind of server or service that accepting connections from the internet you don't need to do anything.

Ever heard of a reverse connection ? ;-)

Firewalls are not about only controlling inbound traffic but also outbound.

To the OP it is a good idea to control your outbound traffic, also just because a service is not listening on a port, remote code execution can be exploited to create listening services on arbitrary ports.

Read here for a good guide on Ubuntu and Firewalls 

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Peace

---

### Post by VE6EFR on 2012-06-10
> **hottarod said:**
> I find it amazing that Microsoft still doesn't get this.    I guess it creates a great aftermarket software industry for some people though.

It does seem that way, doesn't it?

---

### Post by Paqman on 2012-06-10
> **haqking said:**
> remote code execution can be exploited to create listening services on arbitrary ports.


True, but if you've got malicious code executing on your machine then all security bets are off anyway (including ufw/iptables rules).

I agree that adding a firewall can make your system more secure. But that doesn't mean that the default setup is insecure to the point that it requires immediate remedial action. Many computer users have inherited a security mindset intended to deal with Windows pre XP SP2 where the situation was pretty awful. I had a freshly installed XP machine compromised by multiple nasties in the time it took to download a firewall and AV suite. People still assume that a machine is critically vulnerable until they get a firewall and AV running, which I suspect might have been where the OP was coming from.

---

### Post by portage on 2012-06-10
> **Paqman said:**
> People still assume that a machine is critically vulnerable until they get a firewall and AV running, which I suspect might have been where the OP was coming from.

Well I did come from Windows 7. I always used an AV and firewall and people kept telling me without it my computer would be infected easily. But it seems I don't need it here since I only browse, and download from software center.

---

### Post by haqking on 2012-06-11
> **portage said:**
> Well I did come from Windows 7. I always used an AV and firewall and people kept telling me without it my computer would be infected easily. But it seems I don't need it here since I only browse, and download from software center.

the best AV is you !

Education and intelligent browsing and file sharing is the best proactive measure.

AV is reactive.

AV also is really only beneficial for file sharing with windows as there are currently no wild viruses for Linux and if there was then the current solutions would not detect them anyways.

However there are many other steps to take to help in securing your machine, Linux is no more secure than windows.

Read the basic security wiki here for assistance on things like apparmor, NOScript etc. [URL="https://wiki.ubuntu.com/BasicSecurity"]Ubuntu Basic Security WIki
[/URL]
Also you say you are only *browsing*, about 80% of attack vectors these days are web based/browser based so browsing is your most likely entry point for malicious attackers.

---

### Post by haqking on 2012-06-11
> **Paqman said:**
> True, but if you've got malicious code executing on your machine then all security bets are off anyway (including ufw/iptables rules).

I** agree that adding a firewall can make your system more secure. But that doesn't mean that the default setup is insecure to the point that it requires immediate remedial action.** Many computer users have inherited a security mindset intended to deal with Windows pre XP SP2 where the situation was pretty awful. I had a freshly installed XP machine compromised by multiple nasties in the time it took to download a firewall and AV suite. People still assume that a machine is critically vulnerable until they get a firewall and AV running, which I suspect might have been where the OP was coming from.


Well i never said that it was *insecure*, however i will say it is no more secure than Windows, in either they can still get compromised and not just through remote code execution.

I wont enter the linux vs windows futile argument again here as its been done to death.

I totally agree with the mindset that people have about needing x,y,and z and then they are secure which is an unfortunate model of thinking, **security is a process and not a product**.

Not taking proactive measures to secure your machine regardless of the OS however is exactly why systems still get compromised so easily.


To the OP in my opinion as a security professional and long time Linux user and Windows user, then you should take steps to educate yourself about security, dont fall into the category of Linux users who think that Linux is more secure blah blah waffle that you often hear.

Maintain strict firewall rules both inbound and outbound (regardless of whether you have services "listening" or not.

Run some AV if you file share with windows or use Wine.

Look at Apparmor or SELinux.

Safe browsing habits, including things such as NOScript.

etc etc, read the basic security link i posted above along with the places it links too.

Peace

---

### Post by Paqman on 2012-06-14
> **haqking said:**
> 
I totally agree with the mindset that people have about needing x,y,and z and then they are secure which is an unfortunate model of thinking, **security is a process and not a product**.


Yeah, unfortunately that's a pretty entrenched attitude. To be fair, older versions of Windows really did need stuff bolted on, as security hadn't really been addressed effectively in the design of the OS. Will be interesting to see how long that idea persists. I suspect it'll stick around as long as Windows does.

---

