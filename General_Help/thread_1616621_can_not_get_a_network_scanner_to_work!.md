---
title: "can not get a network scanner to work!"
date: 2010-11-08
forum: General Help
---

### Post by unebaguettesvp on 2010-11-08
Hi-

I'm trying to get a network scanner to function. I've been following the guides here:

[http://ubuntuforums.org/showthread.php?t=1519201](http://ubuntuforums.org/showthread.php?t=1519201)
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

And I think I am just misunderstanding something.

1. The scanner is properly functioning on the server side.

2. Both, the client and the server, have the package sane-utils installed.

3. I changed /etc/default/saned on the server to RUN=yes (that was easy!)

4. Editing /etc/sane.d/saned.conf is what I think I'm getting confused on. The internal IP address of the server is 192.168.1.102 and the subnet mask is 255.255.255.0. The internal IP address of the client is 192.168.1.103. So, what do I put there? Is 192.168.1.0/24 correct? That didn't work!

5. Also, editing /etc/sane.d/net.conf on the client is confusing me too! What IP address should go there? Can I put the server name? What is the correct syntax?

6. I added saned to the correct group, lp. I made sure that the scanner was owned by the correct group by doing these commands:
sane-find-scanner
AND
ls -al /dev/bus/usb/XXX/XXX
The group was lp.

7. Yes, the server was restarted! A hard restart!

Any help would VERY much appreciated!

---

### Post by unebaguettesvp on 2010-11-08
I should also mention that both computers are using ubuntu 10.10.

---

### Post by unebaguettesvp on 2010-11-08
sorry for the bump! any help please?

---

### Post by krupintupple on 2010-11-08
i used to be a CSR for a fairly large printer company that also dealt with scanners. our rule #1 was that network scanning might or might not work, there's zero guarantee. sucks i know, but i wish you the best on your search.

---

### Post by unebaguettesvp on 2010-11-09
got it to work!

i edited /etc/sane.d/saned.conf on the server back to 192.168.1.0/24

then i changed /etc/sane.d/net.conf on the client to the ip address of the server.

then i ran on the server:
sudo dpkg-reconfigure sane-utils

i answered one question, whether or not i wanted it to be a standalone server. i clicked yes and that was it! it started working! i have no idea why!

---

