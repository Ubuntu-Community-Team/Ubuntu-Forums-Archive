---
title: "CUPS server failed business, printer won't work"
date: 2011-06-20
forum: General Help
---

### Post by minouper on 2011-06-20
Hi everyone,

I am probably going to get blasted for this statement which is a result of four days of frustration.
There are many people on here who are having problems getting their printers to work with Ubuntu.  
In my case it is version 10:04.  I have been reading and trying fixes for four days.  Nothing works.
Surely this has got to the attention of the people who know what they are doing and design these programs.  I sure don't know how to fix this, along with a lot of other users.  We are not being lazy or arrogant.  Nothing seems to work.  Surely someone in the hierarchy can put in a patch that fixes this problem.The fact that Ubuntu won't print for so many people surely must be a priority in the development of this software. So, please will one of the program developers fix this problem and send out a patch.  Thank you.  Ken

---

### Post by drdos2006 on 2011-06-20
Is the printer installed on your desktop computer or installed on a separate printer server ?
If on your desktop, what do you get when you use your browser to type : [http://localhost:631](http://localhost:631)
If on a print server, what do you get when the type :
http://<server_IP>:631 ?
Do you get the CUPS configuration screen ?

regards

---

### Post by walt.smith1960 on 2011-06-20
Which printer?  There is a (metric:)) ton of difference between printer manufacturers.  HP printers are generally plug & play.  Brother and Epson seem well supported.  N. American Canon users often have to go to European or Asian Canon sites to find software but it is usually available.  Lexmark and Dell (Lexmark with a Dell nameplate) support is spotty, to be charitable.  It does seem that Canon & Lexmark are more likely to support "business class" machines under Linux than their discount store specials.

---

### Post by minouper on 2011-06-21
> **drdos2006 said:**
> Is the printer installed on your desktop computer or installed on a separate printer server ?
If on your desktop, what do you get when you use your browser to type : [http://localhost:631](http://localhost:631)
If on a print server, what do you get when the type :
http://<server_IP>:631 ?
Do you get the CUPS configuration screen ?

regards
My printer is a Samsung laser ML-1710 and I tried : [http://localhost:631]("http://localhost:631/") .  I don't know what to do with this.

---

### Post by minouper on 2011-06-21
> **minouper said:**
> My printer is a Samsung laser ML-1710 and I tried : [http://localhost:631]("http://localhost:631/") .  I don't know what to do with this.
My printer is a Samsung ML-1710 on a desktop compauter.  When I type : [http://localhost:631]("http://localhost:631/") as a URL I get a list of information related to CUPS and printing that bears no resemblance to my problem of not being able to print.  I have read realms of this.  Thank you for replying.

---

### Post by minouper on 2011-06-21
> **drdos2006 said:**
> Is the printer installed on your desktop computer or installed on a separate printer server ?
If on your desktop, what do you get when you use your browser to type : [http://localhost:631](http://localhost:631)
If on a print server, what do you get when the type :
http://<server_IP>:631 ?
Do you get the CUPS configuration screen ?

regards
Thanks for replying.  It is a Samsung ML-1710 on a desktop.

I do not get any configuration screen.  I get a list of material related to CUPS.

---

### Post by minouper on 2011-06-21
> **walt.smith1960 said:**
> Which printer?  There is a (metric:)) ton of difference between printer manufacturers.  HP printers are generally plug & play.  Brother and Epson seem well supported.  N. American Canon users often have to go to European or Asian Canon sites to find software but it is usually available.  Lexmark and Dell (Lexmark with a Dell nameplate) support is spotty, to be charitable.  It does seem that Canon & Lexmark are more likely to support "business class" machines under Linux than their discount store specials.
Thanks.  It is a Samsung ML-170 laser printer.

---

### Post by minouper on 2011-06-21
I have kept trying to get to [B][http://localhost:631](http://localhost:631) and now I am getting:
Firefox can't establish a connection to the server at localhost:631.
so I will try again in the morning.  
[/B]

---

### Post by drdos2006 on 2011-06-21
Along the top of the CUPS screen to the right is a button which says "Printers". Click on this button to see which printer is installed.

If Firefox does not connect to localhost, it may IPv6 problem. 

Convert Firefox to IPv4 with "about:config" in the browser bar.
Click the "I'll Be Careful, I Promise" button.
In the filter bar type "IPv6".
Doubleclick and set 'network.dns.disableIPv6' to true.

Try [http://localhost:631](http://localhost:631) again.

regards

---

