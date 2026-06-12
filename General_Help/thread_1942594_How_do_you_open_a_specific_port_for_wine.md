---
title: "How do you open a specific port for wine?"
date: 2012-03-17
forum: General Help
---

### Post by octohedra on 2012-03-17
Hello,

Im trying to allow connections in 2 ports for this game and i cant seem to find how.

Nobody can join my games, i already disabled the firewall with no luck.

If you happen to know anything about this, id be very grateful for your answer.

Regards,

Octohedra.

---

### Post by octohedra on 2012-03-17
I decided to switch to a modem and its the same thing, anyone could throw some light into this?

Thanks

---

### Post by octohedra on 2012-03-18
Still need info on this.

BUMP

---

### Post by HiImTye on 2012-03-18
likely you need to open the ports on your router

depending on the port, your ISP might block them by default, try changing the ports, if possible to something outside your ISP's block list

---

### Post by octohedra on 2012-03-18
Thanks for your answer HiImTye,

Im using a modem and i have disabled ufw, also my isp doesnt block any ports, i need to make this 2 ports permanently open.

Here its the info from ShieldsUP![FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=courier new,courier][SIZE=3][COLOR=black]

GRC Port Authority Report created on UTC: 
2012-03-18 at 23:01:12 
 Results from scan of ports:0-1055      
2 Ports Open
1054 Ports Closed 
    0 Ports Stealth 

-------------------- 
 1056 Ports Tested  NO PORTS were found to be STEALTH. 
 Ports found to be OPEN were: 139, 445  Other than what is listed above, all ports are CLOSED. 
 TruStealth: FAILED - NOT all tested ports were STEALTH,                    - 
NO unsolicited packets were received,                    - 
A PING REPLY (ICMP Echo) WAS RECEIVED.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by HiImTye on 2012-03-18
what is your ISP
what are the ports you need open?
what is the game you need them open for?
what is the output of:
```
sudo ufw status verbose
```

as much info as possible is needed when trying to diagnose problems

---

### Post by octohedra on 2012-03-18
Seems the only way is using iptables, someone just gave me a hand in the #ubuntu irc.
here is what i did jsut in case:

iptables -I INPUT -p udp --dport 6112 -j ACCEPT

---

### Post by octohedra on 2012-03-18
Didnt help.

---

### Post by octohedra on 2012-03-18
what is your ISP: anteldata: uruguay
what are the ports you need open? 6112 / 6113
what is the game you need them open for? Warctaft 3 Frozen throne.
what is the output of: status: Inactive.
 	Code:
 	sudo ufw status verbose

---

### Post by HiImTye on 2012-03-18
the easiest way would be to use UFW to open those ports such as:
```
sudo ufw allow to any port 6112,6113 proto udp
```or tcp if it isn't udp, if you need both you will need to do one for each (i.e. proto udp and then proto tcp)
optionally you can specify specific IPs to open them to and then remove the rules later, for instance, here is how I opened ports for my printer:
```
sudo ufw allow from 192.168.0.9 to any port 515,631,8611,9100 proto tcp
```obviously you would want to enable UFW after this
```
 sudo ufw enable
```
if that doesn't help then either you need more ports or your ports are being blocked outside of your computer

---

### Post by HiImTye on 2012-03-18
[here]("http://portforward.com/cportsnotes/battlenet/battlenet.htm")'s your problem:
```
Warcraft III: 
Allow port 6112 TCP out and allow established sessions in 
Allow port 6112 TCP in (hosting custom games) 
Allow port 6113-6119 TCP out and in (hosting custom games if you've changed the default port in the Options/Gameplay screen) 
```you need to open all of those ports, in their perspective protocols.

```
sudo ufw enable
sudo ufw default deny
sudo ufw allow to any port 6112:6119 proto tcp
```should produce the results you need. to verify, your output of
```
sudo ufw status verbose
```should look like this:
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
6112:6119/tcp              ALLOW IN    Anywhere
6112:6119/tcp              ALLOW IN    Anywhere (v6)
```you can optionally delete the ipv6 rule
```
 sudo ufw delete 2
```replacing the 2 with whatever number it is, starting at 1, on the top (if you want a numbered list, use numbered instead of verbose)

---

### Post by octohedra on 2012-03-18
it worked, thank you very much!

---

### Post by HiImTye on 2012-03-18
you're welcome :D
please mark as solved so that others may benefit from it :)

---

