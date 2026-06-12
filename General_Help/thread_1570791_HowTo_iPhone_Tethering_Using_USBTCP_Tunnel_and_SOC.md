---
title: "HowTo: iPhone Tethering Using USB/TCP Tunnel and SOCKS Proxy Over SSH"
date: 2010-09-08
forum: General Help
---

### Post by togume on 2010-09-08
I've been searching for a while how to best tether my 10.04 laptop to my iPhone 4, and finally came up with a good way. There was no good howto, so I'm documenting it here for others to enjoy as well:

Setup:
iPhone 4 with 4.01 Jailbroken and OpenSSH installed
Ubuntu 10.04 (it include the usbmux package)

[LIST=1]
[*]Connect iPhone to computer with USB
[*]In a terminal, type "sudo iproxy <local port> <iPhone port>" (i.e. sudo iproxy 2222 22)
[*]In another terminal, type "sudo ssh root@127.0.0.1 -p <local port> -D <desired local proxy port>" (i.e. sudo ssh root@127.0.0.1 -p 2222 -D 9999)
[*]Accept SSH encryption key (if needed), and enter SSH password (default is alpine, in which case CHANGE IT)
[*]Open up Network Proxy application on Ubuntu (System -> Preferences -> Network Proxy)
[*]Set the SOCKS5 proxy (Socks host) to 127.0.0.1 and the <desired local port> used above
[*]Test using browser
[*]Success!
[/LIST]

That's it. After you do it once it should be quite easy to do it again.

---

### Post by unbuntunewb on 2010-09-08
this works up until the part where I set up the proxy network connections, there is no change in my ip address that means its not working right? i also tried this in foxy proxy and have had no luck, this is driving me crazy, any ideas?

---

### Post by togume on 2010-09-08
The IP on the computer will not change. However, the IP others see will change. When you go to [http://www.whatismyip.com/](http://www.whatismyip.com/) you should see the difference.

I'm using Chrome. However, in Firefox, you should check to make sure you're set to use the System Proxy settings. That way it will pick up the proxy. Otherwise, you could set the proxy there instead of Network Proxy (Firefox -> Preferences -> Advanced -> Network -> Settings).

Hope that helps.

---

### Post by Elep.Repu on 2011-05-16
Awesome! This worked perfectly for me with no problems!

I'd like to know a little more about how this works, and why my iPhone is on root@127.0.0.1 

Thanks!

[update] Looks like that iproxy command actually is used to tether the iphone. So it probably just mounts the iphone @ that address. Makes sense! Cool stuff.

---

### Post by GhettoMed1c on 2011-07-22
[FONT=Arial Black][SIZE=4][COLOR=Red]Thank You!!!! Works Brilliantly!!![/COLOR][/SIZE][/FONT]
:KS:D
> **togume said:**
> I've been searching for a while how to best tether my 10.04 laptop to my iPhone 4, and finally came up with a good way. There was no good howto, so I'm documenting it here for others to enjoy as well:

Setup:
iPhone 4 with 4.01 Jailbroken and OpenSSH installed
Ubuntu 10.04 (it include the usbmux package)

[LIST=1]
[*]Connect iPhone to computer with USB
[*]In a terminal, type "sudo iproxy <local port> <iPhone port>" (i.e. sudo iproxy 2222 22)
[*]In another terminal, type "sudo ssh root@127.0.0.1 -p <local port> -D <desired local proxy port>" (i.e. sudo ssh root@127.0.0.1 -p 2222 -D 9999)
[*]Accept SSH encryption key (if needed), and enter SSH password (default is alpine, in which case CHANGE IT)
[*]Open up Network Proxy application on Ubuntu (System -> Preferences -> Network Proxy)
[*]Set the SOCKS5 proxy (Socks host) to 127.0.0.1 and the <desired local port> used above
[*]Test using browser
[*]Success!
[/LIST]

That's it. After you do it once it should be quite easy to do it again.

---

### Post by LaMooNa on 2011-09-05
Amazing topic
I just wanna to know how to transfer file from pc to iphone using this connect :)

---

### Post by spongebob1981 on 2012-01-24
To transfer files:

0) Get sshfs installed. Don't remember how and if I did it or it came installed. Try apt-get ;)
1) In a terminal, type "sudo iproxy <local port> <iPhone port>" (i.e. sudo iproxy 2222 22, as in OP)
2) In another terminal type in: "sshfs root@127.0.0.1:/ ~/ipodmnt/ -p 2222" without the quotes as always. It asks for the password of the device, alpine as default. The directory ~/ipodmnt must be created and have access rights.
3) Profit.

---

