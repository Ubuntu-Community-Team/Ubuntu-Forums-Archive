---
title: "General questions about ssh"
date: 2012-04-30
forum: General Help
---

### Post by hakermania on 2012-04-30
The below problem has been solved, but I mark this thread as unsolved because another similar problem has arise:
when I am trying from a friend's machine (not being in LAN) to connect via ssh to my machine, it gets stuck while trying to connect.
Specifically, I have used dyndns to register a dns, and I have successfully setup a small webpage for personal use, being 'served' by my PC which also runs the APACHE server.
So, I can access my server on my local pc from anywhere outside my house by giving xxxx.dyndns.org to any browser.
Now, that I've installed the openssh server and ssh client, shouldn't I be able using xxxx.dyndns.org to access my pc from anywhere?
So, at first I tried sshing with:
```

bingo@remotemachine:~$ ssh -v -p 22 xxxx.dyndns.org

```and I got:
```

debug1: Reading configuration data /etc/ssh/ssh_config debug1:
Applying options for * debug1:
Connecting to solpan.dyndns.org [100.100.100.100] port 22.

```and it stucks there till it outputs timeout.
Then, I went to /etc/ssh/sshd_config to the local machine and changed the port to 8675 (randomly) and then I gave
```

sudo service ssh restart

```and from the other machine (I could switch machines so easily because I was connected to the other machine using TeamViewer) I gave the same command as the above but using port 8675. Same result, it hangs till it outputs that the connection has timed out.

What can be wrong?


** ==========================================================**
Solved problems of understanding SSH:

Soooooo, I've installed ssh and ssh server and I could login to localhost by giving
```

ssh localhost

```and typing in my login password.

I currently don't have any local PC with linux in it so as to test it locally, but would I be able to login to my PC through an other local PC?
My **local** ip is static (192.168.1.254) and thus, if I give from an other local machine
```

ssh 192.168.1.254

```will I be able to login?

Also, what about login in to my PC from an extrernal PC (behind other modem somewhere else)?

I will totally need my current external IP of my PC.
So the thought is taking the external IP of my PC every once in a while (it isn't static) and update an online file, like an U1 file, and from the external PC, through a script probably, check this file to see the IP address of my PC and then login through e.g.
```

ssh 63.78.1.107

```But then more questions rise, what if two local machines (which have the same external IP address) have installed the ssh server, how does ssh know where to connect to?

Please help me clear it up a bit, because in the search I've done everything seems so easy to be done with ssh but all these questions stay unanswered to me.

Thanks in advance!

---

### Post by josephmills on 2012-04-30
log into new box (anywhere) ---> Log back into your box --> log backinto that same box again one big old circle 

you can also loginto stuff in the lan 
ssh [email]foo@bar.dns.com[/email]
---------------------------===
foo part
```
whoami
``````
foo

```

-----------------------------------------
bar part
```
hostname 

```
```
bar 

```



log into router too see dns

---

### Post by hakermania on 2012-04-30
Ok, thanks, so, so as to connect locally to my machine, it should be
```

ssh alex@MaD-pc

```
but I didn't understand how to do this 'big circle', you suggested connecting to my PC externally and then again to the external PC or something? And how is this going to be done? As I think of it, shouldn't the external PC also have ssh server for this (in that case, it is useless, i only want to connect from the external pc to my pc)?

---

### Post by josephmills on 2012-04-30
> **hakermania said:**
> Ok, thanks, so, so as to connect locally to my machine, it should be
```

ssh alex@MaD-pc

```
but I didn't understand how to do this 'big circle', you suggested connecting to my PC externally and then again to the external PC or something? And how is this going to be done? As I think of it, shouldn't the external PC also have ssh server for this (in that case, it is useless, i only want to connect from the external pc to my pc)?

you have to log into your router and add a dns name or just uses yours that is setup or like I said set one up :) 

the only reason one would ssh off site then back in like that. Is when testing what. I was talking about is for debugging lets say I have a question I just set up server and is my server listening on new port 6342 IDK ssh ---> some computer  --> then ssh back in 

most the time this is done with the -v option. 


that is what I was talking about circle :P

---

### Post by hakermania on 2012-04-30
Oh, I've already setup a server, nice :)

Thanks a lot!

---

### Post by CatKiller on 2012-04-30
The computer you're logging in from doesn't need to be running Linux; SSH clients are available on other platforms. I believe PuTTY is a popular choice for getting such things done on Windows, but I've not used it.

As long as you can find the computer on the Internet and the traffic gets through you can SSH to your computer from outside your LAN. There are Dynamic DNS services that will help with the first bit, or you can do as you suggest and get your computer to periodically check its IP address and send it to you in some fashion. The other part depends on your router configuration. You'll want to tell your computer to forward any packets that come through on your SSH port, 22 say, to the computer that's running the SSH daemon.

If you have multiple computers running SSH on a network with only one external IP address you can either use a different port for each machine and use port forwarding on your router to get to the correct machine or designate one machine as a gateway machine that's exposed to the Internet, log into that one from outside and then SSH from that machine to another on your LAN.

---

### Post by hakermania on 2012-05-01
bump (please read original thread)

---

### Post by hakermania on 2012-05-02
I was also able to login from a local machine to my machine, using:
```

ssh -p 8675 alex@192.168.1.254

```
where 192.168.1.254 is my static local IP.
But still, no luck when trying to do something through the DNS, while it resolves its address (which is mine, actually), the connection times out!

---

### Post by Peter09 on 2012-05-02
Do
 
ssh -vv 'the rest of the command line'
 
it gives you a verbose login so that you can see whats happening.

---

### Post by SeijiSensei on 2012-05-02
Is the machine running sshd directly connected to the Internet, or is it behind a router?  If the latter, did you use the router's port forwarding tools to forward external port 22 back to the server?  If so, and it still doesn't work, your ISP may be blocking connections on port 22.  Try setting the external port to some arbitrary port like 22222 and forwarding that back to the server.  Make sure you open the arbitrary port using the router's firewalling tools.  Then use "ssh -p 22222 yourname.dyndns.org" to connect.

To check that name resolution is working correctly, try "ping yourname.dyndns.org".

---

### Post by hakermania on 2012-05-04
> **SeijiSensei said:**
> Is the machine running sshd directly connected to the Internet, or is it behind a router?  If the latter, did you use the router's port forwarding tools to forward external port 22 back to the server?  If so, and it still doesn't work, your ISP may be blocking connections on port 22.  Try setting the external port to some arbitrary port like 22222 and forwarding that back to the server.  Make sure you open the arbitrary port using the router's firewalling tools.  Then use "ssh -p 22222 yourname.dyndns.org" to connect.

To check that name resolution is working correctly, try "ping yourname.dyndns.org".

Thanks for the answer!
I am using port 8675 for ssh, because I am aware that my ISP can block port 22. But yes, I am behind a router and I haven't forwarded any port!
@Peter09 I did that and it stays at "Connecing to XXX.XXX.XXX.XXX" and then, after a couple of minutes it says that the connection has timed out!

---

### Post by Peter09 on 2012-05-04
Are both ends of the connection using port 8675? You need to tell the client application and the server application which port to use.
 
If you are going through a router (at the server end) then you will need to forward (in the servers local router) port 8675 to the ip address of the server. Otherwise when there is an incoming request from the internet your (servers) router will not know where to send it. The client end does not matter.

---

### Post by hakermania on 2012-05-04
> **Peter09 said:**
> Are both ends of the connection using port 8675? You need to tell the client application and the server application which port to use.
 
If you are going through a router (at the server end) then you will need to forward (in the servers local router) port 8675 to the ip address of the server. Otherwise when there is an incoming request from the internet your (servers) router will not know where to send it. The client end does not matter.

Got it, so I need to redirect the input at port 8675 to my local IP, good thing it's static (192.168.1.254).

I will do it soon, and I will let you know how it went!

---

