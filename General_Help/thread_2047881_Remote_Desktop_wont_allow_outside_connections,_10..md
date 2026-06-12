---
title: "Remote Desktop wont allow outside connections, 10.04"
date: 2012-08-25
forum: General Help
---

### Post by Demented666 on 2012-08-25
Yes I have searched and what little I have found on the issue has not helped any. 

Remote Desktop, no matter what I do, keeps giving the "Your desktop is only reachable over the local network." message. 
My router/modem are forwarding the port I have it set to. First tried it with the default 5900 port but that wont work, so I used my router/modem's default which was 20 with still no luck. 
upnp is disabled
I have tried alt + f2  gconftool -u /desktop/gnome/remote_access/network_interface but it doesn't help any

I'm out of ideas on how to get this to work so I can connect via VNC from a computer that's not on my LAN. Any help?

[IMG]http://i7.photobucket.com/albums/y298/satansfriend/Screenshot.png[/IMG]

---

### Post by Demented666 on 2012-08-25
No one has any ideas?

---

### Post by Demented666 on 2012-08-26
A full day and no one has any ideas? No wonder all of the bug reports on this issue get closed.

---

### Post by steeldriver on 2012-08-26
Sorry I'm not familiar with the GUI way of doing things - is this using x11vnc under the hood? If so and you can post the output of your x11vnc command string

```
ps -ef | grep x11vnc
```

then maybe I can help you figure it out

**Regardless I would strongly recommend that you use SSH tunneling for any remote desktop protocol that you want to transport outside of your LAN** - and if you do that then this issue will likely be moot.

---

### Post by Demented666 on 2012-08-26
No, it is with using Remote Desktop/Vino.

---

### Post by Demented666 on 2012-08-28
Someone has got to know something about this issue...

---

### Post by Demented666 on 2012-08-29
Any help?

---

### Post by dcstar on 2012-08-30
> **Demented666 said:**
> Any help?

System-Preferences-Remote Desktop

Post the screenshot here so we can see what YOU have actually done instead of vainly waiting for any useful information - then you might get somewhere.

---

### Post by Demented666 on 2012-08-30
> **dcstar said:**
> System-Preferences-Remote Desktop

Post the screenshot here so we can see what YOU have actually done instead of vainly waiting for any useful information - then you might get somewhere.
Not sure what a screenshot can help with. Not much to see, but here it is. 

[IMG]http://i7.photobucket.com/albums/y298/satansfriend/Screenshot.png[/IMG]

---

### Post by Demented666 on 2012-08-31
Still no ideas?

---

### Post by steeldriver on 2012-08-31
Some of the bug reports suggest it's actually a false warning - what actual error do you get when you try to connect?

I was unable to replicate the message on 12.04 - even after playing with all the options via dconf

Since there are very good (security) reasons for NOT using raw VNC outside of your LAN anyway, why not tunnel it via SSH? Then vino would be talking to localhost and should be happy I think?

If you are having no luck with vino you could always just install x11vnc as well

---

### Post by Demented666 on 2012-08-31
I'm getting no errors, just am not able to connect. It's not a false error. 

SSH wont work for what I'm trying to do, which is why I'm using VNC. I have no security issues to worry about.

x11vnc is also not good for me. I've tried to use it but just cannot get it to work no matter how hard I try.

I just want a way to fix this problem so I can get back to connecting like I used to be able to.

---

### Post by dcstar on 2012-08-31
> **Demented666 said:**
> Not sure what a screenshot can help with. Not much to see, but here it is. 
..........

What do think that BIG message telling you that the Remote Desktop is ONLY reachable over the local network is telling you?

Use the "Configure Network...." option.

---

### Post by IndyGunFreak on 2012-09-01
The key to this riddle, is in your screenshot.

"Your desktop is only reachable over the local network.  Others can access your computer using the address 192.1.x.x or Ishbu.local."

The most likely problem is you need to log in to your router and forward a port to your machine's IP address (192.168.1.xx...I can't read your screenshot, and I'm not sure how you can either).  I'm not sure exactly what port you need to forward, but I *think* it's either 5500 or 5900.

Once that is done, go to [http://www.whatismyip.com](http://www.whatismyip.com) and get your actual IP address, rather than your network IP address.

Then someone can connect to your machine using your IP address/port#

The way it is now, if someone is on YOUR network (ie, not outside your network) they would be able to access your machine without any problems.

You can do all that, or just avoid it, and use TeamViewer.
[http://www.teamviewer.com](http://www.teamviewer.com)

---

### Post by Demented666 on 2012-09-01
> **dcstar said:**
> What do think that BIG message telling you that the Remote Desktop is ONLY reachable over the local network is telling you?

Use the "Configure Network...." option.
You think I didn't know that? I think I kind of mentioned it in the first post, as well as the options I did to try and resolve it. 

From what I've read in all of the help threads and bug reports, upnp is supposed to be disabled as it causes more problems than it solves with this, thus why I stated I disabled it. 
> **IndyGunFreak said:**
> The key to this riddle, is in your screenshot.

"Your desktop is only reachable over the local network.  Others can access your computer using the address 192.1.x.x or Ishbu.local."

The most likely problem is you need to log in to your router and forward a port to your machine's IP address (192.168.1.xx...I can't read your screenshot, and I'm not sure how you can either).  I'm not sure exactly what port you need to forward, but I *think* it's either 5500 or 5900.

Once that is done, go to [http://www.whatismyip.com](http://www.whatismyip.com) and get your actual IP address, rather than your network IP address.

Then someone can connect to your machine using your IP address/port#

The way it is now, if someone is on YOUR network (ie, not outside your network) they would be able to access your machine without any problems.

You can do all that, or just avoid it, and use TeamViewer.
[http://www.teamviewer.com](http://www.teamviewer.com)
I already forwarded the port like I stated in the original post. 
I've tried 5500, 5900, and 20 for some silly reason. 

I've even gone as far as disabling Ubuntu's firewall temporarily to see if it was blocking connections. 


It seems to be an issue with 10.04, but someone thought it would be a good idea to remove the options tab where you can allow external connections.

---

### Post by steeldriver on 2012-09-01
I don't really understand how vino would implement LAN-specific filtering - for x11vnc the port is either open (default) or only accepts loopback connections (-localhost). To implement LAN-only connections I guess it would need to look at the netmask and/or interact with iptables somehow.

Have you tried probing the port with nmap? First from within the LAN and then from elsewhere? For example here is what I get with my local mythbuntu box running x11vnc on display :0 / port 5900

```
$ nmap -PN -p5900 192.168.1.65

Starting Nmap 5.21 ( http://nmap.org ) at 2012-09-01 10:04 EDT
Nmap scan report for 192.168.1.65
Host is up (0.0014s latency).
PORT     STATE SERVICE
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 0.33 seconds
```whereas if I probe a remote server at my workplace (which only accepts tunneled connections - I have a vnc4server session running on :5 / port 5905) I get

```
$ nmap -PN -p5905 xxx.xxx.xxx.xxx

Starting Nmap 5.21 ( http://nmap.org ) at 2012-09-01 10:00 EDT
Nmap scan report for xxx.xxx.xxx.xxx (nnn.nnn.nnn.nnn)
Host is up.
PORT     STATE    SERVICE
5905/tcp filtered unknown

Nmap done: 1 IP address (1 host up) scanned in 2.41 seconds
```Regardless, I really think your best option is to tunnel over SSH and I don't understand why you are so resistant to doing so

---

### Post by dcstar on 2012-09-01
> **Demented666 said:**
> You think I didn't know that? I think I kind of mentioned it in the first post, as well as the options I did to try and resolve it. 
.........

You - eventually - post a screenshot with the "Configure Network..." option UNTICKED and then seeming refuse to take advice to change it and still complain that things do not work!

Bother others with your intransigence.

---

### Post by Demented666 on 2012-09-02
> **dcstar said:**
> You - eventually - post a screenshot with the "Configure Network..." option UNTICKED and then seeming refuse to take advice to change it and still complain that things do not work!

Bother others with your intransigence.

"Configure network automatically to accept connections" (upnp), ticked or unticked, it changes nothing. If turning on upnp was all that was needed to solve this issue, I wouldn't have had to create this thread to try and get help.

If you don't believe me, maybe this screenshot will make you think otherwise.
[IMG]http://i7.photobucket.com/albums/y298/satansfriend/Screenshot-3.png[/IMG]


Ports 5500, 5800, and 5900 are open on my router. Everything in Vino is set as it should be. Yet no matter what, it will only allow local only connections and not external connections.

---

### Post by Demented666 on 2012-09-05
Any other ideas dcstar?

---

### Post by ingramproductions on 2012-09-05
It's VNC, and it listens on port 5900. Assuming you are using nat and are behind a firewall, simply open port 5900 and assign a nat rule.
This is an issue with your firewall

---

### Post by Demented666 on 2012-09-06
Except port 5900 IS open.

---

