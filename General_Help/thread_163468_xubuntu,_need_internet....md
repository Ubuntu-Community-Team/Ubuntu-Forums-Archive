---
title: "xubuntu, need internet..."
date: 2006-04-20
forum: General Help
---

### Post by orlox on 2006-04-20
Well, I have a fresh xubuntu installlation on my machine, and i'm trying to connect to the internet with dialup. I tried pppconfig, made a connction called provider with all I needed, and then typed pon on a terminal. The modem dials, but after it finishes, i don't have a connection...how can I get this connection working?

---

### Post by zxee on 2006-04-21
Hi, There are fewer and fewer of us using analog modems. Have you tried 'pon' with sudo?
A couple of things to check;  Is your user a member of the dip and or dialout group?  In /etc/chatsripts/ppp0 make sure the timeout = 75 or greater. You also may need to create a wvdial.conf [Dialer Provider*]  with all the required info see man wvdial.conf. If you do configure wvdial you can try to start your connection from a terminal with 'wvdial provider*' and if it fails to establish a connection do a search on the output or post that here. 
*or any name you want to use for your isp
Hope that helps.

---

### Post by StefanoCole on 2006-04-21
Hello orlox, after typing "sudo pon", if you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum. Maybe, reading the log message someone will be able to help you.

Stefano

---

