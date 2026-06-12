---
title: "command required to find  running server port"
date: 2012-06-12
forum: General Help
---

### Post by winzip on 2012-06-12
I  have started Alfresco server in Ubuntu.  I'm not sure on which port it is running.

How do I find on which port Alfresco server running ?

Is there any command to find it out ?

---

### Post by Cheesehead on 2012-06-12
[FONT="Courier New"]netstat -tulp[/FONT]  (for ports by name)
[FONT="Courier New"]sudo netstat -tulpn[/FONT] (for ports by port number)

You can run netstat as a user, but then you won't get PID info. 

The two examples below show how I looked for ports opened by NTP.
The first uses sudo, and I'm looking for PID# 19014, the NTP daemon. This shows the straight relationship - the NTP process has UDP port 123 on IPv4 and IPv6.
The second is done as a user, so it lacks PID info, so the search is by name instead of port number. More useful if you just want to confirm that a port is really open but don't care about the port number.
```
$ sudo netstat -tulpn | grep ntp
udp        0      0 192.168.1.10:123        0.0.0.0:*                           19014/ntpd      
udp        0      0 127.0.0.1:123           0.0.0.0:*                           19014/ntpd      
udp        0      0 0.0.0.0:123             0.0.0.0:*                           19014/ntpd      
udp6       0      0 ::1:123                 :::*                                19014/ntpd      
udp6       0      0 fe80::224:2cff:fe7c:123 :::*                                19014/ntpd      
udp6       0      0 :::123                  :::*                                19014/ntpd      


$ netstat -tulp | grep ntp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
udp        0      0 mycomputer.l:ntp *:*                                 -               
udp        0      0 localhost.localdoma:ntp *:*                                 -               
udp        0      0 *:ntp                   *:*                                 -               
udp6       0      0 mycomputer:ntp   [::]:*                              -               
udp6       0      0 fe80::224:2cff:fe7c:ntp [::]:*                              -               
udp6       0      0 [::]:ntp                [::]:*                              -               

```

---

### Post by winzip on 2012-06-12
> **Cheesehead said:**
> 
[FONT=Courier New]sudo netstat -tulpn[/FONT] (for ports by port number)


[COLOR=Blue]I'll try this because this will tell me port number on which Alfresco server is running.[/COLOR] 

[COLOR=RoyalBlue]By the way  what does ***tulpn* **means literally  ?
[/COLOR] 
> 
 More useful if you just want to confirm that a port is really open **[COLOR=Red]but don't care about the port number.[/COLOR]**
[COLOR=Blue]I need to know port number[/COLOR]

---

### Post by krismatth3 on 2012-06-12
> **winzip said:**
> [COLOR=Blue]I'll try this because this will tell me port number on which Alfresco server is running.[/COLOR] 

[COLOR=RoyalBlue]By the way  what does ***tulpn* **means literally  ?
[/COLOR] 
[COLOR=Blue]I need to know port number[/COLOR]

I think he typoed the second "port number" - it looks like he meant "process id."

---

### Post by winzip on 2012-06-12
I checked this ...
**sudo netstat -tulpn | grep alfresco**

But this does not  produce any output although my alfresco server is up.

---

### Post by Habitual on 2012-06-12
[https://wiki.alfresco.com/wiki/Port_numbers](https://wiki.alfresco.com/wiki/Port_numbers)

```
netstat -plaunt | grep 505
```
tcp6       0      0 :::50500                :::*                    LISTEN      682/java        
tcp6       0      0 :::50508                :::*                    LISTEN      682/java

---

### Post by philinux on 2012-06-12
> **winzip said:**
> [By the way  what does ***tulpn* **means literally ]

See 

```
man netstat
```

---

### Post by Lars Noodén on 2012-06-12
> **winzip said:**
> [COLOR=Blue]By the way  what does ***tulpn* **means literally  ?

These can be looked up in the manual page for [netstat](http://manpages.ubuntu.com/manpages/precise/en/man8/netstat.8.html).  Open a terminal and enter:

```

man netstat

```

---

### Post by winzip on 2012-06-19
> **Habitual said:**
> [https://wiki.alfresco.com/wiki/Port_numbers](https://wiki.alfresco.com/wiki/Port_numbers)

```
netstat -plaunt | grep 505
```tcp6       0      0 :::50500                :::*                    LISTEN      682/java        
tcp6       0      0 :::50508                :::*                    LISTEN      682/java

you are making more complicated.
This is not always possible to find such numbers  505.  There should be some easy way out to find port number of a running server.

is there anything wrong with this ? 
something like this ..netstat -plaunt | grep **alfresco**  ?  ....much more meaningful ....

I'm not sure just a guess ..

---

### Post by Habitual on 2012-06-19
Alfresco does not run as "alfresco" obviously.

How is grep'ing for all alfresco ports (505xx) "complicated"?

It's all "there"...[https://wiki.alfresco.com/wiki/Port_numbers#Alfresco_Port_Configuration](https://wiki.alfresco.com/wiki/Port_numbers#Alfresco_Port_Configuration)

---

### Post by IraBa on 2012-07-05
Alfresco runs many services on different ports. By default it installs tomcat to run on port 8080. But since it runs via Java then all alfresco services are identified by 'java' with netstat. If you used the installer that comes with alfresco it would have asked  you what ports you want to install the different services on. If you've forgotten then you can find the default ports in alfresco-global.properties.sample - use 'locate' to find this.

Another buggy thing with alfresco is that if you don't do a clean powerdown - e.g. 'service alfresco stop' or shutdown - then on boot only some alfresco services will start.  remove /opt/alfresco-4.0.x/tomcat/temp/catalina.pid and use 'service alfresco restart' and you should be all good.

---

