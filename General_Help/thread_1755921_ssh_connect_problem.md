---
title: "ssh connect problem"
date: 2011-05-11
forum: General Help
---

### Post by Gr33nGapion on 2011-05-11
So I'm fairly new to Ubuntu forums, but I'm trying to connect to ssh and can't find anyone with the same problem as me:

I have a desktop and netbook both running Ubuntu. I installed openssh-client and openssh-server on both machines. when I open a terminal on my netbook and try to connect to my desktop using ssh user@ip I get no response. No error, no confirmation, just a blinking cursor on the next line..

Any help would be greatly appreciated. Thanks!

---

### Post by spiky001 on 2011-05-11
Are they both on the same internet network? i.e 10.42.43.xx

---

### Post by Dave_L on 2011-05-11
Can you ping the desktop from the netbook?

---

### Post by spiky001 on 2011-05-11
Also is this on local network or over internet?

---

### Post by serialsito on 2011-05-11
We need more information, you can get it with ssh in verbose mode

Ssh user@ip -vvv

---

### Post by Gr33nGapion on 2011-05-11
Thanks guys for getting back to me so fast! 

Here are the answers to your questions:

Both my netbook and desktop are on the same network according to my the ip addresses. I'm using the network at my University.

I can successfully ping to and from both machines.

Even though I am on a local network I would like to be able to do it over the internet in the future. I will be working on campus with my netbook over the summer, but leave my desktop at home on a separate network and I would still like to connect from campus.

I tried ssh user@ip -vvv and this is what it said:

nate@NateEeePC-1000HE:~$ ssh nate@MY_IP* -vvv
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 72.19.125.73 [72.19.125.73] port 22.

I tried it again as root but that didn't change anything.

Thanks again for your help!

---

### Post by spiky001 on 2011-05-12
Do you have the firewall active on the 1 you are trying to ssh into?

---

### Post by Gr33nGapion on 2011-05-12
I'm not sure. I haven't really played with firewalls before and I don't really know how to check.

---

### Post by spiky001 on 2011-05-12
How are they both connected wire/wireless dose it go through a router

---

### Post by Gr33nGapion on 2011-05-13
Well I'm using the internet at my University so I'm not entirely sure. At the moment both my desktop and netbook are wired in, but my netbook will be on wireless 95% of the time.

---

### Post by matt_symes on 2011-05-13
Hi

> when I open a terminal on my netbook and try to connect to my desktop using ssh user@ip I get no response.Can you do the converse. From your desktop, can you connect to your notebook ? Try this first.

From your desktop can to ssh into local host ?

```
ssh user_name@127.0.0.1
```Have you checked the ports are open and the ssh sever is running on the desktop ? Are the Uni blocking port 22 ? Have you tried a different port number ?

Have you tried flushing any iptable rules on your desktop and netbook ?

```
sudo iptables -f
```Just some things to check.

Can you ssh into the desktop if they are both wired ?

Kind regards

---

### Post by john_spiral on 2011-05-13
run the 'lsof -i' command on both machines to see what network connections are taking place.

---

### Post by tenon on 2011-05-14
Can you verify which IP your ssh server is listening on? (it's possible sshd is installed but not running)
 
>  
netstat -an | grep LISTEN

 
Look for all IP's that are listening on port 22. Check both machines.
 
Also, test the connectivity.
 
```
 
telnet ip_of_other_host 22

```
 
If you have to hit <Control-C> because there's no response, let it run for a few minutes. Please post the results of the command.

---

### Post by Gr33nGapion on 2011-05-16
Okay so I just had to move back home from college for the next week or so. On my home network EVERYTHING works perfectly. I can ssh and scp files back and forth.

I'm guessing this means the problem has to do with the University's network... But I'm not sure how to even start looking at that. 

In a week or so my Desktop will be staying at my place off campus and my netbook will be accessing it from campus. I have a feeling this won't be a problem, but come fall everything will be on the campus network. 

Are there any checks I can use to see what problems are occurring when I get back on campus?

---

### Post by spiky001 on 2011-05-16
Maybe you could change the ssh port, maybe it,s being blocked at campus, as it works at home,  To change port number /etc/ssh/sshd_conf
[http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html](http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html)

---

