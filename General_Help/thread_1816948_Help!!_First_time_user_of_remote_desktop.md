---
title: "Help!! First time user of remote desktop"
date: 2011-08-02
forum: General Help
---

### Post by CaptainMark on 2011-08-02
Im using natty on my current machine and also the same on my mums laptop which ive just wiped windows. Because i figured she would need the occasional bit of help i figured id look into using the remote desktop software software that comes installed by default on natty, so to test on my own netbook first i opened 'remote desktop' on the netbook/server and clicked 'allow others to view your desktop' and after checking connectivity it told me i can connect to my machine using 192.168.0.5 (as i expected) so i go to my desktop/client and click 'remote desktop viewer' type in the local ip address and brillo, all works fine. Now to test over the internet, back to the netbook/server i click 'configure network automatically to accept connection' and i was given a similar message only this time with an external ip address (for arguments sake 12.34.567.890) so i go back the desktop try again with this ip and it just hangs, nothing happens and the netbook/server doesnt detect that someone is trying to use the desktop like normal.  Im probably doing something really simple wrong but im more or less first time with this so i dont know exactly what to do now, 

any help would be appreciated

mark

---

### Post by tredegar on 2011-08-02
192.168.x.y is a L(**L**ocal)AN address, not an "internet" one.

Your mum's router / modem is probably running a firewall by default (good) but then needs to be configured to forward the port from _its_ *internet* address to the *LAN IP* of her laptop. The port is probably 5900 - 5909.

How to do this depends on her Modem / Router (you do not provide any details) but it is probably running a secure firewall by default. This is "good" because it will secure her, but it will not let you in unless you seem to know what you are doing (which is also good).

Opening ports like this has the potential for serious security implications, but for a one-off, now & again, they are probably trivial. I do it all the time, with an elderly relative. She does not start the vncserver until I have asked her, she gets confirmation that I am about to connect, she phones me the (random) password.

I suggest you read up on "remote desktop sharing". 

Windows tends to let everybody in. Linux enforces that you expressly define who is allowed to "share" anything. This makes configuration more awkward, but also very much more secure.

Your problem lies with understanding the difference between LAN IPs and internet IPs and IP-forwarding rules in her router / modem.

Good luck.

---

### Post by CaptainMark on 2011-08-04
Hi thanks for your reply,

I realise the difference between between a lan address and external, i'm still testing on my own setup before i try on my mums and i kinda thought about firewalls so to check (i should have mentioned before) i checked my routers upnp status page and the port 5900 is being opened for the server, thats was totally confused me, any advice?

EDIT:
im hoping it wont make a difference that the two computers im testing with are actually on the same lan anyway, i figured it would still send a signal out to my isp's server and back to my router again just the same as if i was using two seperate pcs in different places. also if i go to the 'remote desktop' on both pcs and click 'confire network to connect automatically' both the desktop and the netbook give the same ip address, i find this confusing and didnt expect it to be the case

---

### Post by Elfy on 2011-08-04
You might want to look into SSH, also the security sticky here. 

Also have a look at [bodhi.zazen's]("http://ubuntuforums.org/member.php?u=89054") blog - there is a SSH section in his GNU'Linux section there. 

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[http://blog.bodhizazen.net/](http://blog.bodhizazen.net/)

---

### Post by tredegar on 2011-08-04
Ports 5900-5909 need to be opened on your router and forwarded to the LAN IP of the computer you want to use to view the "remote" desktop.

Test it like this:
On PC A  Set it up to share the desktop. Use a password.

Use **ifconfig** to find the LAN IP of machine B, if you do not already know it. 
Configure your router to forward ports 5900-5909 from the internet to the LAN IP of machine B.
Note that I had to configure the firewall in my router (DG834G) manually. Clicking "Configure network automatically to accept connections" did not work.

Find out your router's WAN IP. Your router will have this information, or you can run this 
```
wget -O - -q icanhazip.com
```
in a terminal.

Connect to the desktop on PC A knowing that it can be found at YOUR.WAN.IP.ADDR:0 

That's it.

Remember that **vnc** is _not secure_. Script-kiddies will be hitting those ports all the time. It is much better to tunnel your connection through **ssh** There are tutorials all over the web. [Here]("http://www.cyberciti.biz/faq/howto-setup-vnc-server-ssh-client-tunnel-via-internet/") is one

Remember also, if you are going to be offering **ssh** as a service to the big bad net, that **ssh** had better be set up properly, and the links forestpiskie gave you should help with that. As a minimum
- Disable root logins over ssh (this may be the ubuntu default. See man **ssh_config**)
- Disable Passwordauthentication (blocks all the script kiddies).
- Enable (and set up) Private/Public key authentication (this means that you can login securely without any passwords, so long as no one knows your PRIVATE key).

You have some homework, and experiments, to do. But it's quite fun working out how to configure everything, and when it is all set up properly, it is very very usable.

You have already learnt to "Set it up on the LAN, and test it out, *then* try it on the internet".

Have fun, and let us know how you get on.

---

### Post by CaptainMark on 2011-08-04
thanks for the tips, ill have to delve into this when i get some free time, ive got a busy second half of the week, will report how i get on later at the weekend, many thanks

---

### Post by CVGH on 2011-08-04
If you go the ssh route, don't forget fail2ban.
Great way to protect from kiddies as well.....

---

