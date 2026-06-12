---
title: "peergaurdian????"
date: 2009-08-20
forum: General Help
---

### Post by publicladykilla on 2009-08-20
is there a program that is like peergaurdian that is for ubuntu? And im pretty much a nobb so itd be nice if it had an easy interface

---

### Post by hibliss on 2009-08-20
Yes, it doesn't even need to be installed either. It is called common sense. Use it when downloading to avoid legal troubles.

Peerguardian is a flawed concept and there is no way the lists can be accurate, or even close. Don't let something like that give you a false sense of security.

---

### Post by roypk on 2009-08-20
> **publicladykilla said:**
> is there a program that is like peergaurdian that is for ubuntu? And im pretty much a nobb so itd be nice if it had an easy interface

If you want to use it mainly for p2p, Transmission, the bundled torrent client, can utilise the block list.

Best regards,
Roy

---

### Post by hibliss on 2009-08-20
Trasmission, ktorrent, and Vuze all have IPfilter option available. You can use the same useless blocklist that Peerguardian uses.

Feel safe!

---

### Post by Bonster on 2009-08-20
there is a PG clone called ipblock, another one called moblock or moplock, forgot something like that

---

### Post by nah40 on 2009-08-20
here is a gui for ipblock

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by publicladykilla on 2009-08-20
> **hibliss said:**
> Yes, it doesn't even need to be installed either. It is called common sense. Use it when downloading to avoid legal troubles.

Peerguardian is a flawed concept and there is no way the lists can be accurate, or even close. Don't let something like that give you a false sense of security.

Is that supposed to scare me or something? millions and millions of people download.. the chances are tiny of even getting a warning..:popcorn:

---

### Post by lovinglinux on 2009-08-20
I use [moblock](http://moblock-deb.sourceforge.net/),which is great. You can also install [mobloquer](http://mobloquer.foutrelis.com/), which is a gui for it.

[IPList](http://iplist.sourceforge.net/) is also great and looks like PeerGuardian. Nevertheless, I haven't used it since it requires java. I don't like java very much.

About the common sense, ip blockers are not used only to "avoid warning letters". I use moblock as a security tool and, since it can handle iptables scripts, it makes the job of the firewall manager.

You can also use blocklist features of torrent clients like Transmission and Deluge. I prefer Deluge for many reasons. But keep in mind that they only protect the torrent layer, while moblock and iplist protect the whole network.

Also check the "[General Moblock Thread](http://ubuntuforums.org/showthread.php?t=803183)"

---

### Post by hibliss on 2009-08-20
> **publicladykilla said:**
> Is that supposed to scare me or something? millions and millions of people download.. the chances are tiny of even getting a warning..:popcorn:

Then why do you feel you need a blocklist?

> **lovinglinux said:**
> 
About the common sense, ip blockers are not used only to "avoid warning letters". I use moblock as a security tool and, since it can handle iptables scripts, it makes the job of the firewall manager.

You can also use blocklist features of torrent clients like Transmission and Deluge. I prefer Deluge for many reasons. But keep in mind that they only protect the torrent layer, while moblock and iplist protect the whole network.


I personally prefer a proper firewall to a blocklist of known "bad IPs". I would venture to say that very few people use these blocklists for the reason that you do.

Really, a hardware firewall that blocks incoming connections (like in your router) and a few decent browser plugins is sufficient for most. NoScript+Ablock Plus should do fine.

---

### Post by doas777 on 2009-08-20
+1 for iplist. I tried some of the others, but they didn't play nice with network-manager, since the connection didn't come up before service load.

---

### Post by jre on 2009-08-21
> **doas777 said:**
> +1 for iplist. I tried some of the others, but they didn't play nice with network-manager, since the connection didn't come up before service load.
The root problem is that moblock is started by blockcontrol automatically at system boot. While iplist is often started manually, so quite a bit later. But both apps also offer the other concept.
Further I changed some stuff (later automatic start and a watchdog which checks whether another firewall messed up the iptables rules). So you might try it again - but of course iplist is a nice application, too.

Whether IPBlockers give you safety, ... definitely not 100%. (Personally I don´t care about that.) And this is not the sole purpose of IP blockers. They are also made to get rid of bad and fake seeders. And of course they can be used for privacy and security purposes totally unrelated to torrents.

It´s always good to know the basics about IP Blockers. Users should at least
[LIST]
[*]know that a IP blocker does simply prevent connections to IPs in the blocklist (not more, especially they do **not** hide your IP)
[*]read the descriptions of the blocklists, that they use
[*]double think which ports they don´t want to check (=whitelist). E.g. **not** the port of their privacy needing application. You might cry if you knew how often I´ve seen a whitelisted torrent port.
[*]check whether it is working at all (anything in the logfile? does pinging an IP from the blocklist work?)
[/LIST]

---

