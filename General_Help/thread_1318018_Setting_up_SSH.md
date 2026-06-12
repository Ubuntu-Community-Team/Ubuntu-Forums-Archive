---
title: "Setting up SSH"
date: 2009-11-07
forum: General Help
---

### Post by The Funkbomb on 2009-11-07
Not really sure if SSH is what I need.  Let me tell you about what I want to do.

My Desktop is always on.  Sometimes the screen is locked but it runs pretty much 24/7 (sorry Mother Nature).  All of my stuff is stored on this computer.  It runs 9.10 x64.

I also have a netbook that runs Masonux (an LXDE Ubuntu).  Pretty much I want a secure connection that allows me to access all my desktop stuff from wherever I am with the netbook.

How do I do this?  How secure can I make it?

---

### Post by nothingspecial on 2009-11-07
ssh is exactly what you need.

First of all make sure you have openssh-server and openssh-client installed.

Then you need to get a fixed ip address. See [[COLOR="Magenta"]here[/COLOR]]("http://www.dyndns.com/") 

Then you need to set up your keys. See [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by Defrector on 2009-11-07
SSH is pretty darn secure and is rather universal between OSes. SSH in its raw form likes to run as a remote command line to access a computer remotely over a very secure (paranoid?) connection. It can tunnel X11 (X window system) if you can do that from your laptop. SSH isn't pre-installed in ubuntu, I assume for security reasons. (less open ports is better)

Another to check out is VNC which is a bit easier to get working graphically, including the fact that some VNC servers can give a web interface. It is, in my biased unprofessional opinion, not as secure as SSH.

running 'sudo synaptic' will help you find and install these programs. They come with docs but it tends to be easier to just use Google and the forums except for 'man ssh' and so on.

---

### Post by Ampi on 2009-11-07
I have the exact same issue.

The static Ip address, how does that work when a router is in between?

---

### Post by stoyanmihaylov on 2009-11-07
> **Ampi said:**
> I have the exact same issue.
The static Ip address, how does that work when a router is in between?
If your desktop is behind router - you can:
1. expose your desktop through router. Not good idea, because router is additional security for desktop.
2. You can forward some port of router to desktop's 22 port.
In both cases you need to have control over router.

---

### Post by dox_drum on 2009-11-07
> **stoyanmihaylov said:**
> If your desktop is behind router - you can:
1. expose your desktop through router. Not good idea, because router is additional security for desktop.
2. You can forward some port of router to desktop's 22 port.
In both cases you need to have control over router.

Sorry stoyanmihaylov, May you explain how to do so?

Thank you.

---

### Post by Ampi on 2009-11-07
I have total control of router.
I also would like to know how exactly that would go into installing and preparing the ssh'ing...

---

### Post by dox_drum on 2009-11-07
> **Ampi said:**
> I have total control of router.
I also would like to know how exactly that would go into installing and preparing the ssh'ing...

Do you know if there is any way of setting static IP for the computers? Because I have two at home and I'd like to connect them through SSH or SFTP.

Thanks.

---

### Post by Ampi on 2009-11-07
I do know that with at dyndns.com you can ask for an address, e.g. user.homelinux.com, and the dyndns server will make sure that every time your (normal) IP address changes, it will be updated within that address.
Doing this, your user.homelinux.com-address will be your static IP address. 
The only thing I don't know is how to do that if you have a router in between, but if you don't have a router, this is all you need.

---

### Post by isoToxin on 2009-11-07
You shouldn't worry about routers / port forwarding etc until you have successfully set up ssh locally.  You really need to know what you're doing with ssh before you open it up to the world via the internet.

Basic top-level overview of the tasks you need to perform are:

Assign your desktop pc (ssh server) a static ip address on your home network.

Install ssh server on this machine.

Install an ssh client on your notebook (ssh client).  I use puTTY btw which is an excellent GUI client, but any will do.

Connect your notebook to the SSH server using it's static ip address and port (22 by default).

Secure ssh further by enabling rsa key authentication and disabling interactive (user/password) auth.  Once it's in this state, you will need a public rsa key to authenticate witht the server making it secure enough to use over the web.  There are tools to generate key pairs in openssh.

Now you have a working ssh environment that's secure on your home network, it's time to configure the router.  You will need to forward the ssh server port on your desktop pc to your public ip address.  

Finally, you will need to get a dynamic dns service set up so that you can always find your home computer no matter what public ip your desktop or notebook pcs are connecting from.  A good one for this is no-ip.com.

If you get stuck setting up / configuring ssh, here is a guide I just found on google for doing it under ubuntu.  There's literally hundreds of such tutorials out there for ssh, it's a very commonly used technology.

[https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html)

For your router setup, you usually just log onto it's web interface through a browser and set up port forwarding (sometimes called server publishing) through that.

Good luck.

---

### Post by The Funkbomb on 2009-11-07
So, if I understand this correctly.

My desktop is going to be the server.  The netbook is the client.  

1.  Set up a static IP.  My IP address has been pretty static for the last 5 or 6 years but DynDns will be permanently static.

2.  I'm going to create a public and private key.  When I use my netbook from anywhere, the keys will be matched up and I will be granted access.

3.  I'm then going to open up a port to the world and I'll be able to use it even if the screen is locked?

---

### Post by isoToxin on 2009-11-07
> **The Funkbomb said:**
> So, if I understand this correctly.

My desktop is going to be the server.  The netbook is the client.  

1.  Set up a static IP.  My IP address has been pretty static for the last 5 or 6 years but DynDns will be permanently static.

You will have a static private ip for your desktop (which will be the ssh server).  This ip is the one on your home lan (e.g. 192.168.0.3 etc).  Your public ip is the one that your isp gives you when you connect to the web via adsl/cable etc.  (e.g. 86.132.54.23 etc).  What a dynamic dns service does is maps an internet hostname to your public ip address.  So if you use no-ip.com's dynamic dns service, you can always find your home public ip address from anywhere in the world just by typing in a hostname.  e.g. if my public ip address is 87.65.98.132, and I have set up a dynamic dns pointer using the hostname mylan.no-ip.com, then from anywhere in the world I will be able to ping my router just by typing 

ping mylan.no-ip.com

Dynamic dns is needed because if your isp changes your ip address, then you will still be able to find it.  Many home routers have a dynamic dns client running on them that you can use to tie them to a service such as no-ip.com, but failing that, you may need to run a daemon on your home desktop system which updates for you in the event that your isp changes your public ip address.

The alternative to using a dynamic dns system is to pay extra to your isp for a static ip address, but this is mostly used for corporate connections as it is much more expensive.

> 2.  I'm going to create a public and private key.  When I use my netbook from anywhere, the keys will be matched up and I will be granted access.Yes.  Every connection will be compared to an "authorised" list of public keys.  If it's not on the list, connection is refused.  This is a very secure way of authenticating yourself to an ssh server because (as long as you disable standard interactive password auth) it doesn't allow people to run brute force or dictionary password attacks against your system.  Essential for internet connections imo, although a very strong password would be an alternative to using key auth I suppose.

> 3.  I'm then going to open up a port to the world and I'll be able to use it even if the screen is locked?Correct.  If you simply need to access files on the ssh server, that can be achieved by using an SCP (secure copy) client.  This is a file transfer system that is used over ssh.  

OpenSSH server also has a "tunneling" feature.  Once you have made your initial ssh connection, you can then define any number of additional port tunnels to any device on your home lan, including the ssh server itself.  For example, ubuntu has a remote desktop feature (using vnc), which you could easily connect to and remote control the machine via the ssh connection you have established.  Using this, it's possible to connect to any service on any system on your home network.  So you could tunnel to a vnc service, or a remote desktop port on a windows machine etc.  The ssh server acts as a relay, passing data to from the client to any machine on your home lan.  If you've ever used a vpn system in the past, it works in a functionally similar way.  The puTTY ssh client fully supports ssh tunnels, allowing you to map ports on your client to ports on either the ssh server, or any machine the ssh server has local connectivity to.

My suggestion is to do all of this one step at a time though.  Your first goal should be to get "command line" access to your server via ssh.  Once that's done, you can move on until you have learnt it all, and are running tunneled apps over it.

I use ssh to access my home systems from work, and it works brilliantly.

---

### Post by The Funkbomb on 2009-11-13
Sorry to bump my old thread but how much does DynDNS cost?

---

### Post by nothingspecial on 2009-11-13
Same as ubuntu

---

### Post by The Funkbomb on 2009-11-13
Very well.  That's good news.  Thanks for the response.

I have a few more questions.  Bare with me.  I'm a little paranoid.

1.  How can I tell if my computers are secure?  I definitely plan to use passkey auth and changing my default port.  How can I tell if ssh is actually using the passkey and not leaving me wide open?

2.  Say I'm out and about with the netbook.  Am I exposed to people sniffing my ssh traffic?

3.  My desktop, the ssh server, is on a network thus having a local IP.  I understand setting up DynDNS will lock my internet IP but how does it know to connect to 192.168.1.10X on my network?

4.  Other than port forwarding, what else do I need to do?  I have UFW enabled with deny all.  Any other settings I'd have to change in my router config or UFW?

Anything else, I'm all ears.

---

### Post by CharlesA on 2009-11-13
> **The Funkbomb said:**
> Very well.  That's good news.  Thanks for the response.

I have a few more questions.  Bare with me.  I'm a little paranoid.

1.  How can I tell if my computers are secure?  I definitely plan to use passkey auth and changing my default port.  How can I tell if ssh is actually using the passkey and not leaving me wide open?

2.  Say I'm out and about with the netbook.  Am I exposed to people sniffing my ssh traffic?

3.  My desktop, the ssh server, is on a network thus having a local IP.  I understand setting up DynDNS will lock my internet IP but how does it know to connect to 192.168.1.10X on my network?

4.  Other than port forwarding, what else do I need to do?  I have UFW enabled with deny all.  Any other settings I'd have to change in my router config or UFW?

Anything else, I'm all ears.

1. Try to login with a wrong passkey or no key at all. It'll kick you out as soon as you enter the username. Check the auth.log I think. Not sure what to do other then that tbh. I locked down my firewall rules to only accept connections on the SSH port from 2 IP addresses.

2. Anything going over SSH will be encrypted, they can sniff them but won't find anything in plain text. I've tried it on my home network, but there wasn't anything I could understand.

3. You need to set port forwarding on your router to forward port 2000, for example on the WAN side to the IP of the machine that had port 2000 open.

4. You don't need to do anything outside of allow the IP address you are connecting from thru the firewall.

Hope that helps somewhat.

EDIT: If you need to connect from different IP addresses, it would probably be best to install something like DenyHosts or something similar (but I'm not sure if that works with passkeys)

---

### Post by The Funkbomb on 2009-11-13
Yeah, that's what I'm looking for.  The ability to use my home computer from any place.

I might want to sit at starbucks one day and then go to some other public wifi spot the next.

---

### Post by CharlesA on 2009-11-13
If that's the case, you can just allow traffic from any IP on that port thru the firewall, but install something like DenyHosts. There is one that uses firewall rules, but I cannot recall what it is atm.

---

