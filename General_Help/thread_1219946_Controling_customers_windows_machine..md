---
title: "Controling customers windows machine."
date: 2009-07-22
forum: General Help
---

### Post by avacomputers on 2009-07-22
Hey Guys and Gals, I do windows tech support and I need something to easily control customers windows machine. While I had Windows, I used Showmypc.com because it was very simple for customers to understand.

Any suggestions?

---

### Post by Cheesemill on 2009-07-22
Terminal Server client is installed on a default Ubuntu installation.
You just need to enable Remote Desktop on the client machines and your ready to go.

---

### Post by avacomputers on 2009-07-22
> **Cheesemill said:**
> Terminal Server client is installed on a default Ubuntu installation.
You just need to enable Remote Desktop on the client machines and your ready to go.

What is my customer knows nothing about Ip addresses or ports of any of that stuff?

---

### Post by avacomputers on 2009-07-22
Anyone?

---

### Post by credobyte on 2009-07-22
> **avacomputers said:**
> What is my customer knows nothing about Ip addresses or ports of any of that stuff?

They don't need to know anything about IP addresses or ports ! All they need to do is to enable Remote Desktop ( which is already there .. check Firewall Settings ). Yes, you'll need an IP, tough, they can open [http://www.ip-adress.com/](http://www.ip-adress.com/) and tell it to you in the matter of seconds :)

---

### Post by t4thfavor on 2009-07-22
Actually, they do. It appears he does remote support from the not so safe ssied of the "customers" firewall. Things like gotomypc are proxy based, therefore needing no firewall configuration. tsclient is not, so you will need to forward port 3389, which, if I know the users, they think is an address on their street.

Im not sure of an alternative, perhaps virtual XP to the rescue again, until someone fixes the activex requirement of most remote administration websites.

---

### Post by avacomputers on 2009-07-22
> **t4thfavor said:**
> Actually, they do. It appears he does remote support from the not so safe ssied of the "customers" firewall. Things like gotomypc are proxy based, therefore needing no firewall configuration. tsclient is not, so you will need to forward port 3389, which, if I know the users, they think is an address on their street.

Im not sure of an alternative, perhaps virtual XP to the rescue again, until someone fixes the activex requirement of most remote administration websites.

I usually use showmypc, which is free.

---

### Post by dehcbad25 on 2009-07-22
I use logmein.com
It is similar to showmypc, and it works on firefox on Ubuntu. The ActiveX client is better, but it works without too.
However, you will probably benefit more and love ultravnc sc. I use it as a backup for the PCs that do not have the logmein client installed (I also use ITreach subscription)
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)
it is not difficult to create your own client with your logo and text. In a couple of hours you could have the client created that can be emailed to remote customers (mine is 300KB), or put it as a download from the web site :)

---

### Post by avacomputers on 2009-07-22
> **dehcbad25 said:**
> I use logmein.com
It is similar to showmypc, and it works on firefox on Ubuntu. The ActiveX client is better, but it works without too.
However, you will probably benefit more and love ultravnc sc. I use it as a backup for the PCs that do not have the logmein client installed (I also use ITreach subscription)
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)
it is not difficult to create your own client with your logo and text. In a couple of hours you could have the client created that can be emailed to remote customers (mine is 300KB), or put it as a download from the web site :)

Thank YOu, great options. I have used logmein in the past, I just don't want to pay for IT Reach, but guess I have no choice right now.

---

