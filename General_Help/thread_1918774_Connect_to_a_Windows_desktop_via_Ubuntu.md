---
title: "Connect to a Windows desktop via Ubuntu"
date: 2012-02-01
forum: General Help
---

### Post by Jake Sweeney on 2012-02-01
Hello everyone :D,

I was wondering if it was actually possible to connect to a Windows PC through Ubuntu over the Internet and not a LAN (For I know how to do this!). Can it be possible using the Terminal Server Client?

Thanks, Jake :)

---

### Post by lechien73 on 2012-02-01
Yes, it certainly is possible. Ubuntu has a Remote Desktop client, which supports RDP (Remote Desktop Protocol, used by terminal services).

You can do it in one of two (well...more, really, but I'll stick to two :D) ways:

1. The insecure way:

Forward TCP port 3389 from your Internet router to the PC, then connect using the Ubuntu Remote Desktop client to your router's public IP address.

You can use [www.whatismyip.com](www.whatismyip.com) to find out your IP address, if it's dynamic.

2. The secure way:

Set up a VPN, and first configure a VPN client on your Ubuntu box. I work remotely all the time this way.

3. (I know I said 2, but here's a 3rd) Use TeamViewer. You can download it for free for non-commercial use from [www.teamviewer.com](www.teamviewer.com). It also has an unattended version, so you don't need to have someone by the PC to initiate the connection - which you do with the standard TeamViewer application.

---

### Post by Jake Sweeney on 2012-02-02
I do like the sound of th VPN option. Unfortunately I do not know how to set up a VPN :( I don't even know what a VPN is :confused:

---

### Post by aeiah on 2012-02-02
VPN - 'Virtual Private Network'. in short, it creates a secure tunnel that effectively places your linux machine on the same LAN as the windows machine - even though there's a whole internet in between them.

VPN isn't the only thing you could use - an ssh tunnel would serve the same purpose.

once you're securely connected over the internet to the same LAN as your windows box, you can do remote desktop, mount shares etc, without those services being available to the internet at large.

---

### Post by Jake Sweeney on 2012-02-02
How do I go about setting a VPN up then? and how would the Windows PC connect to it?

---

### Post by winh8r on 2012-02-07
Have a look here:

[http://www.nomachine.com/download.php]("http://www.nomachine.com/download.php")


or take a look at  openvpn  which is in the Ubuntu repositories.


There is a lot of helpful info around which should make it fairly painless if you do it step by step!

good luck

---

### Post by 0011235813 on 2012-02-07
> **lechien73 said:**
> Yes, it certainly is possible. Ubuntu has a Remote Desktop client, which supports RDP (Remote Desktop Protocol, used by terminal services).

You can do it in one of two (well...more, really, but I'll stick to two :D) ways:

1. The insecure way:

Forward TCP port 3389 from your Internet router to the PC, then connect using the Ubuntu Remote Desktop client to your router's public IP address.

You can use [www.whatismyip.com](www.whatismyip.com) to find out your IP address, if it's dynamic.

2. The secure way:

Set up a VPN, and first configure a VPN client on your Ubuntu box. I work remotely all the time this way.
Hmmm... VPN is a bit complex for this task. 

> 3. (I know I said 2, but here's a 3rd) Use TeamViewer. You can download it for free for non-commercial use from [www.teamviewer.com](www.teamviewer.com). It also has an unattended version, so you don't need to have someone by the PC to initiate the connection - which you do with the standard TeamViewer application.
If it has anything to do with teamspeak, I wouldn't go near the thing... My organization uses it and I find it horrible.
> **Jake Sweeney said:**
> I do like the sound of th VPN option. Unfortunately I do not know how to set up a VPN :( I don't even know what a VPN is :confused:
A VPN (**V**irtual **P**rivate **N**etwork) is basically a connection between your device, your ISP (**I**nternet **S**ervice **P**rovider), the proxy server and the server hosting the site. The connection is encrypted, so information is only transferred through you, the proxy (good ones don't even keep any records) and the site server. Neither your ISP nor their ISP get any say in the matter. You could use a program called traceroute:
```
sudo apt-get install traceroute
```
and then:
```
traceroute <IP address>
``` or
```
traceroute <hostname>
```
let's say Facebook:
```
traceroute https://www.facebook.com 
```
.
> **aeiah said:**
> VPN - 'Virtual Private Network'. in short, it creates a secure tunnel that effectively places your linux machine on the same LAN as the windows machine - even though there's a whole internet in between them.

VPN isn't the only thing you could use - an ssh tunnel would serve the same purpose.

once you're securely connected over the internet to the same LAN as your windows box, you can do remote desktop, mount shares etc, without those services being available to the internet at large.

> **Jake Sweeney said:**
> How do I go about setting a VPN up then? and how would the Windows PC connect to it?

> **winh8r said:**
> Have a look here:

[http://www.nomachine.com/download.php]("http://www.nomachine.com/download.php")


or take a look at  openvpn  which is in the Ubuntu repositories.


There is a lot of helpful info around which should make it fairly painless if you do it step by step!

good luck

Really this sounds like the thing for ssh and virtualizing.

---

### Post by xianbei on 2012-02-07
I've had great luck with openvpn and rdesktop. It can be tricky to set up the cert, but once done you can install this and create a vpn connection.

Once the VPN is established you can use rdesktop to connect using  the Windows computer's name, i.e. 

```
sudo service openvpn start
password stuff...

rdesktop -f MyWindowsComputer
```

good luck!

---

