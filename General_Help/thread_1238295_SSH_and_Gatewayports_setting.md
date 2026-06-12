---
title: "SSH and Gatewayports setting"
date: 2009-08-12
forum: General Help
---

### Post by MrGrey1 on 2009-08-12
I have had ssh setup and working for sometime. 
I have recently setup an ftp server on my LAN. 
I'm looking to tunnel the connection from outside my network through my ssh machine to my ftp server on a different machine.
From what I gather all I need do is set 'Gatewayports yes' in sshd_config.
Can someone please confirm that the 'Gatewayports' setting in sshd_config is all I need to do to allow the ssh server to relay a connection to another machine on the internal network?

---

### Post by bear24rw on 2009-08-12
hm im not sure about the gateway stuff but this is how i would do it..
im going to assume your on a windows machine outside the network

install putty and filezilla

in putty go to tunnelling add port 1234 (can be any number) and set to dynamic click add then go back to main tab and enter your ip for your home, log into your server

than in filezilla go to prefrences and set it to use a socks proxy pointing to 127.0.0.1 and port 1234

you should then be able to enter the local ip of your ftp server and connect to it..

---

