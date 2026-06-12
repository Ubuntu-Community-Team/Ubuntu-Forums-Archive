---
title: "ssh: connect to host XXXX port 22: Connection timed out"
date: 2010-07-04
forum: General Help
---

### Post by jv2112 on 2010-07-04
I have been playing with this for awhile now and I am ready to go postal. ](*,)

I just want to move some files around and potentially rsync my net book with my desktop as well as learn the software (my primary reason)


Steps Taken.
Set Static IP address to machines on LAN
Turned on Port Forwarding (22)
Added Rule to UFW allow 22/TCP

Any support in helping me avoid multiple life sentences will be appreciated. ..LOL :D

---

### Post by CharlesA on 2010-07-04
If you are connecting from outside your local network, try setting it to use a different port, as your ISP might block port 22.

---

### Post by jv2112 on 2010-07-04
How  ?


ssh -p 18 TUX-BOX

(also tried 5590,6188 )

got me the same result..... Thoughts ?

Thank You

---

### Post by snkiz on 2010-07-04
do you have dns on your network? If you does you could try to connect with a hostname instead of depending on static ip. A little more robust that way

---

### Post by prodigy_ on 2010-07-04
Wait. Some stupid questions first: 

1) Did you install **openssh-server** package?
2) Did you enable it to listen on whatever IP address you want to connect to (in /etc/ssh/sshd_config)?
3) Did you start sshd?
4) Can telnet connect on port 22 (or whatever port you tell sshd to bind to)? The command is: ```
telnet <sshd_host_name_or_ip_address> <port>
```

If telnet times out, then either sshd isn't up or something (sshd, name resolution or firewall) isn't configured properly.

---

### Post by DJYoshaBYD on 2010-07-04
it should come configured for port 22 by default, as that is the industry standard SSH port..

You should probably forward UDP, as well.. 

you can also port scan your self using the following command

```
nc -vv youripaddresshere 22
```

that will give you a prompt that will tell you if you succeeded in connecting to it..

check iptables, as well.. make sure that is good, and there is no ACL set up ( i dont know why there would be, but check anyway..)

And I believe you have to tell your ssh conf file to accept connections from outside of your network.. its been helllllllllaaaa long since I installed it, and i never need to admin it, so I could tell ya.. lol

haha.. almost forgot.. is the service even running? haha.. cause, you can do all the networking you want, but if the service hasnt been started, then, well, you get the idea **thumbsup**

---

### Post by DJYoshaBYD on 2010-07-04
> **snkiz said:**
> do you have dns on your network? If you does you could try to connect with a hostname instead of depending on static ip. A little more robust that way

you could do that, but you have to make a CNAME record to point to the ip address and port

```
@       IN       CNAME   mydomainorIP:port
```

although, i have never been successful in doing that.. it just doesnt like it..

like, at work, i have a simple script set up, with a command like this, replacing the need to type ssh -l joo -p 1234 myipaddressorURL

this script, simply called house, will take me home via SSH

```
ssh myname@mydomain -p 1234
```

then, i can just type house, and it will take me there..

although, im pretty sure, that with SSH clients, you cannot send the URL:port.. you have to send it like - URL -p port

---

### Post by CharlesA on 2010-07-04
> **jv2112 said:**
> How  ?


ssh -p 18 TUX-BOX

(also tried 5590,6188 )

got me the same result..... Thoughts ?

Thank You

Are you connecting from outside your network or on the local LAN? You never answered that.

Also, try connecting using the IP address instead of hostname.

You can configure which port sshd listens on by editing the setting below in /etc/ssh/sshd_config:

```
# What ports, IPs and protocols we listen for
Port 22
```

Then restart ssh:

```
sudo service ssh stop && sudo server ssh start
```

> **prodigy_ said:**
> Wait. Some stupid questions first: 

1) Did you install **openssh-server** package?
2) Did you enable it to listen on whatever IP address you want to connect to (in /etc/ssh/sshd_config)?
3) Did you start sshd?
4) Can telnet connect on port 22 (or whatever port you tell sshd to bind to)? The command is: ```
telnet <sshd_host_name_or_ip_address> <port>
```

If telnet times out, then either sshd isn't up or it isn't configured properly.

Good idea trying telnet.

> **DJYoshaBYD said:**
> 
You should probably forward UDP, as well.. 

You wouldn't need to forward UDP, as SSH uses TCP.

---

### Post by bodhi.zazen on 2010-07-04
> **CharlesA said:**
> You wouldn't need to forward UDP, as SSH uses TCP.

I was just going to post this comment ^^

---

### Post by jv2112 on 2010-07-04
The Sever was not set up on one of the two machines I was working with. All set now. :p

Do I need to keep port forwarding set ?

Thanks Again !!!!:guitar:

---

### Post by CharlesA on 2010-07-04
You only need to use port forwarding if you are connecting from a remote location and not your local LAN.

---

### Post by jv2112 on 2010-07-05
Thanks !

---

### Post by mikeyb22 on 2010-07-27
Hi,

I came across this thread whilst trying to solve my own ssh problem, hopefully there's somebody out there who can help!

Basically, when I try to ssh into my laptop I get the message

[PHP]ssh: connect to host 10.172.xxx.x port 22: Connection timed out[/PHP]I was previously using my computer with a different wireless network and had no problems. I also have no problems sshing from my laptop. I'm pretty new to ssh so any help would be gratefully received!

Cheers,

Mike

---

### Post by jv2112 on 2010-07-30
Do you have openssh-server on the machine you are trying to reach ?

I finally figured out that was my issue. 

Hope that helps

---

