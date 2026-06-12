---
title: "opening port 119"
date: 2006-04-10
forum: General Help
---

### Post by frankie84 on 2006-04-10
Hi this is my first post i hope this is in the right forum, sorry if its not.

could any one tell me how I go about opening port 119

thanks
Steven

---

### Post by cwaldbieser on 2006-04-10
[QUOTE=frankie84]Hi this is my first post i hope this is in the right forum, sorry if its not.

could any one tell me how I go about opening port 119

thanks
Steven[/QUOTE]
If you are not running a firewall, the port will be open by default.
If you are running a firewall, let us know what front end you are using (e.g. firestarter).
Feel free to explain what you are trying to do, so we can better understand the problem.

---

### Post by frankie84 on 2006-04-11
Im not running a firewall, but when I have run a port scan port 119 is not shown as open.

It is for a University project where I need the port to be open.

---

### Post by krismatth3 on 2006-04-11
Did your port scan show 119 as not open or as nothing listening? Nothing listening means that it is open.

Are you behind a router? Is it configured properly? For the university project, are you trying to connect via a loopback IP address, a local address, or through whatever NAT device / switch?

(Sorry for all the questions!)

---

### Post by frankie84 on 2006-04-11
I entered nmap -P0 my ip address into the termina and got the following output

(The 1661 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
25/tcp open  smtp
80/tcp open  http

I am completly new to linux and running web servers so please bare with me. 

I have set up the web server on my machine and i running a php script on it that should allow me to connect to the message board I am running on my server through a newsreader. But when i try to connect though the newsreader using my ip address i get the message 

could not connect to server connection was refused

Im guessing that this was down to the fact that port 119 was closed

---

### Post by krismatth3 on 2006-04-11
Oh. The port scan means that something is listening on ports 25 (mail) and 80 (www). It does not mean the other ports are closed. The reason you can't connect is that you're not running an nntp server (which uses port 119).

What messageboard software is this that allows you to connect with a newsreader? I'm not familiar with it. :)

---

### Post by frankie84 on 2006-04-11
im trying to connect to a version of a phpbb.com message board that allows threaded posts.

I have that installed on the server and have also a php script that i run that should allow the newsreader to communicate with the message board.

So the problem isnt down to the port being closed?

---

### Post by cwaldbieser on 2006-04-11
[QUOTE=frankie84]im trying to connect to a version of a phpbb.com message board that allows threaded posts.

I have that installed on the server and have also a php script that i run that should allow the newsreader to communicate with the message board.

So the problem isnt down to the port being closed?[/QUOTE]
Don't those message boards usually run as web pages?  The server is probably serving them up on port 80 like any other web page.

If there a link to the documentation for the newsreader script you are using?

By the way, if no server is listening on a port,  you typically get a connection refused message.  For example, try
```

$ telnet 127.0.0.1 9900

```

---

### Post by krismatth3 on 2006-04-12
I believe the problem is not that the port is closed - there is simply nothing listening on this port. I am unfamiliar with any PHP script that acts as an NNTP server. Could you provide a link? We can examine it better that way.

---

