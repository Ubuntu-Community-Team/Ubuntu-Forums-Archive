---
title: "Thunderbird/Evolution email not working"
date: 2011-01-30
forum: General Help
---

### Post by cblnchat on 2011-01-30
Ive tried both Evolution and Thunderbird email, and i prefer Thunderbird, and they wont work, they wont retrieve my email from my email account (yahoo email) or even find the password and username right.  Plz help, its kinda irritating. 

Ive also tried out Empathy IM  and it wont work finding my facebook chat account, i havent tried it with anything else yet but its just not connecting.  It says theres a network problem or the problems coming from facebook.   Plz help, again its kinda irritating

Thanks

---

### Post by ivanp on 2011-01-30
You should try one problem at the time, even they do seem to be related.
Is your firewall up?
```
sudo iptables --list
```

here's a link for the email setup in thunderbird. give it a try
[http://products.secureserver.net/email/email_thunderbird.htm](http://products.secureserver.net/email/email_thunderbird.htm)

---

### Post by cblnchat on 2011-01-30
Ok something strange just happened, instead of using my yahoo account i used my gmail account and it worked perfectly.  No problems at all starting or getting the emails.  Im really confused as to why gmail is working but yahoo isnt.  

Btw thanks for your help but im still kinda new to ubuntu and im not entirely sure how to use the Terminal.  What is that code supposed to do?  And the link you sent must be an old help link, or not for ubuntu because almost none of the options given in it were available for me, such as choosing POP vs SMTP.

Thanks very much for the help.

---

### Post by topher-t-mill on 2011-01-30
The non retrieval of email may be down to getting server name correct eg mail.btinternet.com or stmp.mail.yahoo.com, I had trouble with Thunderbird setting up automatically the server names, but  I was able to manually change them. also on one USB install I agreed to some security question and hey presto I could no longer access my account so I set up Evolution, which I prefer as it has a backup facility so you can install and then set up email in a jiffy.

---

### Post by Noah0504 on 2011-01-30
Doesn't Yahoo! charge for POP access to their email?

---

### Post by cblnchat on 2011-01-31
> **Noah0504 said:**
> Doesn't Yahoo! charge for POP access to their email?

Im not sure.  But once i changed the setting thunderbird gave me from POP to the other one it worked fine.  

Thank you very much.   Nice quote btw!

---

### Post by neel148 on 2011-03-09
> **ivanp said:**
> You should try one problem at the time, even they do seem to be related.
Is your firewall up?
```
sudo iptables --list
```

here's a link for the email setup in thunderbird. give it a try
[http://products.secureserver.net/email/email_thunderbird.htm](http://products.secureserver.net/email/email_thunderbird.htm)

I did it and all I got is:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

What am I supposed to do next?

Additionally my evolution mail works on the internet connection at my office premises and not at home! Even youtube-dl works at the office and not at home.

Please guide.

---

### Post by ivanp on 2011-03-09
maybe your network configuration is suited for your workplace, where you might be using a static ip, but doesn't for your house.

what's the content for your interfaces file? type
```
gedit /etc/network/interfaces
```

the following output means it will get an automatic ip, from your ISP for example.
```
auto lo
iface lo inet loopback
```

if you have something like the following, your ip config is static and that's why it works only i your office
```
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

if this is the case you should setup two network interfaces.

---

### Post by Wharf Rat on 2011-03-09
> **Noah0504 said:**
> Doesn't Yahoo! charge for POP access to their email?

Yes.    I had a similar problem until I bought an account.

---

### Post by neel148 on 2011-03-10
[QUOTE=ivanp;10543171]maybe your network configuration is suited for your workplace, where you might be using a static ip, but doesn't for your house.

what's the content for your interfaces file? type
```
gedit /etc/network/interfaces
```

the following output means it will get an automatic ip, from your ISP for example.
```
auto lo
iface lo inet loopback
```

My output is:
auto lo
iface lo inet loopback

What should I do now?

---

### Post by DAB4970 on 2011-03-11
My Thunderbird 3.1.8 is receiving msgs but not sending msgs with file attached.:(

With either my gmail or live accnts.

---

