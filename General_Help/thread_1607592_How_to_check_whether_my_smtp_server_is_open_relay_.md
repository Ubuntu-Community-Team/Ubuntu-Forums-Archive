---
title: "How to check whether my smtp server is open relay or not"
date: 2010-10-27
forum: General Help
---

### Post by karthick87 on 2010-10-27
I am trying  to setup my first email server..First i have configured postfix,many post says misconfiguration of postfix may make smtp open relay..So that the spammers can misuse..So how to verify my smtp server for open relay inorder to avoid  misuse..?

---

### Post by spikoley on 2010-10-27
This [site]("www.spamhelp.org/shopenrelay/") has a test to see if your server is open relay.

---

### Post by karthick87 on 2010-10-28
Tested...But got error,this is my test result...


```
**SMTP Open Relay Test**

Testing XXX.XXX.XXX.XXX on port 25... Error - could not connect to server
```

---

### Post by spikoley on 2010-10-28
Try this [one]("http://www.abuse.net/relay.html").  Maybe your server is blocking the other one.

---

### Post by karthick87 on 2010-10-28
> **spikoley said:**
> Try this [one]("http://www.abuse.net/relay.html").  Maybe your server is blocking the other one.

Tried.,

[IMG]http://verify.abuse.net/nac_ad.gif[/IMG] 

**Mail relay testing **
Connecting to 117.206.90.100 for anonymous test ... 
**Relay test result**

 Could not connect, test failed.

---

### Post by spikoley on 2010-10-28
It looks like your server is blocking their requests.  My guess is your firewall is blocking it.  You could run an nmap scan on your IP to see if your ports are open.

---

### Post by karthick87 on 2010-10-28
karthick@Ubuntu-desktop:~$ nmap XXX.XXX.XXX.XXX

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-28 11:17 IST
Interesting ports on XXX.XXX.XXX.XXX:
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
80/tcp   open  http
5900/tcp open  vnc

---

### Post by spikoley on 2010-10-28
> **getyourkarthick said:**
> karthick@Ubuntu-desktop:~$ nmap XXX.XXX.XXX.XXX

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-28 11:17 IST
Interesting ports on XXX.XXX.XXX.XXX:
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
80/tcp   open  http
5900/tcp open  vnc

Did you run that from your network or an external one?

---

### Post by karthick87 on 2010-10-28
I ran that from my network,i gave the following command in terminal

```
nmap publicaddress
```

---

### Post by JoelOl75 on 2010-10-28
Most ISP's block port 25 and 80

---

### Post by karthick87 on 2010-10-28
> **JoelOl75 said:**
> Most ISP's block port 25 and 80

How to check whether the port 25 is open or not..?

---

### Post by HermanAB on 2010-10-28
$ telnet localhost 25

If it asks for a user name and password to send mail manually, then it is not an open relay:
[http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119)

Here is another:
[http://www.askstudent.com/techtips/how-to-use-telnet-to-send-email-over-port-25-using-smtp/](http://www.askstudent.com/techtips/how-to-use-telnet-to-send-email-over-port-25-using-smtp/)

---

### Post by spikoley on 2010-10-28
> **getyourkarthick said:**
> How to check whether the port 25 is open or not..?

You would have to check with your ISP or search online for the ISP company plus SMTP.  You should be able to find a site where it lists ISPs that block SMTP traffic on port 25.

---

### Post by JoelOl75 on 2010-11-24
Or goto grc.com and use shields up to test if port 25 is open/closed/stealth

---

### Post by dcstar on 2010-11-24
> **JoelOl75 said:**
> Or goto grc.com and use shields up to test if port 25 is open/closed/stealth

Little point testing ports if someone doesn't have the appropriate port forwarding set up.

---

