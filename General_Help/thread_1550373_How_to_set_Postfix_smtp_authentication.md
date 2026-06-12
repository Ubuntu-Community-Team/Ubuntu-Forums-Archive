---
title: "How to set Postfix smtp authentication ?"
date: 2010-08-11
forum: General Help
---

### Post by solidussnake on 2010-08-11
I have built up my mail server successfully,
can send(smtp) and receive(POP and IMAP) with my domain.
Howver, I want my smtp to be authenticated by username and password.

[IMG]http://i171.photobucket.com/albums/u312/solidussnakex/Untitled-1.gif[/IMG]

Now I can connect to my smtp without any anthenication(as below).
But I want it to check username and password(as above).

[IMG]http://i171.photobucket.com/albums/u312/solidussnakex/Untitled-2.gif[/IMG]



Here are the setting I made after a fresh ubuntu 10.04 installation.

sudo useradd [my_name]
sudo passwd [my_name]
dig mx [mydomain.com]
sudo apt-get install postfix
sudo apt-get install mailutils
sudo postconf -e "home_mailbox = Maildir/"
sudo postconf -e "mydestination = localhost.localdomain, localhost, [mydomain.com]"
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.1.0/24"
sudo postconf -e "inet_interfaces = all"
sudo postconf -e "inet_protocols = all"
sudo  /etc/init.d/postfix stop
sudo  /etc/init.d/postfix start

set godaddy domain directed to [my IP]
set router port fowarding at port 25, 110, 143 to my server


What should I do next ?

---

