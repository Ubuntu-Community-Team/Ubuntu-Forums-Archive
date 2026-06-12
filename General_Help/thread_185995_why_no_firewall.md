---
title: "why no firewall?"
date: 2006-06-01
forum: General Help
---

### Post by waldorf on 2006-06-01
I'm just curious why ubuntu does not come with a firewall.

I don't have an opinion on the matter, but I'm curious what the community thinks.

---

### Post by Ramses de Norre on 2006-06-01
Not every package can be installed by default.. machines not connected to the net wont need a firewall.
If you do need one install firestarter (or another one), which is very easy.

---

### Post by skymt on 2006-06-01
The Ubuntu policy is to have as few ports as possible open by default, making a firewall redundant. You can install Firestarter, but there's really no reason to unless you (a) run servers and (b) aren't behind a trusted NAT router.

If you use Apache or the like for testing web sites, you should configure them to bind to localhost. Ditto for personal mail servers.

---

### Post by Almighty on 2006-06-01
On my Dapper laptop I have 4 ports open...

one for printing
two for VNC
one for X11

---

### Post by 5-HT on 2006-06-01
Just guessing here, but perhaps one reason that Ubuntu does not ship with a restrictive firewall set up is to avoid cases of having it block wanted connections. If there was a restrictive firewall set up by default, that may lead to unhappy/frustrated/confused users.

Additionally, as there are no world-listening daemons running from a standard install, a really pressing need for a firewall really only comes into play when a user installs any such service.

If someone installs something that is world-listening, they should already know how to take appropriate security precautions.

If one would like a firewall, there are many options easily available.

HTH

---

### Post by steve.horsley on 2006-06-01
The default install doesn't need one because it doesn't have any open ports (except the DHCP client). If and when you install any network services, you may want to install a firewall too.

Edit:
5-HT said it better.

---

### Post by jonibo on 2006-06-01
Actually, the Linux kernel has firewall functionality built in.  What you do not have installed is a tool to configure the firewall... but the Ubuntu defaults are sane (no open ports), so you do not have to worry about changing the configuration, hence no configuration tool needed!

---

### Post by garyng on 2006-06-01
I would say it is a mistake of not including a basic firewall package(and a restricted rule set by default). Windows used to do the same but I believe in SP2, it becomes the default and warn you if it is disabled.

---

### Post by FrancoNero on 2006-06-01
firestarter is pretty easy and you can installit via the package installer. if you really need a firewall then i can recommend it

---

### Post by jonibo on 2006-06-01
The Linux kernel IS a firewall, and the Ubuntu "firewall rule set" IS restricted by default.

---

### Post by garyng on 2006-06-01
[QUOTE=jonibo]The Linux kernel IS a firewall, and the Ubuntu "firewall rule set" IS restricted by default.[/QUOTE]

the kernel only has the necessary modules to activate firewall rules. As for restricted, it must be I installed it through debootstrap rather booting the DVD then as my "iptables -L" shows that it allows everything.

---

### Post by jonibo on 2006-06-01
A moot point if you have no open ports anyway...!

---

### Post by garyng on 2006-06-01
[QUOTE=jonibo]A moot point if you have no open ports anyway...![/QUOTE]

If you don't have open port, how are you going to say share local directories through SMB for other workstations ? Or activate remote desktop ?

---

### Post by thasheep on 2006-06-01
Ubuntu does come with a really powerful (albiet unfriendly) firewall called iptables. Unfortunately (imo), this filewall is set to accept everything. If you know how to use it, open a terminal and do so (eg to block incoming tcp connections on port 445, do 'sudo iptables -A INPUT -p tcp --dport 445 -j DROP'). If you have no idea what that means, type iptables into google or install firestarter. I've never used it, but I believe firestarter is a graphical frontend to iptables.

---

### Post by az on 2006-06-01
[QUOTE=garyng]I would say it is a mistake of not including a basic firewall package(and a restricted rule set by default). Windows used to do the same but I believe in SP2, it becomes the default and warn you if it is disabled.[/QUOTE]
The only reason you need a firewall on a windows desktop is because you have no control (or knowledge) of what can talk to the outside world.  This is not so with a default ubuntu install.


In ubuntu, if you install a service which listens, and then you install a firewall, you are going to have to punch a hole in your firewall anyway.  If you only are listening on that port, what's the point?

---

### Post by darkhatter on 2006-06-01
there is a firewall its built into the kernel and its called iptables2 I believe. you don't need to worry about it. its all set up.

---

### Post by mk1970 on 2006-06-02
[QUOTE=waldorf]I'm just curious why ubuntu does not come with a firewall.
[/QUOTE]

As many have already said, you already have the firewall active in your kernel but it's allowing everything by default. Personally I like the text-based configuration files so I advertise little bit my own rule set: [http://users.piuha.net/martti/comp/ubuntu/firewall]("http://users.piuha.net/martti/comp/ubuntu/firewall")

See  [http://users.piuha.net/martti/comp/ubuntu/install.html#10]("http://users.piuha.net/martti/comp/ubuntu/install.html#10") how to activate these rules after every reboot.

---

### Post by frodon on 2006-06-02
Just to bring insight on what is the ubuntu firewall :
Ubuntu and all 2.4.X and 2.6.X kernel series have an embedded firewall called netfilter : [http://www.netfilter.org/](http://www.netfilter.org/)
The popular langage to configure this firewall is iptables and firestarter is a popular frontend for iptables.

So to configure a firewall install firestarter if you don't want to bother with iptables rules and if you want a better firewall write your own iptables rules.

If you want to check that the default policy allow all, run this command : ```
sudo iptables -L
```It will list the iptables rules, the 3 default chains are INPUT/OUTPUT/FORWARD and by default these 3 chains are in the ACCEPT state.

---

### Post by RAOF on 2006-06-02
[QUOTE=waldorf]I'm just curious why ubuntu does not come with a firewall.[/QUOTE]
It's a trade-off between security & user-friendlyness.  Ubuntu doesn't ship with any internet-listening services by default, so the only things that a firewall would do is block outgoing connections - which you'd need to disable on a per-port basis whenever you wanted something new to talk to the internet.

Since you generally trust the software on your system (if you install stuff from the repositories), this is annoying for very little security gain.

---

### Post by Kray on 2006-06-02
I suppose it would be nice (for paranoid persons at least ;-)) to include some user-friendly firewall in repositories. Sadly, AFAIK such firewall does not exist (nah, Firestarter does not count) for Linux. I'm not even sure if this is possible - from what I've read iptables can filter by process id only outgoing (not incoming) traffic. 

Second issue is that such firewall should be configurable by generic user, not neccessary someone with root permisions.

---

### Post by thasheep on 2006-06-02
[QUOTE=Kray]Second issue is that such firewall should be configurable by generic user, not neccessary someone with root permisions.[/QUOTE]In my opinion, that would be an unforgivable security hole. If you really (and I mean REALLY) want to set it up yourself, you can edit /etc/sudoers to that effect.

---

### Post by frodon on 2006-06-02
[QUOTE=Kray]I suppose it would be nice (for paranoid persons at least ;-)) to include some user-friendly firewall in repositories. Sadly, AFAIK such firewall does not exist (nah, Firestarter does not count) for Linux. I'm not even sure if this is possible - from what I've read iptables can filter by process id only outgoing (not incoming) traffic. 

Second issue is that such firewall should be configurable by generic user, not neccessary someone with root permisions.[/QUOTE]
You miss the point about iptables i think, once again the firewall is netfilter and iptables a langage to configure it.
Iptables rules allow you to filter incoming/outcoing packets with id/tag/ip/... filtering, you can configure you computer as a proxy through iptables, you can also forward the traffic with or without filtering, .... so you're really able to do what you want with iptables and netfilter which are far better than any windows firewall in my opinion because it's included in the kernel and therefore handled at the beginning of the chain.
So really i don't see why you don't want to concider firestarter as a user-friendly firewall solution for linux.

---

### Post by Kray on 2006-06-02
Bleh, I edited this message so long that cookie expires and save dind't work :/

[thaspeep]

Why? There are global rules contributed by administrators and per-user rules, like allow this app to connect to IP from x to y on port z. Global rules can't be overriden by Joe Simple User so what's the problem...

[frodon]

You of course are right about netfilter/iptables relations ;-)

I'm apparently aware that netfilter is much more powerful that built-in Windows firewall. Which can be fortunately disabled, and this is first thing I would do after installing Windows today. I used to use Outpost Firewall, still got subscriptions for my parent...

The difference is between configuring firewall by user. In Outpost Firewall case (or ZoneAlarm, Kerio...) when app tried to connect to Internet popup is raised where user can allow/disallow network activity for this app. Advanced user can add additional rules using various restrictions (ip's, ports, protocols). All this is easy clickable and user friendly.

Now, in Firestarter things are more complicated and much more heavy. There is no such thing like popup notification when some app are connecting and no valid rule is found - you can only globally allow or disallow such connections (IIRC you can view blocked connection via GUI and unblock such connections if you want). Besides all, as I wrote before netfilter can't block incoming connections using per app rules, e.g. disallow all incoming connection to ports opened by MyApp.exe. IIRC outgoing traffic can be filtered if kernel is properly compiled. Summaring, contributing own rules to firewall isn't just easy as in case of Windows firewalls.

One more - yes, Firerstarter is most friendly GUI to Linux firewall I've found. It just that Windows firewalls are much more user friendly IMO. Of course 'no open ports' policy makes this topic less important, but ya know, there are paranoid ppl here :s

---

### Post by asimon on 2006-06-02
[QUOTE=azz]In ubuntu, if you install a service which listens, and then you install a firewall, you are going to have to punch a hole in your firewall anyway.  If you only are listening on that port, what's the point?[/QUOTE]
Exactly, a firewall makes sense if you want to restrict the service to only listen to some specific systems or something like that and the service itself can't be configured in this regard.

---

### Post by frodon on 2006-06-02
[QUOTE=Kray]Now, in Firestarter things are more complicated and much more heavy. There is no such thing like popup notification when some app are connecting and no valid rule is found - you can only globally allow or disallow such connections (IIRC you can view blocked connection via GUI and unblock such connections if you want). Besides all, as I wrote before netfilter can't block incoming connections using per app rules, e.g. disallow all incoming connection to ports opened by MyApp.exe. IIRC outgoing traffic can be filtered if kernel is properly compiled. Summaring, contributing own rules to firewall isn't just easy as in case of Windows firewalls.

One more - yes, Firerstarter is most friendly GUI to Linux firewall I've found. It just that Windows firewalls are much more user friendly IMO. Of course 'no open ports' policy makes this topic less important, but ya know, there are paranoid ppl here :s[/QUOTE]ha ok, i get your point :), you mean pop-up warnings/configuration by user-friendly, indeed firestarter is not at this level of user-friendlyness.
But i know it's possible because the mandriva default firewall GUI use this principle (the same than windows), so with some luck it will be available for other distros in the furure.
Anyway for my personnal needs i will always use a custom iptables script.

---

### Post by Kray on 2006-06-02
Interesting, I didn't know about Mandriva. I was assuming that this is possible, at least partially, still haven't seen working implementation. Thx for info, I think I will go now and check if there is Mandrive Live CD ;-)

---

### Post by frodon on 2006-06-02
Here is the link if you want to learn more on the topic : [http://qa.mandriva.com/twiki/bin/view/Main/InteractiveFirewall](http://qa.mandriva.com/twiki/bin/view/Main/InteractiveFirewall)

---

### Post by FredB on 2006-06-02
I have no problem with the built in firewall for ubuntu. Shieldsup ([http://grc.com/](http://grc.com/)) tells me it is ok.

PCFlank too... So, why bothering ? ;)

---

### Post by waldorf on 2006-06-02
Wow. I didn't realize I was raising such an involved issue.

For what its worth, given the discussion and my lack of knowledge on the whole matter and my rather basic needs for browsing, podcasts, email, and IM I think I will leave well enough alone and not install Firestarter or any other GUI and not mess around with any preconfigured settings.

Thanks for the enlightening discussion. Ubuntuforums are GREAT!

---

### Post by anthro398 on 2006-06-02
[QUOTE=azz]The only reason you need a firewall on a windows desktop is because you have no control (or knowledge) of what can talk to the outside world.  This is not so with a default ubuntu install.[/QUOTE]

True, but not very.  Lots of people will unknowingly install a listening service thus exposing themselves.  Either way, a port that responds as closed is not as a good as a port that doesn't respond at all.  

[QUOTE=azz]In ubuntu, if you install a service which listens, and then you install a firewall, you are going to have to punch a hole in your firewall anyway.  If you only are listening on that port, what's the point?[/QUOTE]

Two arguments there.  First, many poeple have no idea what a listening service is.  Protecting the ignorant from themselves is pretty important, isn't it?  That's the philosophy of OpenBSD, the most secure operating system in the world, anyway.  Second, using iptables, you don't have to just "punch a hole in your firewall" for everyone.  You can specify ip addresses or ranges.  So, although I can connect to ssh on my home machine from work, your packets will all be dropped as though my machine doesn't exist.  That's pretty powerful stuff.  It isn't as if remote vulnerabilities in applications like OpenSSH, vnc, and such aren't uncommon.  

Instead of leaving users to fend for themselves, I'd like to see Ubuntu use iptables with a default setting of allowing all outgoing traffic and all incoming traffic of state related.  That way, every normal use works and, in the case of using a listening service, one would have to edit default.  Even a simple gui menu option to turn the default firewall on/off would make it very easy for users.  

That's my two cents.

---

### Post by garyng on 2006-06-02
[QUOTE=anthro398]
Instead of leaving users to fend for themselves, I'd like to see Ubuntu use iptables with a default setting of allowing all outgoing traffic and all incoming traffic of state related.  That way, every normal use works and, in the case of using a listening service, one would have to edit default.  Even a simple gui menu option to turn the default firewall on/off would make it very easy for users.  

[/QUOTE]

That is basically my opinion too and what XP does now in SP2(which reverts their previous stand exactly of "you don't need firewall as you would need to poke a hole anyway").

---

### Post by Fred Doolie on 2006-06-02
I just went to Shields Up
[http://www.google.com/search?hl=en&q=test+firewall&btnG=Google+Search](http://www.google.com/search?hl=en&q=test+firewall&btnG=Google+Search)
Third one down

and ran the scans. The reports on my brand-new out-of-the-box Ubuntu 6.06 are the same as my Winblows system running either Mcaffee or Zone Alarm on full protection mode. NOTHING is visible except my IP address and the ping test.
Functionally, Ubuntu kinda has a firewall it seems.

*** Assumptions *** PLEASE correct me if I'm wrong
99.9% of the hackers out there are after Winslows systems; their automagic hacking software can't handle Linux.

If there were any security holes in Ubuntu (or Linux in general) the community would find them and release a patch within 48 hours.
 



 .

---

### Post by garyng on 2006-06-02
[QUOTE=Fred Doolie]I just went to Shields Up
[http://www.google.com/search?hl=en&q=test+firewall&btnG=Google+Search](http://www.google.com/search?hl=en&q=test+firewall&btnG=Google+Search)
Third one down

and ran the scans. The reports on my brand-new out-of-the-box Ubuntu 6.06 are the same as my Winblows system running either Mcaffee or Zone Alarm on full protection mode. NOTHING is visible except my IP address and the ping test.
Functionally, Ubuntu kinda has a firewall it seems.

*** Assumptions *** PLEASE correct me if I'm wrong
99.9% of the hackers out there are after Winslows systems; their automagic hacking software can't handle Linux.

If there were any security holes in Ubuntu (or Linux in general) the community would find them and release a patch within 48 hours.
 



 .[/QUOTE]


No it is very different. Functionally, ubuntu come naked by default. Yes, it is firewall "ready" but letting everyone in, should you start say a file/printer sharing feature.

---

### Post by thasheep on 2006-06-02
The reason the port scan finds nothing is because nothing is "listening" to those ports. Basically that means you're not running a web, email, ssh, printing server or something of the sort. This however doesn't mean the firewall is blocking anything (and as per default, it blocks nothing).

As for your assumption about hackers only being after windows, that isn't true. Viruses target windows because they can and because they can target far more people. However for hacking attempts, linux systems are targeted plenty. For instance, I run an ssh server (allows people to log in remotely) and get hundreds of (failed) attempts to hack in each day. This isn't really a problem because I've limited the server to only accept connections for two specific accounts and only authorised with a dsa key. In short, these hackers have a better chance of winning the lottery every week for six months. If it were set up to accept passwords alone, this could be a significant problem
Security holes in linux programmes are usually minor and picked up before anyone takes advantage of them (unlike windows ones). But, no amount of patching will stop someone from creating their own security problems by the way they configure their system.

---

### Post by hanzomon4 on 2006-06-03
I found this script that will setup iptables for regular desktop users
> Below is a firewall script for desktop computers. If you don't run any server of any kind and only intend to use the internet for desktop use e.g. surfing and e-mailing this is for you. 
[iptables script]("http://wiki.debianhelp.org/pmwiki.php/DebianHelpPages/FirewallForDesktopComputers")

---

### Post by angkor on 2006-06-03
[QUOTE=thasheep]If it were set up to accept passwords alone, this could be a significant problem[/QUOTE]

Would it? How long would a brute force attack take to calculate my let's say 13 character password...caps, numbers, special characters included? These ssh sweeps are nothing to worry about if you have strong passwords.

If a cracker decides to hit your box and take his time, it's another story. Of course your method is safer. But I prefer to be able to log into my box from anywhere if I want to.

---

### Post by frodon on 2006-06-03
[QUOTE=hanzomon4]I found this script that will setup iptables for regular desktop users

[iptables script]("http://wiki.debianhelp.org/pmwiki.php/DebianHelpPages/FirewallForDesktopComputers")[/QUOTE]It's quite easy to write his own iptables script, which is for sure the most secure firewall because it allows only the connection you needs.
If you wish to learn my guide will help you : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by Phreaker on 2006-06-03
The best way to setup a firewall is to use iptables.
Just read a couple of manuals ...and you learn new things ,too

---

### Post by thasheep on 2006-06-03
[QUOTE=angkor]Would it? How long would a brute force attack take to calculate my let's say 13 character password...caps, numbers, special characters included? These ssh sweeps are nothing to worry about if you have strong passwords.

If a cracker decides to hit your box and take his time, it's another story. Of course your method is safer. But I prefer to be able to log into my box from anywhere if I want to.[/QUOTE]
Well it's obviously up to you but someone only needs to log in once to screw you over. If I have the slightest intention of logging in remotely, I'll take a usb disk containing my key. To get some idea of how frequent these attempts are, enter 'grep ssh /var/log/auth.log' on the command line. It'll show the date and time of each attempt in the last couple of days. To see the older logs, grep auth.log.0 or zgrep auth.log.?.gz. It scared me....

---

### Post by garyng on 2006-06-03
[QUOTE=angkor]Would it? How long would a brute force attack take to calculate my let's say 13 character password...caps, numbers, special characters included? These ssh sweeps are nothing to worry about if you have strong passwords.

If a cracker decides to hit your box and take his time, it's another story. Of course your method is safer. But I prefer to be able to log into my box from anywhere if I want to.[/QUOTE]

except that most people(and I very much believe the targeted audience of ubuntu, which is quite similar to windows') use easy to guess password which is subjected to dictionary attacks.

---

### Post by thasheep on 2006-06-03
[QUOTE=Phreaker]The best way to setup a firewall is to use iptables.
Just read a couple of manuals ...and you learn new things ,too[/QUOTE]
I agree and that's what I do. However, you need to make sure you really understand what you're doing otherwise you could end up with either a false sense of security or you could prevent yourself from accessing the web, email, instant messaging and making you running servers (if any) useless. As with all firewalls, it's important that you check everything you want to use works and also get someone to do a port scan (eg [http://www.dslreports.com/scan](http://www.dslreports.com/scan)).

---

### Post by hanzomon4 on 2006-06-03
[QUOTE=frodon]It's quite easy to write his own iptables script, which is for sure the most secure firewall because it allows only the connection you needs.
If you wish to learn my guide will help you : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)[/QUOTE]

Will do ;)

---

### Post by az on 2006-06-03
[QUOTE=anthro398]True, but not very.  Lots of people will unknowingly install a listening service thus exposing themselves.   [/QUOTE]

On a default install, you are secure.  If you use the repositories to install your software, I think it's highly unlikely that you will install some malevolent "backdoor" software.

[QUOTE=anthro398]
Either way, a port that responds as closed is not as a good as a port that doesn't respond at all.  [/QUOTE]
I dissagree with that.  It's not like that is going to conceal my presence in any practical way.  The moment I browse the web, the webservers I query know I'm there.

[QUOTE=anthro398]
...
You can specify ip addresses or ranges.  So, although I can connect to ssh on my home machine from work, your packets will all be dropped as though my machine doesn't exist.  That's pretty powerful stuff.  It isn't as if remote vulnerabilities in applications like OpenSSH, vnc, and such aren't uncommon.  [/QUOTE]

That is something the user must learn about when they install such software.  It isn't needed out-of-the-box.

[QUOTE=anthro398]
Instead of leaving users to fend for themselves, I'd like to see Ubuntu use iptables with a default setting of allowing all outgoing traffic and all incoming traffic of state related.  That way, every normal use works and, in the case of using a listening service, one would have to edit default.  Even a simple gui menu option to turn the default firewall on/off would make it very easy for users.  
[/QUOTE]

Elagant solutions should be there for the problems when they exist.  By default, they are not there.  If you install vnc or ssh, you should know about the vulnerabilities you are exposing yourself to.  You could probably argue that it can be better documented...

---

### Post by hanzomon4 on 2006-06-04
How do you know which ports a particular service uses

Nevermind I found it /etc/services

---

### Post by thasheep on 2006-06-04
[QUOTE=hanzomon4]How do you know which ports a particular service uses[/QUOTE]
/etc/services states the standard ports used by various services (you don't need to be running them but this is the standard). This file is used by iptables if you specify a name of a service instead of a port. Eg the following are equivalent. They both close port 22 for tcp connections (normally ssh)```
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -j REJECT
sudo iptables -A INPUT -i eth0 -p tcp --dport ssh -j REJECT
```
Many services can be configured to run on non-standard ports. For an ssh server, the configuration file is /etc/ssh/sshd_config. If you set it to run on another port (can be useful to prevent attacks), then people connecting will need to know this and run the ssh client with the "-D port" option.

---

### Post by hanzomon4 on 2006-06-04
[QUOTE=frodon]It's quite easy to write his own iptables script, which is for sure the most secure firewall because it allows only the connection you needs.
If you wish to learn my guide will help you : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)[/QUOTE]

Okay I followed your guide run the stealth test and my ports show up as blocked, But 
When I stop the firewall my ports still show up as blocked.

So do I have two firewalls or something?

---

### Post by hanzomon4 on 2006-06-04
How do I stealth icmp, it shows up as open

---

### Post by jonrkc on 2006-06-04
I will not connect to the Internet without a firewall in place.  I have happily used Guarddog to configure my iptables for me for about three years.  I installed it in my Dapper setup and set my allowed and blocked services and got a perfect stealth score with grc.com's Shields Up test, just as I did when running Hoary.  Prior to that, ports showed as closed but not stealthed.  

Just my preference.  I do not subscribe to the belief that Linux is almost invulnerable.  I feel much safer if I put a reasonable number of safeguards in place in addition to what comes out-of-the-package.

I tried Firestarter and could not see how to use it right.  Guarddog is very simple to use.

---

### Post by frodon on 2006-06-05
[QUOTE=hanzomon4]Okay I followed your guide run the stealth test and my ports show up as blocked, But 
When I stop the firewall my ports still show up as blocked.

So do I have two firewalls or something?[/QUOTE]How did you stop the firewall ?
running the "sudo /etc/init.d/firewall stop" command ?

You shouldn't have any ports seen as blocked after stoping the firewall because the flush script given in my guide delete all the iptables rules.
You can use the forum thread related to my guide if you need support.
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by hanzomon4 on 2006-06-05
Yeah I used that command 
In another thread someone said that my router could be the reason that my ports show up as blocked

---

### Post by frodon on 2006-06-05
Indeed it could be the reason, in addition if you have a router you don't really need a software firewall because you router already do that for you, so if was you i would just well configure my router and not run a software firewall.

---

### Post by Fred Doolie on 2006-06-07
[QUOTE=hanzomon4]Okay I followed your guide run the stealth test and my ports show up as blocked, But 
When I stop the firewall my ports still show up as blocked.

So do I have two firewalls or something?[/QUOTE]

I ran that test with nothing installed or configured and all ports show up as blocked.
Maybe Dapper is already firewalled?

---

### Post by az on 2006-06-07
[QUOTE=Fred Doolie]I ran that test with nothing installed or configured and all ports show up as blocked.
Maybe Dapper is already firewalled?[/QUOTE]
Nothing is listening.  That's the default.  Except in Windows.

---

### Post by Chris03 on 2006-06-07
System -> Admin -> Network Tools -> Port Scan

Go to a site like [ipchick]("http://www.ipchick.com/") to get your IP address and test!

If none are listening, a firewall isn't needed. Only service I've ever seen is the CUPS printer driver, and it doesn't listen to the outside, only to your own connection.

---

### Post by jonrkc on 2006-06-08
[QUOTE=hanzomon4]Okay I followed your guide run the stealth test and my ports show up as blocked, But 
When I stop the firewall my ports still show up as blocked.

So do I have two firewalls or something?[/QUOTE]
In the release notes for Dapper 6.06, it says that 6.06 is released with default of no ports listening, so there's no need for a firewall.  I think this would account for the "all ports blocked" result.  (When I first used the live Dapper CD and hooked up (via pppoeconf, as the supplied graphic thing would not even let me type in it!), I ran the Shields Up test and got an all-blue result, meaning all ports closed.  Then I re-instated Guarddog with my known good settings, and the test showed up as perfectly stealthed (all green).

I just prefer to go one step further and make my computer supposedly invisible on the Internet.  With ports closed the security is not as great as when they're stealthed, according to grc.com--and I tend to trust Steve Gibson.  

It's up to each user, of course.  I just feel a lot better knowing I'm invisible rather than visible but hard to get into.

There is NO absolutely secure protection, though--short of unplugging your machine, which tends to limit its usefulness, though it does eliminate a lot of headaches, too. :)

---

### Post by RAOF on 2006-06-08
[QUOTE=jonrkc]...
It's up to each user, of course.  I just feel a lot better knowing I'm invisible rather than visible but hard to get into.
...[/QUOTE]
Without open ports, you're **impossible** to get into.  100% guaranteed.

I seem to remember a series of articles on [The Register](www.theregister.co.uk) about Steve Gibson.  Basically saying that he doesn't know as much about security as he thinks ;).  

Take this second-hand vague rememberance for what it's worth. :)

---

### Post by asimon on 2006-06-08
[QUOTE=jonrkc]I just prefer to go one step further and make my computer supposedly invisible on the Internet.  With ports closed the security is not as great as when they're stealthed, according to grc.com--and I tend to trust Steve Gibson.[/QUOTE]
You can't make your computer invisible short of disconnecting it from the net. Even if your default policy is deny and those firewall testers give you an "stealth" your computer is far from invisible.
Which is not to say that droping unwanted packages instead or rejecting them is a bad thing. It has advantages, but invisibility it's not.

---

### Post by jonrkc on 2006-06-08
[QUOTE=RAOF]Without open ports, you're **impossible** to get into.  100% guaranteed.

I seem to remember a series of articles on [The Register](www.theregister.co.uk) about Steve Gibson.  Basically saying that he doesn't know as much about security as he thinks ;).  

Take this second-hand vague rememberance for what it's worth. :)[/QUOTE]
I can't think of any well-known personality who doesn't have detractors...  :)  I believe I read the piece you're referring to that was in The Register.

I'm just inclined to trust somebody who is smart enough to write Spin-Write (which, now that it's available for Linux as well as That Unwarrentedly Popular Operating System, I intend to obtain when I have the $$).  

Besides, I'll bet Steve G. doesn't attract the animosity that Richard Stallman does!  But I am a Stallman fan, too.  So I'm just in a peculiar corner, I guess.  I'm glad there are enough corners for everybody to be relatively happy.

Maybe this security thing is kind of like seat belts: People have been killed because they WERE wearing their seatbelts; but also a lot of people have been saved by them.  I doubt that there are any unmixed blessings in the Real World--wherever that is....

---

### Post by jonrkc on 2006-06-08
[QUOTE=asimon]You can't make your computer invisible short of disconnecting it from the net. Even if your default policy is deny and those firewall testers give you an "stealth" your computer is far from invisible.
Which is not to say that droping unwanted packages instead or rejecting them is a bad thing. It has advantages, but invisibility it's not.[/QUOTE]
I was impressed by all ports being closed by default when I tested right after installing, without a firewall.  And I'm sure that as long as I have an IP address somebody somewhere can do something to my computer.  But I still feel I'm minimizing the risk more by being "stealthed" than just having ports closed.  If this is buying into a fantasy, it's no more than billions of people do in their daily lives....

I agree totally that disconnection is the only completely safe mode of operation.

---

### Post by mannheim on 2006-06-08
[QUOTE=azz]Nothing is listening.  That's the default.  Except in Windows.[/QUOTE]

Ah, that's not quite fair. It is the default in ubuntu. But I remember installing slackware a few years ago, and finding that the default install set up a live web server on port 80 and had sshd listening to the world on port 22.

---

### Post by az on 2006-06-08
[QUOTE=mannheim]Ah, that's not quite fair. It is the default in ubuntu. But I remember installing slackware a few years ago, and finding that the default install set up a live web server on port 80 and had sshd listening to the world on port 22.[/QUOTE]
You are right.

---

### Post by darkhatter on 2006-06-08
are they going to work on a new gui for the firewall in ubuntu 7.xx not sure what odd name this version is going to get

---

### Post by JGKC9AYC on 2006-06-11
[QUOTE=frodon]Indeed it could be the reason, in addition if you have a router you don't really need a software firewall because you router already do that for you, so if was you i would just well configure my router and not run a software firewall.[/QUOTE]

Got some tips on how to do that?  I'm using a D-Link DI-524.
I took a peek at the /etc/services file & needless to say I was totally lost by all that...i'd have no idea on where to start as far as customizing my iptables.  About all I do is web browsing, checking e-mail, & doing the bittorrent thing.

---

### Post by jonrkc on 2006-06-12
[QUOTE=JGKC9AYC]Got some tips on how to do that?  I'm using a D-Link DI-524.
I took a peek at the /etc/services file & needless to say I was totally lost by all that...i'd have no idea on where to start as far as customizing my iptables.  About all I do is web browsing, checking e-mail, & doing the bittorrent thing.[/QUOTE]
I bet if you start at: [http://www.dlink.com/products/support.asp?pid=316&sec=0](http://www.dlink.com/products/support.asp?pid=316&sec=0) you will be able to find the instructions for your version of the DI-524.  The hardware firewall in the router doesn't have anything to do with iptables, if I'm not mistaken.

---

### Post by JGKC9AYC on 2006-06-12
Anyone here heard of or tried running Peer Guardian in their iptable?

---

### Post by frodon on 2006-06-13
I met some persons there who run iptables scripts and PeerGuardian without any problems, so yes it's possible.

---

### Post by JGKC9AYC on 2006-06-14
[QUOTE=Chris03]System -> Admin -> Network Tools -> Port Scan

Go to a site like [ipchick]("http://www.ipchick.com/") to get your IP address and test!

If none are listening, a firewall isn't needed. Only service I've ever seen is the CUPS printer driver, and it doesn't listen to the outside, only to your own connection.[/QUOTE]

& how long does a port scan take?

---

### Post by jonrkc on 2006-06-14
[QUOTE=JGKC9AYC]& how long does a port scan take?[/QUOTE]
About two minutes on grc.com; I haven't tried others.

---

### Post by JGKC9AYC on 2006-06-14
[QUOTE=jonrkc]About two minutes on grc.com; I haven't tried others.[/QUOTE]

I did the "System -> Admin -> Network Tools -> Port Scan" thing & let it run for over an hour & it was still running when I checked it.

---

### Post by rdoyle on 2006-06-14
[QUOTE=RAOF]Without open ports, you're **impossible** to get into.  100% guaranteed.

I seem to remember a series of articles on [The Register](www.theregister.co.uk) about Steve Gibson.  Basically saying that he doesn't know as much about security as he thinks ;).  

Take this second-hand vague rememberance for what it's worth. :)[/QUOTE]
"Personal Firewalls" are mostly snake-oil at  [http://www.samspade.org/d/firewalls.html](http://www.samspade.org/d/firewalls.html)
makes the same point:

"So... what does a 'personal firewall' actually do? Well, effectively it listens on all the ports on your system. This provides no real additional security over turning off the services that you don't use."

---

### Post by jonrkc on 2006-06-14
[QUOTE=JGKC9AYC]I did the "System -> Admin -> Network Tools -> Port Scan" thing & let it run for over an hour & it was still running when I checked it.[/QUOTE]
I go to the "Shields Up!" section and run the function that tests all 1,000+ of common ports, and it takes about two minutes at most, often less....  I get a "Perfect Stealth" rating and though there will always be disagreement about the importance of a firewall, I stubbornly maintain that it's better to have one.  It can't hurt anything; it gives me added peace of mind rather like religion gives some people peace of mind.  (The present writer not included.)

---

### Post by RAOF on 2006-06-15
[QUOTE=jonrkc]I go to the "Shields Up!" section and run the function that tests all 1,000+ of common ports, and it takes about two minutes at most, often less....  I get a "Perfect Stealth" rating and though there will always be disagreement about the importance of a firewall, I stubbornly maintain that it's better to have one.  It can't hurt anything; it gives me added peace of mind rather like religion gives some people peace of mind.  (The present writer not included.)[/QUOTE]
It **can** hurt something.  On the default install, it's totally worthless, and if you have one then each time you install a server package (ssh, apache, vsftpd, whatever) you now need to go through an extra configuration step (opening the relevant ports in the firewall).

I feel that it is reasonable to assume that anyone who installs a server package such as ssh-server **wants** to be able to ssh in from the internet.  If the user is advanced enough to want to do the special things a firewall can do (only allow certain IP ranges, port knocking, whatever), then they certainly know enough to either configure iptables manually, or to install a gui-firewall configurator.  But these are advanced options; they're certainly not the default use-case.

---

### Post by airtonix on 2007-05-01
ahem .... how many of you are connecting to the net with a adsl router? you know one that is also a 4-port switch?
 
how many of you run servers in a public network enviroment?

do you want everyone seeing those samba shares?(this is why i hate samba..less control)

do you trust your flatmates friends who come over and hook up to your network, then try claiming they are a *hacker* when in fact all they are is a button pusher using a virus ridden vb app made by another eight year old.....and thusly procced to attempt a hack at your server?

closing all our ports then opening when you need to open them is a good thing.....it means you wont get caught with your pants down

it means you can relax and leave the linux-cave every now and then with out suffering anxiety attacks...

it means contigency plans are in effect.

---

### Post by jpatton on 2007-05-02
It seems to me that everyone is spouting off about the lack of open ports meaning that you are secure by default. I would tend to agree with those who realize that just because a port is closed does NOT mean you are safe!

I would put forward that on the default install of Fiesty, that the right person would be able to exploit it. I mean come on people, web browsers use ports, im's use ports, email use ports, I'm not claiming to be someone who could do this, but to operate under the false assumption that you are safe just because a given port isn't open is silly.

Then people are spouting about how wonderful netfilter/iptables are, these are just packet filters, the loweset common denominator of firewall. In the grand scheme these types of firewalls are stupid, they don't know how to do anything. True firewalls do so much more than filter packets, the scan the incoming packets at multiple layers of the stack.

This type of firewall can block a virus from coming in through email but not the email. Block a user from using a specific chat protocol while allowing other chat protocols to work. Contrary to the popular belief that the only good firewalls are hardware firewalls many application layer firewalls are implemented via software. 

These things should be used in conjunction to provide layers of protection. There must be some security guru somewhere reading this stuff and just giggling to himself. Do you really think it's EVER a good idea to take a default install of ANYTHING and just plug it into the internet?

Ok, feel free to flame or otherwise :)

---

### Post by az on 2007-05-02
> **airtonix said:**
> ahem .... how many of you are connecting to the net with a adsl router? you know one that is also a 4-port switch?
 
how many of you run servers in a public network enviroment?

This is not relevant to what should be running on a default Ubuntu desktop.

---

