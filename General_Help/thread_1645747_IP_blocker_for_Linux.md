---
title: "IP blocker for Linux?"
date: 2010-12-15
forum: General Help
---

### Post by eyehatehippies on 2010-12-15
Just curious if anyone knows of an IP blocker usable with Linux. I used to use Peerblock for my Windows comp, and was curious if there was something similar for Linux anyone is aware of.

(currently running Ubuntu [lucid lynx])

---

### Post by antonvrg on 2010-12-15
moblock is an alternative... personally i think it is junk. some people like it, others like me dont.

---

### Post by Keypel on 2010-12-15
I think I read somewhere that Transmission bit torrent client uses the same peer list as peer-block / peer guardian.

If you use Transmission, it's under preferences -> privacy

But if it's true it uses the same list as peer block, then I don't understand why it only has 224,914 rules. I seem to remember peer block blocking allot more IP's.

---

### Post by trinitydan on 2010-12-15
You might try IPblock.

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)[IMG]http://ubuntuforums.org/images/editor/separator.gif[/IMG]

---

### Post by eyehatehippies on 2010-12-15
Thank you all for the responses! Much appreciated!

---

### Post by jre on 2010-12-16
If you don't need a GUI I recommend to use moblock's successor PeerGuardian Linux (see my signature). If you need a GUI you can use the old moblock/blockcontrol/mobloquer combination or iplist/ipblock.

When you compare how many IPs are blocked you have to look whether IPs or IP ranges are blocked (the first being millions or billions, the latter a few hundred thousands). Generally I recommend to use the blocklists from iblocklist.com, there you get all lists, including those from bluetack and TBG, which you probably know from PeerBlock.

If you use blocklists in an application like transmission, then only this application's traffic will be checked. In contrast the real IP blockers work for your whole system. So if you just want to avoid downloading fake files then the builtin block mechanism of transmission is ok. But if you just don't want to be contacted by any of the organizations that are in the blocklist, then you should use an IP blocker for "stealth" mode.

---

### Post by tolf242 on 2010-12-17
> **trinitydan said:**
> You might try IPblock.

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)[IMG]http://ubuntuforums.org/images/editor/separator.gif[/IMG]

[SIZE="2"][FONT="Comic Sans MS"]Thanks for posting that how to, unfortunately I still can't get IPbock to show after following the steps.

Any thought's on this would be gratefully received.

Thank you, Tolf242. [/FONT][/SIZE]

---

### Post by trinitydan on 2010-12-20
I can't take the credit for the how to, only for linking you to it.;)  Sorry, I managed to miss your post for a few days. 

Maybe the problem is that in the tutorial it says to type sudo aptitude update and that is not current for Ubuntu 10.10.  If that is what you had typed in you should try again but this time use:```
 sudo apt-get update
```Followed by:
```
sudo apt-get install iplist
```After that you should be able to type in: ```
sudo ipblock -g
``` to start the ipblock g.u.i. or navigate to it under Applications>Internet>
As soon as you get it started update it.

Hopefully that helps.

Edit:  [uljanow]("http://ubuntuforums.org/member.php?u=335776") (op) is doing a fine job of maintaining this and now the directions are correct again on the howto. :D

---

### Post by WorMzy on 2010-12-20
I use iptables as a IP blocker. My basic config is as follows:

```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [738:82758]
:OPEN-TCP - [0:0]
:OPEN-UDP - [0:0]
-A INPUT -s 127.0.0.0/8 -i wlan0 -j DROP 
-A INPUT -s 127.0.0.0/8 -i eth0 -j DROP 
-A INPUT -i lo -j ACCEPT 
-A INPUT -m state --state INVALID -j DROP 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -p icmp -m icmp --icmp-type 8 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m state --state NEW -j OPEN-UDP 
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j OPEN-TCP 
-A INPUT -j REJECT --reject-with icmp-proto-unreachable 
-A INPUT -p tcp -m recent --set --name TCP-PORTSCAN --rsource -j REJECT --reject-with tcp-reset 
-A INPUT -p udp -m recent --set --name UDP-PORTSCAN --rsource -j REJECT --reject-with icmp-port-unreachable 
-A OPEN-TCP -p tcp -m recent --update --seconds 60 --name TCP-PORTSCAN --rsource -j REJECT --reject-with tcp-reset 
-A OPEN-TCP -p tcp -m tcp --dport 80 -j ACCEPT 
-A OPEN-UDP -p udp -m recent --update --seconds 60 --name UDP-PORTSCAN --rsource -j REJECT --reject-with icmp-port-unreachable 
-A OPEN-UDP -p udp -m udp --dport 53 -j ACCEPT 
COMMIT
```

Once that's in place, I add IPs I want to block by running:
```
sudo iptables -I INPUT -s xxx.xxx.xxx.xxx -j DROP
```
Then save the changes:
```
sudo /etc/init.d/iptables save
```

I generally only block individual IP addresses which spam my server with attempts to find my phpmyadmin page.

---

### Post by katykat on 2010-12-20
I generally only block individual IP addresses which spam my server with attempts to find my phpmyadmin page.
------------------------------

Isnt there an app which does this automagically?

I forgot its name...

---

### Post by tolf242 on 2011-01-05
> **trinitydan said:**
> I can't take the credit for the how to, only for linking you to it.;)  Sorry, I managed to miss your post for a few days. 

Maybe the problem is that in the tutorial it says to type sudo aptitude update and that is not current for Ubuntu 10.10.  If that is what you had typed in you should try again but this time use:```
 sudo apt-get update
```Followed by:
```
sudo apt-get install iplist
```After that you should be able to type in: ```
sudo ipblock -g
``` to start the ipblock g.u.i. or navigate to it under Applications>Internet>
As soon as you get it started update it.

Hopefully that helps.

Edit:  [uljanow]("http://ubuntuforums.org/member.php?u=335776") (op) is doing a fine job of maintaining this and now the directions are correct again on the howto. :D

[SIZE="2"][FONT="Comic Sans MS"]Thank you trinitydan, that worked perfect! Thanks also to uljanow for the howto and the time spent amending and updating.[/FONT][/SIZE]

---

### Post by trinitydan on 2011-01-05
> **tolf242 said:**
> [SIZE=2][FONT=Comic Sans MS]Thank you trinitydan, that worked perfect! Thanks also to uljanow for the howto and the time spent amending and updating.[/FONT][/SIZE]
You're welcome(and +1 on the thanks to uljanow)!  I'm glad you got it working!  IPBlock is a great program. I think everyone using torrents should use it or some other form of IP blocker and I find the IPBlock GUI to be very handy.
:guitar:

---

