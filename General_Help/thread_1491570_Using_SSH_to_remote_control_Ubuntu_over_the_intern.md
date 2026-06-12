---
title: "Using SSH to remote control Ubuntu over the internet"
date: 2010-05-23
forum: General Help
---

### Post by themusicalduck on 2010-05-23
What is the easiest way to use SSH over the internet with Putty? I have a Symbian phone with Putty installed and I was hoping I might be able to run some commands remotely on my 10.04 desktop with it.

I've found a few tutorials but it seems like they deal with local networks and not over the internet.

---

### Post by Snow986 on 2010-05-23
You have to configure the LAN router to forward the port (typically 22) and then make sure your ubuntu is set to allow ssh.  The best configuration is usually no root access and only allowing your username access.  Then on putty you do 
```

ssh <username>@<external IP>

```

---

### Post by 2hot6ft2 on 2010-05-23
I know there is this one in the Tutorials & Tips section but I don't know if it will do what you want. There may be more there I just remember that one.
[HowTo: Use your mobile phone as a remote control for your Ubuntu system]("http://ubuntuforums.org/showthread.php?t=341408")

Like Snow986 said it should just be a matter of forwarding the port and using your public IP Address
:popcorn:

---

### Post by themusicalduck on 2010-05-23
When I run Putty on my phone, it asks for a host address. I tried putting both username@ipaddress and then ssh username@ipaddress but both ways it said "host name lookup failed: Unkown error (-5120)"

I don't actually have a router. I live in a flat where the internet just comes from an ethernet plug in the wall. Is it quite likely that the way the network is set up is to block the necessary port?

I could try to ring up the support for my internet provider and see if they know, but I suspect their tech support might not know what I'm talking about.

---

### Post by 2hot6ft2 on 2010-05-23
Make sure your firewall isn't blocking it and you could use a free service like dyndns.com to have a url for your IP Address.

---

### Post by themusicalduck on 2010-05-23
I might give that DynDNS a go. Although I'd quite like to see just if I can connect through my IP address to test it.

I have openssh-server and ssh installed. Are there any other packages I should have? And do I need to run a command first to start the SSH service on my desktop?

---

### Post by spikoley on 2010-05-23
Use [PortForward.com]("http://portforward.com/") to get directions on how port forward your router.  I also recommend using [DynDNS]("https://www.dyndns.com") if you do not own your own domain.  Then follow one of the guides.

---

### Post by 2hot6ft2 on 2010-05-23
> **themusicalduck said:**
> 
I have openssh-server and ssh installed. Are there any other packages I should have? And do I need to run a command first to start the SSH service on my desktop?
No the server is all you would have had to install since the client is installed by default

How to start/stop/restart the SSH Server
```
sudo /etc/init.d/ssh stop
```
(Replace stop with start for starting it again or restart to restart it)
:guitar:

---

### Post by themusicalduck on 2010-05-23
Well I have DynDNS setup and I can now ping my address and my IP address will show up.

I still can't get putty to connect. I noticed that when I try to connect, my phone doesn't display 3.5G, but instead 3G in the status bar. When I connect to the internet, it normally switches to 3.5G and refuses to download anything until it has.

I wonder if my phone is using a battery saving option that stops it using a full connection all the time and this is confusing Putty, or Putty isn't waiting long enough for the phone to connect.

EDIT: I tried connecting from a virtual XP machine using putty and it connected fine through DynDNS. So the problem seems to be with Putty not being able to get a connection on my phone.

---

### Post by Oblivion_4 on 2010-05-23
putty works slightly different then generic ssh. To use putty you only need the ip address. If putty successfully connects to a server running sshd, putty will then ask you for a username and password. The only way you won't be able to connect to your ubuntu box is if there is a firewall somewhere between you and your box.

---

### Post by themusicalduck on 2010-05-23
I worked out what was wrong. I was putting the hostname with my username and @ in front of it when you just need to put the hostname.

Thanks for the help.

---

