---
title: "How do I ssh?"
date: 2010-08-14
forum: General Help
---

### Post by linux18 on 2010-08-14
I've posted almost 400 times and nearly every one was for helping others, now I've come across my first ever real problem: using ssh. I have a computer 6 feet from the laptop I'm typing this on and I want to communicate with it! I don't know where I've gone wrong this is really the only thing I can't seem to do on linux, I'm not a noob (over 4 years of linux experience) but I conveniently avoided the whole ssh problem on my other servers through cron, web interfaces, and such. Now I'm motivated to do it the right way, I wan't to learn this. So will you help?

---

### Post by Bachstelze on 2010-08-14
Did you install openssh-server on the machine you want to connect to?

---

### Post by cj.surrusco on 2010-08-14
Well it's kind of hard to tell what could be wrong without listing the command used to connect to the server. Make sure that you are using the username like 'ssh user@host' and if you are using an external IP, make sure the router port 22 is forwarded to the server. And also make sure openssh-server is installed as the previous post mentions.

---

### Post by Iowan on 2010-08-14
I set up my server with the same username I used for this workstation, so I can **ssh servername** without the "username@servername". Because it's internal, I'm using the default port 22, so I don't need to specify that either. I still need to set up keys, so I DO need to supply a password when requested.

Have you seen the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html") section on SSH server?

---

### Post by linux18 on 2010-08-14
I'm not even getting to the point where I'm supplying passwords, I just get:  Connection refused if someone could show an example of the exact sequence of commands for both client and server that would help.I know I'm messing up on some small detail somewhere.

---

### Post by bodhi.zazen on 2010-08-14
Server:

```
sudo apt-get install ssh
```

Client :

```
ssh user@server
```

If you are getting connection refused, most likely you either need to forward port 22 from a router to your server or you have a firewall. could be a DNS problem as well (use the server IP address).

To test, use the -vv option

```
ssh -vv user@server
```

Just be sure to secure the ssh server (use keys, disable passwords).

---

### Post by bilkay on 2010-08-23
Your problem might be in /etc/hosts.allow and /etc/hosts.deny.

$ man hosts.allow

---

### Post by pricetech on 2010-08-23
The OP says the computers are 6 feet away from one another, so it's probably safe to assume they are on the same subnet.

OP;
Have you installed openssh-server on the server you want to connect to ??
If so, have you edited the config file for it ??  It should function on port 22 by default, so if you haven't touched the config, it should work anyway.
Try ssh "user@server_IP" (without the quotes of course) on the client.  It should just plain work.

---

### Post by triunenature on 2010-08-23
Definitive Guide:

Server (the computer you want to connect TO):

```
sudo apt-get install openssh-server
sudo /etc/init.d/ssh start
```

If you get any erros with; sudo /etc/init.d/ssh start

post them here,

Client:

```
ssh serverip
```

Note, if you want both computers to be able to ssh to each other, both need to be servers and both need to be client, so install openssh-server on both machines

post error messages please

:: Also, make sure both machines iptables allow for ssh!!! (ie iptables allow port 22)

---

### Post by mhgsys on 2010-08-23
just want to add to everything listed here;

```
ssh user@ipadress
```

f.e ssh mhg@192.168.1.11

(You might want to set a static ip,.btw)

---

### Post by liquidfunk on 2010-08-23
```
ssh -X username@server 
```

is nice too. Bringing the Xsession across to you.

---

### Post by nothingspecial on 2010-08-23
On both machines

```
sudo apt get install openssh-server openssh-client
```

Then from the client machine

```
ssh -X -C -c blowfish user@ipadress 
```

That is how you do it.

---

