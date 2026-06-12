---
title: "Accessing my router via telnet"
date: 2009-11-04
forum: General Help
---

### Post by Isilion on 2009-11-04
I want to manage my router using telnet since i havent got a desktop environment.
ISP gave me the relevant information need to have root privileges over my router. They gave me the same account they use. debugging info:

isilion@felix-00:~$ telnet 192.168.0.1 23
Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.
Connection closed by foreign host.
isilion@felix-00:~$ telnet 192.168.0.1 8063
Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.
HTTP/1.1 400 Bad Request
Server: micro_httpd
Cache-Control: no-cache
Date: Wed, 04 Nov 2009 12:55:48 GMT
Content-Type: text/html
Connection: close

<HTML><HEAD><TITLE>400 Bad Request</TITLE></HEAD>
<BODY BGCOLOR="#cc9999"><H4>400 Bad Request</H4>
No request found.
<HR>
<ADDRESS><A HREF="http://www.acme.com/software/micro_httpd/">micro_httpd</A></ADDRESS>
</BODY></HTML>
Connection closed by foreign host.
isilion@felix-00:~$ 


(thats trying to connect to de internal routers ip, my gateway) ISP told me they use another IP address, which is my VoIP. When trying to connect these, telnet seems be waiting for something and nothing happens)

isilion@felix-00:~$ telnet 172.x.x.120 23 <--- external VoIP (that is what ISP uses, but i think i cannot call to myself)

Trying 172.x.x.120...
Connected to 172.x.x.120.
Escape character is '^]'.
Connection closed by foreign host.
isilion@felix-00:~$ telnet 217.x.x.3 23 <--- internal VoIP
Trying 217.x.x.3...

(nothing happens, CTRL + C)
isilion@felix-00:~$ 




the router has open both ports 23, 1720 and 8063. 8063 is the one i use for managing the router with a webbrowser. Im trying port 23 for telnet but for some reason connection refuses.

---

### Post by Isilion on 2009-11-04
what im looking for is that my router wont be accessible using telnet from outside my lan.

i have a forwarding for ssh so i can manage my servers via SSH. Once in, i would be able to connect the router using telnet, with a non default port if posible.

I would do, if someone could explain me why the router closes the connections or whats awaiting for...

Thanks in advance

---

### Post by justleen on 2009-11-04
try entering the account details in the command?
```
 telnet -l user 192.168.0.1 23 
```

Trying to telnet to the web port won't work offcourse. Yould perhaps try a text based browser like elinks or lynx for that..

edit: the default port for telnet would be 23, so you dont have to add it.

---

### Post by Isilion on 2009-11-04
i tryed that command but router still closing the connection:

Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.
Connection closed by foreign host.


ISP uses the VoIP address to manage my router. i got that ip, both internal and external. i mean, that perhaps I may not work on 192.168.0.1.

router is a telsey from Tele2.

---

### Post by ColdFFF on 2009-11-04
The command justleen gave you is very generic. He was using it to show you how to include the account details in the telnet command.

Modify the command to suit. You could try:

```
telnet -l xxx 172.x.x.120 23
```

Make sure to replace xxx with the account name

---

