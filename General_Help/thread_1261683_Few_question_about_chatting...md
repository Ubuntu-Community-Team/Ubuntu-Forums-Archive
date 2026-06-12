---
title: "Few question about chatting.."
date: 2009-09-09
forum: General Help
---

### Post by karthick87 on 2009-09-09
I used to chat with my friends in gmail and yahoo,and i have a fear that is it possible to get my ip address during chatting?If so how can i secure myself from being hacked?

---

### Post by 3rdalbum on 2009-09-09
Every time your computer sends data to another computer, it gives out its IP address. Otherwise, there's no probability of recieving data in return.

Ubuntu, by default, doesn't listen to any incoming ports, so it's not like anyone can just get into your system, unless you have installed server software like Apache, SSH or Postfix (anything that listens to incoming connections).

If you have software that listens to incoming connections, you need a firewall in between your computer and the Internet, that denies incoming connections. Many modem/routers have firewalls built-in these days.

---

### Post by karthick87 on 2009-09-09
I want to ensure that whether my system is listening incoming connections or not?How to check this?

---

### Post by gastly on 2009-09-09
You can do this with the netstat command. Open up a terminal and type:
```
netstat -pl
```

The **-l** will display all the listening server sockets and the **-p** option will also display the pid of the program which is listening to the port.

For mode info do **man netstat** :)

---

### Post by wojox on 2009-09-09
```
netstat -l
```

---

### Post by 3rdalbum on 2009-09-09
Wow, I've just learnt something new today: How to use netstat :-)

Netstat will show what is listening on incoming ports, but if your home network is protected by a firewall on the router, then anyone outside your network will not be able to access those ports.

If you're concerned, then try the Shields Up online port scanner: [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)

It will show you what ports are accessible from the Internet (click the "All Service Ports" button). If all are closed or "stealthed", then you don't need any additional protection. If one or two are opened, then you should take a look at what they might be (with that netstat command) and either take action to disable the listening program, or ensure that it is configured in as securely a fashion as possible if you really need that program running.

---

### Post by karthick87 on 2009-09-09
In the above site no options are present to scan..

---

### Post by gastly on 2009-09-09
It won't work with direct-linking to the page. go here [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm) and select 'Services->Shield's Up' from the navbar :)

---

### Post by karthick87 on 2009-09-09
I have scanned,it is my output
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=courier new,courier][SIZE=3][COLOR=black]GRC Port Authority Report created on UTC: 2009-09-09 at 17:09:10

Results from scan of ports: 0-1055

    0 Ports Open
 1056 Ports Closed
    0 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]Was my system secure???

---

