---
title: "DSL connection keeps disconnecting after ~30 mins"
date: 2006-06-02
forum: General Help
---

### Post by amihaic on 2006-06-02
HI All,

I installed Ubuntu 6.06 and configured my DSL connection using pppoeconf (btw if anyone can suggest a nice GUI application for configuring and starting/stopping the connection i'd appreciate that).
Now, the internet connection starts at boot time, and I can stay connected for about 30 minutes, but then all of a sudden I'm not connected anymore.

Don't have a clue where that's from, if I try to connect again using 'pon dsl-provider' it keep saying that i'm already connected or something like that but nothing works, not even ping. The only way to restart the connection is to boot again.

I'm having this problem only in Ubuntu/Kubuntu. Didn't have this problem when I installed Suse.

Please help.
Thanks.

---

### Post by RRS on 2006-06-02
> .......GUI application for configuring and starting/stopping the connection.....

System>Administration>Networking

As for your connection problem, a little more info would be handy.

What DSL provider and do you use an external DSL modem or router?

Also what was your previous system? Breezy, Windows?
And how was your connection configured (I assume it worked OK before)

Often with DSL the modem handles PPPoE duties and the computer connects to it with DHCP.

---

### Post by amihaic on 2006-06-02
[QUOTE=RRS]System>Administration>Networking[/QUOTE]
This is just the network configuration. I can't configure any DSL dialing from there.

I use an Alcatel SpeedTouch Home modem connected to my ethernet card, and it's not a router (although configuring it as a router would solve this problem but introduce other ones).

I used to use Windows before, and Suse. In both I didn't need to add anything in the configuration other than my user name and password.

And I'm from Israel, so I doubt it has anything to do with my provider.

---

### Post by hibatsu on 2006-06-02
Exactely the same problem!
After 30 mins disconnect from the internet. also using pppoeconf.
Provider is ocn Japan. Its an external dsl modem. Config file looks like this:

cat /etc/ppp/peers/dsl-provider
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "***@ipcon.ocn.ne.jp"

(can't use code tag cause the opposite [ doesn't seem to work with my keyboard conf)

---

### Post by amihaic on 2006-06-02
[QUOTE=hibatsu]Exactely the same problem!
After 30 mins disconnect from the internet. also using pppoeconf.
Provider is ocn Japan. Its an external dsl modem. Config file looks like this:

cat /etc/ppp/peers/dsl-provider
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "***@ipcon.ocn.ne.jp"

(can't use code tag cause the opposite [ doesn't seem to work with my keyboard conf)[/QUOTE]
This is what it says on my /etc/ppp/peers/dsl-provider exactly (except the username).

---

### Post by adam.hill on 2006-06-02
I've been having the same problem since upgrading from 5.10 to 6.06 yesterday, except my connection lasts anywhere from ten to eighty minutes before mysteriously disappearing. I'm able to re-connect without rebooting, though, using `poff -a` to end the connection and then `pon dsl-provider` to start it up again.

I've got the same dsl-provider file as the other posters (less the username, of course), and my ISP is Primus in Canada. I've also got a SpeedTouch modem connected via eth0, and no router. 

One thing I've noticed - my connection gets lost whether it's idle (no network activity) or actively uploading / downloading. (My first thought was that some sort of "disconnect when idle for X minutes" option got set in the upgrade, but that doesn't seem to be the case.)

**Edit: **
It seems that I'm not actually disconnecting; rather, I'm just losing track of the DNS servers, and so I can't resolve any web address. When my connection appears to be dropped: 
- if I run ipconfig, ppp0 still appears as being up and running
- I can ping Google by IP (72.14.207.99) but not by name.
so I'm still actually connected.

I did some fiddling based on some remarkably helpful info in the Wiki ([https://wiki.ubuntu.com/StaticDnsWithDhcp]("https://wiki.ubuntu.com/StaticDnsWithDhcp")), and also double-checked my modem's settings, and it seems to have fixed my problem. I've cronned a script to run overnight to check that names resolve to IPs, and hopefully it's still working in the morning. 

Hopefully that's all the problem is...

---

### Post by amihaic on 2006-06-03
> **adam.hill]
One thing I've noticed - my connection gets lost whether it's idle (no network activity) or actively uploading / downloading. (My first thought was that some sort of "disconnect when idle for X minutes" option got set in the upgrade, but that doesn't seem to be the case.)

**Edit: **
It seems that I'm not actually disconnecting said:**
> https://wiki.ubuntu.com/StaticDnsWithDhcp[/URL]), and also double-checked my modem's settings, and it seems to have fixed my problem. I've cronned a script to run overnight to check that names resolve to IPs, and hopefully it's still working in the morning. 

Hopefully that's all the problem is...

I think I have the same problem. The PPP connection also stays connected from me (or at least that's what it says).

The symptom for it is really weird - I can't seem to surf web pages from a certain moment (supposedly when the DNS loses itself), but e.g Synaptic is still downloading packages from the repository, and Kopete still works. That can explain why.

@adan - Can you share the script here?

---

### Post by hibatsu on 2006-06-03
Yeah, exactly. Webpages don't work anymore. But instant messaging and running apt-get downloads still work further on.

Btw. does anyone know a good kde tool to connect and disconnect (including an online time counter)?

---

### Post by amihaic on 2006-06-03
[QUOTE=hibatsu]Btw. does anyone know a good kde tool to connect and disconnect (including an online time counter)?[/QUOTE]
I've tried using Knet but it didn't really work for me. Maybe it will for you.
I've been using the solution at [https://wiki.ubuntu.com/StaticDnsWithDhcp](https://wiki.ubuntu.com/StaticDnsWithDhcp) and so far it works, I just hope it will still work after a reboot.

Does anyone knows how can I configure my system to dial automatically at boot?

---

### Post by adam.hill on 2006-06-03
> **amihaic]
@adam - Can you share the script here?[/QUOTE]
Sure. It's a Perl script that pings google by IP and by name (ie google.com) and logs it, and also logs the output of 'ifconfig' and 'tail /var/log/messages/' so you can see . I cronned it to go every few minutes from 2:00am-4:00am and from 5:00am-7:00am (the hour gap is so that I could tell if it would drop if the connection wasn't being used), and it seems to have worked - I came back this morning to a normally-working Internet :)

Pick your own times, and file/folder names, as appropriate.

**script.pl**
```
#!/usr/bin/perl

$datetime = `date +%H.%M.%S` said:**
> 
Does anyone knows how can I configure my system to dial automatically at boot?
For me, pppoeconf asked if I wanted the connection to start automatically, and I said yes. Which didn't seem to work at first; I had to edit my /etc/network/interfaces to turn off eth0 from being loaded automatically so that ppp could bring up eth0 when it was ready for it (as per [this thread]("http://ubuntuforums.org/showthread.php?t=12896")).

---

### Post by Eriksmits596 on 2007-10-16
I also have the same problem, in SuSE 10.3. But then the modem's only working in 3 minutes.

---

