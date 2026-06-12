---
title: "access Remote Desktop behind router"
date: 2009-12-07
forum: General Help
---

### Post by gypsumwolf on 2009-12-07
Is it possible (and how) would I connect to a computer behind a router if I have no control of the router, but I know the router is set up with default settings. (If I can't set up port forwarding on the router).

My PC ---------------> Router ---> OthersPC

---

### Post by Snow986 on 2009-12-07
You would have to know what the routers external IP is, the computers internal IP, and then you would have to use either VNC or ssh (among others) but port 22(ssh) is usually set to open on default router settings.  VNC ports can vary a little but they are not always open on default settings.  Ofcourse you will have to make sure the ports are open on the pc you are trying to reach.

---

### Post by mal on 2009-12-07
Reverse SSH.

Sorry, I don't have the instructions, but a search of the forums should give you some pointers.

Mal

---

### Post by gypsumwolf on 2009-12-08
> **Snow986 said:**
> You would have to know what the routers external IP is, the computers internal IP, and then you would have to use either VNC or ssh (among others) but port 22(ssh) is usually set to open on default router settings.  VNC ports can vary a little but they are not always open on default settings.  Ofcourse you will have to make sure the ports are open on the pc you are trying to reach.
I would like to use ssh on port 22 or port 443. If 22 is not open then 443 probably will be.

> **mal said:**
> Reverse SSH.

Sorry, I don't have the instructions, but a search of the forums should give you some pointers.

Mal

Sounds interesting. Let me know if u find instructions about that.

---

### Post by gypsumwolf on 2009-12-08
Just found these to info sources:

[http://www.howtoforge.com/reverse-ssh-tunneling]("http://www.howtoforge.com/reverse-ssh-tunneling")

[http://www.raiden.net/articles/howto_create_a_reverse_ssh_tunnel/]("http://www.raiden.net/articles/howto_create_a_reverse_ssh_tunnel/")

---

### Post by gypsumwolf on 2009-12-08
Not sure how that would work with a router though. Any ideas?

---

### Post by Snow986 on 2009-12-08
There's no point in Reverse SSHing.  Just ssh into the box from the external ip... 
```

ssh 192.168.*.*@externalIP

```

---

### Post by shazi786 on 2009-12-08
if you are trying to use windows desktop connectivity then it is not possible. otherwise you can use TeamViewer application for desktop sharing.

---

### Post by gypsumwolf on 2009-12-08
> **Snow986 said:**
> There's no point in Reverse SSHing.  Just ssh into the box from the external ip... 
```

ssh 192.168.*.*@externalIP

```

I am confused.

Which computer is the " 192.168.*.*" ip adddress for? is it PC2 in my diagram? and is the externalIP then IP of the router?

[PC1]------------>[Router]---->[PC2]

So is this what your saying?

```
ssh PC2@router
```

---

### Post by Snow986 on 2009-12-08
Right,  open a terminal and do 
```

man ssh

```
to learn how to use ssh.  Basically, the 192.168.*.* will be replaced with the computers IP and the external IP is the IP given to the router from the ISP.

---

### Post by mal on 2009-12-09
Snow986,

Sorry, but I will be very surprised if you can connect through a router using "ssh 192.168.*.*@externalIP".  This would mean that every machine that is sitting behind a router is open to attack from the internet without any ports on the router being forwarded.

gypsumwolf,

In answer to your last question (post #6), the idea of reverse SSH is that it provides a means of getting through the router by creating a tunnel from the inside.  You have to set this up first from the destination machine (OthersPC), with the source machine (My PC) being accessible from the internet (eg with port 22 forwarded).  You can then communicate from the source to the destination.  If the tunnel is disconnected for any reason, you would have to re-establish it from the destination machine (a bit of a disadvantage if the connection is not reliable).

Regards,

Mal

---

### Post by Snow986 on 2009-12-09
> **mal said:**
> Snow986,

gypsumwolf,

In answer to your last question (post #6), the idea of reverse SSH is that it provides a means of getting through the router by creating a tunnel from the inside.  You have to set this up first from the destination machine (OthersPC), with the source machine (My PC) being accessible from the internet (eg with port 22 forwarded).  You can then communicate from the source to the destination.  If the tunnel is disconnected for any reason, you would have to re-establish it from the destination machine (a bit of a disadvantage if the connection is not reliable).

Regards,

Mal

 I said that the port would have to be open on both router and machine.  I use this method to connect to my work and home pc's.

---

### Post by gypsumwolf on 2009-12-11
> **Snow986 said:**
> I said that the port would have to be open on both router and machine.  I use this method to connect to my work and home pc's.

I am talking about if I have no access to the router (no port forwarding). That is where it is different. I know how to use ssh just fine, I do it all the time.

---

### Post by blackened on 2009-12-11
> **gypsumwolf said:**
> I am talking about if I have no access to the router (no port forwarding). That is where it is different. I know how to use ssh just fine, I do it all the time.

If you don't have access to the router settings, then your only real choices are reverse ssh or some sort of vpn software like Hamachi. The latter would be my vote.

---

### Post by gypsumwolf on 2009-12-11
If the person on the other computer ssh's to my computer can I somehow use that tunnel to access their computer? Or somehow trace their route and use the same route. (Is that even possible?)

---

### Post by blackened on 2009-12-12
> **gypsumwolf said:**
> If the person on the other computer ssh's to my computer can I somehow use that tunnel to access their computer? Or somehow trace their route and use the same route. (Is that even possible?)

It's possible to use VNC in listening mode with an SSH tunnel. This would require that the server initiate the connection to the viewer, but that can be accomplished with cron running a server-to-client connection script every so often. Or, for that darker OS, Windows Scheduler.

Seriously though, you should look into Hamachi unless you're just out for the learning experience.

---

