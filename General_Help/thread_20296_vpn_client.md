---
title: "vpn client?"
date: 2005-03-16
forum: General Help
---

### Post by rookie on 2005-03-16
Hello

in win xp, you ca create a vpn client session. is there a similar tool for ubuntu?

---

### Post by bored2k on 2005-03-16
[QUOTE=rookie]Hello

in win xp, you ca create a vpn client session. is there a similar tool for ubuntu?[/QUOTE]
 Yep, forgot the name though.

---

### Post by rookie on 2005-03-16
:lol:  :lol:

---

### Post by alastair on 2005-03-16
There is no GUI setup or point & click interface for setting up an VPN in Linux - as far as I know. VPN's are also quite complex sometimes, and the complexity depends on what you are connecting.

The easiest VPN tool in Linux is probably OpenVPN - which is very straightforward to setup, but still requires a little reading and thought.

See package : openvpn

This will have to be at BOTH ends.

More complex but perhaps more widely used is IPSec VPN's. 
It depends on your requirements.

---

### Post by rookie on 2005-03-16
hmmm...both ends...no, that's not what I was looking for. my firewall/router manages the vpn's, I don't want to do anything on os-level.

i need a client, which, for example, supports pptp-vpns. all you should need to type in is the ip-adress of the remote pc and username/password. the firewall does the rest.

---

### Post by jkka on 2005-03-16
[QUOTE=rookie]
i need a client, which, for example, supports pptp-vpns. all you should need to type in is the ip-adress of the remote pc and username/password. the firewall does the rest.[/QUOTE]

Add to /etc/apt/sources.list
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

#sudo apt-get update
#sudo apt-get install pptpconfig
#sudo pptpconfig

---

### Post by az on 2005-03-16
Don't you need an encryption kernel module or something?

---

### Post by rookie on 2005-03-16
[QUOTE=jkka]Add to /etc/apt/sources.list
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

#sudo apt-get update
#sudo apt-get install pptpconfig
#sudo pptpconfig[/QUOTE]

Thanks. Meanwhile, I found this link

[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

---

### Post by thomasmathiesen on 2005-04-15
[QUOTE=rookie]Hello

in win xp, you ca create a vpn client session. is there a similar tool for ubuntu?[/QUOTE]

If you're using openvpn server, you can use the new client gui that I've just released for linux  :razz: 

It's still in it's early stages, but it works fine, and I need it for my customers, so if you find _any_ bugs, tell me asap!

Find source,debian and redhat packages at 
[http://www.clubnix.net/modules/mydownloads/viewcat.php?cid=8](http://www.clubnix.net/modules/mydownloads/viewcat.php?cid=8)

Homepage/forum
[http://www.clubnix.net/modules/newbb/viewforum.php?forum=31](http://www.clubnix.net/modules/newbb/viewforum.php?forum=31)

/Thomas

---

