---
title: "ssh problems. Reporting strange hostname when restarting"
date: 2009-11-02
forum: General Help
---

### Post by DanielReidal on 2009-11-02
I just installed 9.10 and open ssh server.

When I try to restart ssh after editing the sshd_config I get
this message

ssh: Could not resolve hostname restart: Name or service not known 

Or when I try to stop ssh:
ssh: Could not resolve hostname stop: Name or service not known

What does it mean by "hostname stop"? 

I have configured for static ip in my home network. And the machine is really a fresh install.

ssh is running, I can connect to it from my windows computer, with no problems...I have edited sshd_config with AllowUsers

I can't remember I have had these problem before...But I am a newbie...;)

Cheers Daniel

---

### Post by nikgare on 2009-11-02
Please can you post the contents of your **/etc/hosts** file

---

### Post by dcstar on 2009-11-02
> **DanielReidal said:**
> I just installed 9.10 and open ssh server.

When I try to restart ssh after editing the sshd_config I get
this message

ssh: Could not resolve hostname restart: Name or service not known 

Or when I try to stop ssh:
ssh: Could not resolve hostname stop: Name or service not known

What does it mean by "hostname stop"? 
........

It means you are trying to use the ssh **client** to connect to host "stop". Read the man page for correct command syntax:

```
man ssh
```

---

### Post by DanielReidal on 2009-11-03
Ok solved! Thanks for your support!

I did not understand when to use ./ or not

dradmin@drServer:/$ sudo etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                       [ OK ] 
dradmin@drServer:/$ cd etc/init.d/
dradmin@drServer:/etc/init.d$ sudo ssh restart
ssh: Could not resolve hostname restart: Name or service not known
dradmin@drServer:/etc/init.d$ sudo ./ssh restart
 * Restarting OpenBSD Secure Shell server sshd                       [ OK ]

---

