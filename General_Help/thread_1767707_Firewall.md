---
title: "Firewall"
date: 2011-05-26
forum: General Help
---

### Post by gpsvn on 2011-05-26
I posted a query on Java and linuxinstalledfromhdd kindly provides a link to a blog, where one could find lot of tips.

May be I went a bit too far, configuring up my firewall with the following rules added without knowing what they do to my laptop.

sudo ufw deny 5353/udp
sudo ufw deny 5900/tcp
sudo ufw deny 22
sudo ufw deny 25/tcp
sudo ufw deny 135,139,445/tcp
sudo ufw deny 137,138/udp
sudo ufw deny 110
sudo ufw deny 2049
sudo ufw deny 143
sudo ufw deny 21/tcp

I used to be able to print on a printer connects to Windows PC on my network. Since I added firewall rules, I can not print anymore. I have to turn off my firewall in order to print a page.

Please advise which rules should I remove to connect to other PC on my home network.

If possible, would you please explain what each rule does.

Thank you,
gpsvn

---

### Post by duke.tim on 2011-05-26
You should do a google search on ports 
which is what you are choosing to deny

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

21 ftp file transfer protocol 
22 ssh	The Secure Shell (SSH) Protocol
25 smpt	Simple Mail Transfer
110 pop3 Post Office Protocol
135 epmap	DCE endpoint resolution
137 Netbios-ns		Net-Bios Name Service
138 netbios-dgm		Net-Bios Datagram Service
139 net-Bios-ssn	Net-Bios session service
143 IMAP Internet Message Access Protocol
445 UAAC	UAAC Ptotocol
2049 nft Network file system - Sun Microsystems
5900 Remote Framebuffer
5353 mdns	Mulicast DNS

You can disable almost everything...but it really depends on your network setup and what you plan to do on the net
If you use a mail service re-enable
25,110,143

If you use ftp (a.k.a. downloading files) re-enable it

and just to be on the safe side
5353
[http://en.wikipedia.org/wiki/Zero_configuration_networking](http://en.wikipedia.org/wiki/Zero_configuration_networking)

---

### Post by seawolf167 on 2011-05-26
Ubuntu in it's default state doesn't have any programs listening on any ports which is why it doesn't come with a firewall enabled with rules. Once you start adding programs that listen on certain ports (especially in a server enviroment) you'll want to add and enable a firewall.

I think the easiest way for you to manage your firewall and see what rules you have setup is to use *gufw* (a GUI for *ufw*)

```
sudo apt-get install gufw
```

---

### Post by gpsvn on 2011-06-10
Thank you all for the responses. I don't really understand them so I removed all the rules, back to square one.

---

