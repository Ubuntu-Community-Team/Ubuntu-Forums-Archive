---
title: "bluetooth in commandline?"
date: 2006-04-18
forum: General Help
---

### Post by Ulokye on 2006-04-18
I have a silly problem with my Ubuntu computer, to send files to my Samsung SGH mobile I have to use gnome-obex-send/gnome-obex-server the normal obexserver obexftp obexftpd is refusing to work, very annoying. the errors I get is the following 

obexftp -b XX:XX:XX:XX:XX -t /dev/rfcomm1 -p file.jpg
Browsing XX:XX:XX:XX:XX ...
Channel: 7
Custom transport set to 'Siemens/Ericsson'
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect

this works swell on the debian machine but I can't find anything that differ in the configuration files.

---

