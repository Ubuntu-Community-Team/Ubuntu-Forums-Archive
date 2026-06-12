---
title: "How can I telnet to my ubuntu machine"
date: 2006-05-04
forum: General Help
---

### Post by SwaroopKunduru on 2006-05-04
Hi All,

I wanted to access my Linux via Telnet. How can I configure for telnet to Ubuntu from windows.

Regards,

Swaroop Kunduru

---

### Post by Slim Odds on 2006-05-04
[QUOTE=SwaroopKunduru]Hi All,

I wanted to access my Linux via Telnet. How can I configure for telnet to Ubuntu from windows.

Regards,

Swaroop Kunduru[/QUOTE]

You would be much better off using ssh. 

sudo apt-get install openssh-server

---

### Post by nanotube on 2006-05-04
yea, ssh is like telnet, only secure. :)

---

### Post by harisund on 2006-05-04
So did you make up your mind? You prefer to go with telnet still?

---

### Post by dusanyu on 2006-05-04
i would recomend ssh as well but you will need a ssh client for windows putty [http://www.putty.nl/download.html](http://www.putty.nl/download.html) is a good solid ssh client for windows

---

### Post by dcstar on 2006-05-04
[QUOTE=SwaroopKunduru]Hi All,

I wanted to access my Linux via Telnet. How can I configure for telnet to Ubuntu from windows.
.......[/QUOTE]
The Telnet daemon is not installed by default, go into Synaptic and install it (or preferably the other more secure alternatives).

---

### Post by Slim Odds on 2006-05-04
[QUOTE=dusanyu]i would recomend ssh as well but you will need a ssh client for windows putty [http://www.putty.nl/download.html](http://www.putty.nl/download.html) is a good solid ssh client for windows[/QUOTE]

When I have to use a windose machine, I install cygwin ([http://www.cygwin.com]("http://www.cygwin.com")) :idea: 

Then you can get ssh, bash, X, and tons of other great things that almost make you forget that you're not on a linux machine.

---

### Post by mravenca on 2006-11-07
Actually, this thread is exactly about my problem. I have more computers in my network and want to be able to access Xubuntu machine from the others. I think almost everything I need was said here. 
Please, how do I set up the ssh? Sure I need setting up users, passwords, etc.. but I don't know where. Maybe it is important to say that I do not have X window installed. I also do not have any file manager. I will probably have to edit some configuration files, but do not know how. 
Anyway, how do I configure or find out the ip address of the XUbuntu machine? It gets the ip address from DHCP server probably, I did not setup anything and the internet connection works.

---

### Post by Christmas on 2006-11-07
One example of accessing a web page on a machine with apache installed would be:
```
christmas@floyd:~$ telnet 89.39.4.39 80
Trying 89.39.4.39...
Connected to 89.39.4.39.
Escape character is '^]'.
GET /scripts/scripts.php
<html>
        <head>
                <title>Linux Scripts and Plugins</title>
        </head>
        <body>
                <table align = "center" cellpadding = "0" cellspacing = "0" nowrap>
                        <tr height = "2">
                                <td width = "5%">
                                </td>
                                <td width = "2" bgcolor = "navy">
...
```
So bassically you specify the host/IP of the machine you want to connect to and a port. Various ports are open for various services, and you use some special words to get something from the remote machine, in the above example "GET". Some google searching should turn up how to use telnet exactly.

---

### Post by mravenca on 2006-11-07
OK, this helped me understand it a little bit. Will I be able to execute all commands as I was directly loggen on the Ubuntu machine?

Anyway, I have heard about cygwin/x. 

Which one do you think is better for me? And will I have to have X window installed on the Ubuntu machine to use cygwin/x?

Thanks

---

### Post by nanotube on 2006-11-10
> **mravenca said:**
> OK, this helped me understand it a little bit. Will I be able to execute all commands as I was directly loggen on the Ubuntu machine?

Anyway, I have heard about cygwin/x. 

Which one do you think is better for me? And will I have to have X window installed on the Ubuntu machine to use cygwin/x?

Thanks

if you ssh into your ubuntu machine, yes, you can run any command as if you were at a terminal on the actual machine.

cygwin is basically a unix-like environment for windows, that lets you run some unix tools on windows. you don't need cygwin on ubuntu, since ubuntu is already linux! :)

---

### Post by mravenca on 2006-11-24
I have just solved the problem. I installed ssh and downloaded Putty. Problem solved, but it was a long time for a total newbie to find out what to do:+))

---

### Post by 5h4rk on 2006-11-26
Is there any guide about this? How to set up and configure ssh?

---

### Post by StormNet on 2006-11-26
When i setup ssh i followed the guide at:

[OpenSSH (Ubuntu Handbook)]("http://cgi.ebay.ca/Sony-PlayStation-3-Game-console_W0QQitemZ140055419709QQihZ004QQcategoryZ62054QQrdZ1QQcmdZViewItem")

but i complemented it with the guide at:

[Debian SSH guide]("http://www.debian-administration.org/articles/87")

I used the second one to work with my host.allow and host.deny files in order to secure my SSH server.

---

### Post by Slim Odds on 2006-11-29
> **mravenca said:**
> I have just solved the problem. I installed ssh and downloaded Putty. Problem solved, but it was a long time for a total newbie to find out what to do:+))

Nothing against Putty, I've used it before and it's fine. But these days I prefer to use the cygwin port of ssh. It's bit more of a natural feel using it with the Linux environment. 

You can also set it up as a server on the Windows side and do the reverse commute :).

Just my thoughts.

---

