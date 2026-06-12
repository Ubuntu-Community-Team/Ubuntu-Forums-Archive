---
title: "SSH Help"
date: 2009-07-10
forum: General Help
---

### Post by tom.swartz07 on 2009-07-10
Hey everyone,

Im not sure if this thread belongs here, but for the most part, this is a general help question.

I have been trying to setup SSH on my home network so that I could access my home computer (Dell Inspiron Ubuntu 9.04) from the road (Ubuntu 9.04 running on a persistent usb key).

I have setup ssh correctly (I believe); assigning my routers IP address to DynDNS.org, opening the selected ports 22, 5900, etc in the firewall both from the router and from my ISP Verizon.

I have only been able to SSH once. I logged on to my neighbors wifi (SSHHHH! dont tell) and used the command 
```
$ ssh tom@**.homelinux.com
 
```Where ** is my domain name.
Over the entire process of setting up the SSH, I have used another laptop running Ubuntu to test the SSH connection.
Like I had mentioned before, it had only worked once or twice, and now every time I try I get the error
```
ssh: connect to host **.homelinux.com port 22: Connection refused
 
```Does anyone know what I am doing wrong?
The ultimate goal for this is to tunnel X11 through the SSH connection, so that I could remotely and securely control my desktop at home while on the road, similar to a secure VNC connection.

---

### Post by alien8tive on 2009-07-11
What happens if you 

```
telnet **.homelinux.com 22
```

Also from you machine,

```
telnet localhost 22
```

just to make sure ssh is working.

---

### Post by GCoffee on 2009-07-11
I belive, connection refused is where the ports havent been forwarded right.. or have you updated your dynamic IP?

I use a similair setup and often find i forget to update the dynamic IP. 

go to dyndns.org, login, and check your IP has been updated.

---

### Post by ducksun43 on 2009-07-11
see [http://sunoano.name/ws/public_xhtml/ssh.html](http://sunoano.name/ws/public_xhtml/ssh.html) --> PKA

---

### Post by tom.swartz07 on 2009-07-11
Thanks everyone for your quick help!

I managed to get back on only after I noticed that the connection to the outside network had dropped, and the testing laptop had reverted to my own wireless network. ](*,):-\"

Everything seems to connect fine!

Now for the bigger question, how would I use my USB Ubuntu to SSH in to the home laptop to say, securely use firefox sans web blocks, or to load files from the home computer on the mobile one? Like I said, this is the final goal of it, but I cannot seem to figure it out.
I know about foxyproxy, but I am unsure how to set it up. Ive heard that this is a better bet to use.

---

### Post by tom.swartz07 on 2009-07-25
Hey everyone again...


It seems that I am still having trouble with the SSH connections.

I have updated my dynamic IP, thanks for the tip, (that seems to change pretty often, ill need to keep an eye on it)

When I attempt to use 
```
telnet **.homelinux.com 22
```
It returns an error message, but when I use the localhost command, it logs right in and returns ```
tom@ubuntu-laptop:~$ telnet localhost 22
Trying ::1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
```

What seems to be wrong here, Im really only a beginner at all of this, so Im not too sure about what I need to do here.

I know for certain that the dyndns account is registered for my ip, and (i believe, although i may be wrong) the port forwarding is setup correctly. Does anyone have any experience with a Westell 6100 modem connected to a Belkin wireless g router? Both of the devices needed to be setup with the port forwarding rules, and I believe, to the best of my knowledge, that it is done correctly... walk-through anyone?

Thanks to everyone so far for the help! Anything else would be greatly appreciated!

---

### Post by sideaway on 2009-07-29
Hi guys, I have a similar problem, I'm sure it's simple but:

Trying to ssh over local network
```
hamish@hamish-desktop:~$ ssh 192.168.1.8
ssh: connect to host 192.168.1.8 port 22: Connection refused
hamish@hamish-desktop:~$ telnet localhost 22
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

What's wrong or what haven't I configured installed?

---

