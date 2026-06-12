---
title: "Need assistence creating web server."
date: 2010-11-19
forum: General Help
---

### Post by cgroza on 2010-11-19
Hello, I am trying to set up a web server. I have my site ready in /var/www and if i go to 192.168.1.100 I can browse with no problems. I give this IP to my friends and they either go to other page , either it says "Is taking too long to respond". If I acces it from my other computer, wich shares the router with the host, it works ok .I need some guidance to get my site visible on the WWW. How do I do that?
I am running apache.

Thank you.

---

### Post by lykwydchykyn on 2010-11-19
192.168.1.100 is what we call a "private IP" -- it is only for the private network, not reachable from the Internet.

Your router and/or modem will have a "public IP", which is the address that people can get to from the internet, but you have to tell the router and/or modem to forward incoming web traffic to the server.  This is called "port forwarding".

If you go to your router or modem's setup, you should see some interface for forwarding ports.  Basically you want to forward port 80 (http) to your server's address (192.168.1.100).

If you're on a standard consumer internet connection, your IP will probably change periodically.  The best way to solve this problem is to set up a dynamic DNS so that they can just use a URL.

This should help: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by cgroza on 2010-11-19
Ok, that explained a lot. Thanks. I will try and then post back.

---

### Post by cgroza on 2010-11-19
OK, found it. What range should I set? 80-80?

This is what it looks like now:


[SIZE=2]**Local IP Address**[/SIZE] [SIZE=2]**Protocol**[/SIZE] [SIZE=2]**Port Range**[/SIZE] [SIZE=2]**Comment**[/SIZE] [SIZE=2]**Select**[/SIZE] [SIZE=2]192.168.1.100[/SIZE] [SIZE=2]TCP+UDP[/SIZE] [SIZE=2]80[/SIZE] [SIZE=2]webserver

Is it ok?
[/SIZE]

---

### Post by cgroza on 2010-11-19
My friend says it does not work. He enters 192.168.1.100 and its being taken to some other page.

---

### Post by axept on 2010-11-19
You cant use a "private IP", you have to use the public IP. I think.

192.168.1.* is used by the modem/router to the different connected hardware on your local network.

---

### Post by cgroza on 2010-11-19
My forward settings:
```
Local IP:               port       Protocol
192.168.1.100       80           Both
```If I enter my public IP there it says its Invalid. If my friend enters my public IP in his browser it says it could not connect. 
I am new in all this. Maybe someone has enough patience to explain me?

---

### Post by CharlesA on 2010-11-19
YOu use the private IP on yer router, but the public ip is used for accessing that machine from outside yer local network.

---

### Post by cgroza on 2010-11-19
Yes, I got it... it still does not work! My public IP is not accepted in the port forwarding utility.
It says : 
**Invalid IP address! It should be set within the current subnet.**

---

### Post by CharlesA on 2010-11-19
You don't use the public ip in the port forwarding utility, you use the private ip.

[http://portforward.com/](http://portforward.com/)

---

### Post by joshruehlig on 2010-11-19
How I do is make sure my router ports out port 80 for my server, in this case port 80 for 192.168.1.100.
You then findout your public ip [http://www.whatismyip.com/](http://www.whatismyip.com/)
Your friend just types in your public ip and accesses your webserver. So basically port your server's port 80 out.

You can also use a dynamic dns on your server or your your router (recommended) so that your website is always the same name. Cause your public ip most likely changes.

dyndns.com

---

### Post by cgroza on 2010-11-19
I did so... But my friend still can not connect. It gives the error: Could not connect to 
[B]173.248.192.114. 
[/B]

Maybe skype is blocking the port because I heared that skype is usng port 80?

---

### Post by CharlesA on 2010-11-19
Run shieldsup to see if that port is actually open or not.

---

### Post by cgroza on 2010-11-19
It says its STEALTH!

---

### Post by CharlesA on 2010-11-19
Could be yer ISP is blocking that port. Try using port 8080 instead of 80 and see what happens.

Public port would be 8080, private port would be set to 80.

---

### Post by cgroza on 2010-11-19
Still no. What could be the problem?

---

### Post by CharlesA on 2010-11-19
> **cgroza said:**
> Still no. What could be the problem?
ISP could be blocking that port. Try a port above 10,000. 80000 or something like that.

If it's still not working, make sure that yer port forwarding is set up correctly. You are using the private IP address there, right?

---

### Post by SeijiSensei on 2010-11-19
> **CharlesA said:**
> ISP could be blocking that port. Try a port above 10,000. 80000 or something like that.

Charles was probably having a rare mental lapse :D  The highest port you can use is 65535 (2^16-1).  Ports below 1024 belong to the root user, so they're usually off limits as well.  Any random four- or five-digit number between 1024 and 65535 is fine.  I usually choose numbers in the 20000-50000 range.  I sometimes use mnemonics based on the location of the numbers and letters on a phone so I can "spell" out unusual high ports if I need to remember them.  For instance, "abcde" translates to "22233".

---

### Post by CharlesA on 2010-11-19
Lol. I was trying to pick a random (high) number.

Good catch. ;)

---

### Post by cgroza on 2010-11-20
> **CharlesA said:**
> ISP could be blocking that port. Try a port above 10,000. 80000 or something like that.

If it's still not working, make sure that yer port forwarding is set up correctly. You are using the private IP address there, right?

Yes, I use my private IP for forwarding.

---

### Post by cgroza on 2010-11-20
I can't test it right now. I'll post back later.

---

