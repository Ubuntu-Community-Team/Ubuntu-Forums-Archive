---
title: "SSH vs FTP on Wifi Network - Speed?"
date: 2009-11-15
forum: General Help
---

### Post by KingBongo on 2009-11-15
Hi. I have been setting up a local network. All units use 802.11g for communication: OS X 10.6 (Mac), Ubuntu 9.10 (PC) and an Apple AirPort Router.

Here is the issue. Although I read everywhere that FTP should be faster than SSH, I cannot confirm that in my own tests. So far, it seems like SSH is actually faster than FTP! Why? It should be noted that I have only been transferring files with the Mac as Server and Ubuntu as client, i.e. logging into the mac from Ubuntu and transferring files TO Ubuntu.

Is there something wrong with my setup? It's so easy so I cannot see how. The applications I use are the following,

SSH: OS X - Built in, Ubuntu - Connect To Server (Built in)  
FTP: OS X - pureFTPd, Ubuntu - Connect To Server (Built in)

Also, what speeds should I be expecting from my network? So far I have maxed out at 550 KB/s (SSH) and often the speed is half of that. It should be noted that FTP and SSH are close in terms of speed, but the latter seems to have the edge.

Why is SSH faster than FTP and what speeds should I be expecting?

PS. If SSH is actually even remotely as fast as FTP, for security reasons I will be using SSH.

---

### Post by efflandt on 2009-11-15
I noticed that a long time ago when I had a WAP11 that choked when using WEP to half of its open system speed.  When I used scp I could typically get transfer speeds with WEP as fast as open system ftp.

ssh/scp is more secure because it is encrypted, but it can also use compression (maybe by default).  The compression is what can make it faster than ftp, especially when transferring ordinary uncompressed files.  Of course already compressed files (gz, zip, etc.) may not be able to be compressed much more and may not transfer as fast.

Compressed transfer can more than make up for the time it takes to crypt/decrypt the data.  So you win both ways using ssh/scp/sftp, more secure and possibly faster than ftp.

---

### Post by Slim Odds on 2009-11-15
> **efflandt said:**
> Compressed transfer can more than make up for the time it takes to crypt/decrypt the data.

If you have a fast CPU. Which most are these days....

---

### Post by MaxIBoy on 2009-11-15
If you have a slow CPU, SSH should trivially be slower. A faster CPU, and SSH may have a small advantage.

But the real bottleneck is the network itself, no getting around that.

---

### Post by XCan on 2009-11-15
I think the compression is only enabled by explicitly giving the -C flag. But perhaps the built in function in nautilus does just that?

---

### Post by KingBongo on 2009-11-15
Ahhhh. Thank you guys! So it can in fact be the case that SSH IS faster! And yes, I have i fairly fast processor. It is a single-core, but clocking at 3.06GHz. It has Hyper Threading as well, but I don't know if that is useful. I also have 2GB of RAM, but again, I don't know if that is an advantage or not. For sure my network is the main bottleneck.

Thank you! I thought that I was doing something stupid over here, but maybe not.

---

### Post by zebtonson on 2011-07-03
Change of ssh cipher I found also gives ssh a big boost. Try -C -c arcfour to enable compression and a high bandwidth cipher. 

E.g. 

```
 scp -C -c arcfour username@remotehost:./somefile ./ 
```

---

### Post by daxbau on 2011-07-03
in all cases remember just that you need calculating power to encrypt the transfer.

if you have a wpa2 wireless network your chip of your networkcard should take the encryption. but if you use ssh or something else the packets of your data have to be encrypted by the server and decrypted by the client as well. therefore you have a lot more power to invest.

btw. why are you using ssh in your encrypted wireless network?

I use only ssh or a vpn tunnel to connect via internet to my pc's. otherwise i use the encrypted wireless network. for unencrypted datatransfer.

i.e.:

connectet from samsung galaxy s II to my hp-compaq 8510w ubuntu vsftpserver:
1. port 21 ftp; 2800 kbit/s, cpu 1 core 100%
2. port 22 sftp; 250 kbit/s, cpu 1 core 100%

theres still no open source software to do the encryption on more than one core.

kind reguards

---

### Post by prodigy_ on 2011-07-03
I don't see any practical use for non-public FTP these days. And since it's local network, you should consider using regular Samba shares.

---

