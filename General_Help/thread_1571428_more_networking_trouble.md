---
title: "more networking trouble"
date: 2010-09-09
forum: General Help
---

### Post by unbuntunewb on 2010-09-09
I have been trying to get this one to work for a LONG time now and just cant seem to figure it out.

I have an ipod touch with openssh on it that I can connect via wifi to my home network, I will call that device A.
I have a laptop (device B) that I want to use to connect via ssh socks proxy to device A for security when im not home and on another network.
I have a desktop (device C)  that I want to use to connect via ssh socks proxy to device A for security at home.

basically this all revolves around my jailbroken, openssh-enabled ipod touch.

I am not a computer admin, I am a tech enthusiast who values my privacy and this project I just cant seem to beat. I am in no way an expert so please use use teeny tiny words.

I have been having much trouble with the "user@domain.com" that appears to be critical in the process. I was under the impression a domain was something you got when you buy a website, my brother however informed me that in this case a domain is something you create at home for networking and apparently ssh socks proxies.

question 1 - how do I create the "user@domain.com" ?
question 2 - how do I have device B piped into device A for use when I am not at home?
question 3 - how do I use device C piped into device A for added security at home?

I have a wirless D lynksys router, I dont know if I need to foward ports. Also I use foxy proxy to connect to my proxies so I would rather use that to configure the proxy as opposed to the proxy options built into firefox.;)

Someone please help!


ps - when I do this: -ssh -D9999 (ip of device A)     -   I am greeted with a "enter password for device A" which I dont know, I have manually added all the passwords to device A so I dont know the problem I know all the passwords, if I use putty it will connect as far as I can tell but when I configure foxy proxy to use that connection I get no internet.

---

### Post by btindie on 2010-09-09
"domain.com" or more precisely host.mydomain.com is used to identify the host to connect to. This is then resolved through DNS to get the hosts IP address. You can buy a domain or use the IP address in place of the FQDN (Fully Qualified Domain Name). There are services offered for free that allow you to have a sub domain of someone elses domain. Off of the top of my head, once such service is no-ip.com. If you're on a dynamic IP address they offer some software that you can run on one of your boxes and that will periodically up your IP address that is registered with your hostname. You can then use that instead of your IP address to connect to your box behind your router.
 
Why are you trying to connect via a SSH SOCKS proxy?
 
If you want to access your internal network from the internet then I'd just setup port forwarding on your router to forward a port, say 2222, to your ipod on port 22.
 
I'm not familiar with a "jailbroken, openssh-enabled ipod touch", presumably this is running it's own SSH server? If that's the case then you should have a username to access it. This is the "user" you'd use to SSH in to it.
 
2) When you want to connect your laptop over the internet to your ipod you'd ssh into the public IP address of your router on the port you setup to forward to your ipod.
> ssh -p 2222 root[EMAIL="root@myrouter.no-ip.com"]@myrouter.no-ip.com[/EMAIL]
 
3) This is very similar to the above except you'd be connecting directly to your ipod and not 'via' your port forwarding router, you'd use either the local IP address or local hostname if you've got it setup.
> ssh root[EMAIL="root@192.168.0.3"]@192.168.0.3[/EMAIL]
 
 
What is it you're trying to achieve? - access the muic on your ipod?? You could use SSHFS to remotely mount the filesystem.
 
If you get the above working then you should be able to customise it to your specific needs.

---

### Post by unbuntunewb on 2010-09-09
Thank you so much that explained a lot, I will give it another go. I have managed to access my music through ssh already and its great but I figured that out by accident trying to create a ssh socks proxy. Also to answer your question I am not aiming to do anything specific, I just like tinkering with things, however I enjoy such projects and the idea of surfing encrypted is appealing to me. To answer your second question a jailbroken ipod is an ipod thats unlocked to third party stuff, including openSHH.

heres some more on the jailbroken ipod 
https://encrypted.google.com/search?hl=en&safe=off&client=firefox&hs=LvU&rls={moz:distributionID}:{moz:locale}:{moz:official}&defl=en&q=define:Jailbreaking&sa=X&ei=q1SJTMjiNoT6lwfzxcjvCw&ved=0CBIQkAE

[http://www.crunchgear.com/2010/07/26/now-legal-in-the-u-s-jailbreaking-your-iphone-ripping-a-dvd-for-educational-purposes/](http://www.crunchgear.com/2010/07/26/now-legal-in-the-u-s-jailbreaking-your-iphone-ripping-a-dvd-for-educational-purposes/)

my overall objective is increased online security through anonymity, when I check the IP on my ipod its different than the IP of my home computer even if we are both on the same network (my home network). I was hoping to use my laptop (say at starbucks) and ssh into my ipod and use that to go online through my home network instead of ssh-ing into my home desktop and going online from there. I wanted to use the ipod becuase of the at least perieved anonymity increase.  I would like to be on my home network but under an IP that was not associated directly with my home.

---

### Post by unbuntunewb on 2010-09-09
update!


this happened 
nunya@nunya-desktop:~$ ssh root@(my ipods wifi IP)
root@(my ipods wifi ip) password: 
iPod-touch:~ root# 

so I did this! now how do I turn this into a proxy where I can browse the net from within an ecrypted tunnel?

---

### Post by btindie on 2010-09-09
Well done, you got SSH working on an ipod!
 
> now how do I turn this into a proxy where I can browse the net from within an ecrypted tunnel?
 
I'm not quite with you on that one... Do you want your ipod to be a proxy server??
 
Does one of these answer your question? [http://www.google.co.uk/search?q=ssh+socks+proxy](http://www.google.co.uk/search?q=ssh+socks+proxy)

---

### Post by unbuntunewb on 2010-09-09
yes, I am trying to make my ipod a proxy, are there any real benefits to this? I want to do this because when I check the IP of my ipod when im connected to my home network its not the same one I use when I am on my desktop/laptop. Also when I check my ip on whatismyipaddress.com when im on my desktop/laptop everything about my physical location is public info. I dont like that. When I check my ipods IP on that same site I get this. 

[COLOR=red][I]This is a [private IP address]("http://whatismyipaddress.com/private-ip") and cannot be traced.
[/I][/COLOR]Hostname (my ipod wifi ip)
ISP:
Organization:
Proxy:None detectedType:UnknownAssignment:[Static IP]("http://whatismyipaddress.com/dynamic-static")

as opposed to this

ISP:Comcast Cable                     Organization:Comcast Cable                     Connection:[Broadband]("http://whatismyipaddress.com/broadband")                                          Proxy: 
                                        City: (my city)
                    Region (my state)
                    Country:United States [IMG]http://whatismyipaddress.com/images/flags/us.png[/IMG]

---

### Post by btindie on 2010-09-09
Ok, I see!
 
Well using your ipod as a proxy in this case isn't going to help.
 
Your Laptop/Desktop/ipod all have private non-routable IP addresses, when they establish a connection to the internet your Linksys router performs NAT on your devices IP address. Thereby making it appear as if the request originated from your router. HTTP is a layer on top of that and in the HTTP request the client identifies it's local (private IP address). When you connect to whatsmyip their server can see your public address as that's what makes the connection. I'm not sure why it's only seeing the private IP address on your ipod, it may have something to do with the software, but it will know the public address of your Linksys router if that is what the connection is going through.
 
The only way you'd be able to hide your 'identity' when browsing the web is to use a public / open proxy on the internet that presents another IP address instead of the public routable IP address on your Linksys router.

---

### Post by unbuntunewb on 2010-09-09
so I suppose ditching the ipod idea would be the way to go, with that in mind could I have my laptop tunnel its way remotely to my desktop? in a secure encrypted tunnel? from what I understand I need to do this:

[http://www.no-ip.com/support/guides/routers/linksys.html](http://www.no-ip.com/support/guides/routers/linksys.html)

is that right?

---

### Post by btindie on 2010-09-10
Yes that's correct, that would then allow you to connect to your desktop computer via any computer on the internet. Using the same method you could run your own webserver on it if you desired.
 
An alternative method that would achieve a similar result would be to create a VPN to your Linksys if it supports it. The way that would work is on your laptop, when it is connected via the internet, would establish a VPN tunnel to the linksys using it's public IP address. You'd then SSH into your desktop using the internal private IP address as through the VPN your laptop would already be part of the internal network.
 
The advantage of this is if you have a few internal devices that you want to be able to access you don't have to set up *n* port forwarding rules to be able to access them from the internet. Through the VPN it makes it appear as if you're on the internal network.

---

### Post by unbuntunewb on 2010-09-10
Thank you so much you have been very helpful. As far as security goes within the tunnels what method would be more secure (vpn as opposed to ssh socks) I started this whole project with the expectation that my browsing would be encrypted, if I were to use a vpn would my browing be encrypted? as far as I know an ssh socks proxy is encrypted so im leaning towards that however I am open to suggestion if vpn does indeed create a more secure online experience.

this whole thing was started after I watched this video by telecomix
[http://www.youtube.com/v/g8Hw1tqiJzY](http://www.youtube.com/v/g8Hw1tqiJzY)

that is what im trying to achieve (although for much less dramatic reasons than discussed in that video)

---

### Post by btindie on 2010-09-15
From watching the video on youtube that you provided the link for I got a better idea of what it is you're trying to implement. The method given in the video is more for getting around censorship in countries where they block access to certain websites - you have a Linux box somewhere that doesn't have those restrictions then tunnel your browsing via it. It's only encrypted up to the point of the Linux box, beyond that it's just a normal unencrypted session. Is this really what you want to achieve?
 
A VPN would provide an encrypted connection from your laptop on the internet back to your home network allowing you to access the internet in the same way as if you were at home. You would however only need the one VPN connection open to access all the resources on that network. You could then run a normal proxy server(squid) on your Linux box at home to access the internet via your laptop on the internet.
 
Laptop ---> VPN (over internet - encrypted) ---> Home Network ---> Desktop Proxy ---> Internet (unencrypted) ---> Website
 
In the above example the request would appear to come from your Desktop. If that's all you want to do then you could just use the SSH SOCKS proxy method described in the video.
 
This has nothing to do with securing all HTTP communications to websites for browsing. It's a method to overcome certain restrictions some countries place on browsing by blocking certain IP address ranges.

---

