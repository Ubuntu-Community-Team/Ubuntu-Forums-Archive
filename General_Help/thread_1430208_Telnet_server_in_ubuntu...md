---
title: "Telnet server in ubuntu..?"
date: 2010-03-15
forum: General Help
---

### Post by karthick87 on 2010-03-15
How to create a telnet server in ubuntu..?My students have unix Lab by next sem and so i would like to create telnet server so that they can access it from windows..Can someone give me a detailed information on this..?Thanks in advance :)

---

### Post by mikemelen on 2010-03-15
Try to access using "ssh". Install putty application for access the linux box from windows machine. Putty is an SSH and telnet client.

For [download ]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

---

### Post by HermanAB on 2010-03-15
You may also want MinGW.

---

### Post by l4zy on 2010-03-15
If u really want to use telnet and you say to ssh.

try:

sudo apt-get install telnetd && /etc/init.d/inetd restart

after this you should be able to telnet <ip>

But you should stick in ssh. Putty has all what you need, also X11 forwarding, ofc you need X-server app for windows. But there are few good ones available @*sourceforge.net

---

