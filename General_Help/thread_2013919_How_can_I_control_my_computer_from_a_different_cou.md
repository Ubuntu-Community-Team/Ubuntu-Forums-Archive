---
title: "How can I control my computer from a different country?"
date: 2012-07-01
forum: General Help
---

### Post by helloalternative on 2012-07-01
I have been setting up my old laptop with ubuntu for my grandma. Her computing capabilities are very limited so I am trying to automate almost everything that she might want to do. I wanted to know if there is a, hopefully easy, way of accessing this computer from another computer even though I am in a different country? This way I can make sure that my grandma doesn't get stuck and doesn't have to wait for a year or so for me to see her and fix up her laptop again. 

Any help is greatly appreciated.

---

### Post by LeftFoot on 2012-07-01
This is a rough answer, you will have to do some homework :


-1. Install openSSH server on your grand'ma station (apt-get install openssh-server)
That way if you have a network connection to that station you can connect to it from a terminal with the following command:
ssh <IP address of the station> 
It will ask you for a login/password : be sure to use a secure password

-2. On your grand'ma router you need to define a connexion so you can connect from the Internet.
This heavily depend on her internet setting (statics public IP or not...)
Be VERY carefull about security as you do NOT want anybody to be able to ssh in your grand'ma station.

Hope this help

Have fun !

LeftFoot

---

### Post by PaulW2U on 2012-07-01
> **helloalternative said:**
> I wanted to know if there is a, hopefully easy, way of accessing this computer from another computer even though I am in a different country?

You can find some pretty comprehensive instructions at [https://help.ubuntu.com/community/SSH/](https://help.ubuntu.com/community/SSH/).

---

### Post by cybergalvez on 2012-07-01
Let me tell you how I do the same thing with my mom in a different state. I 
1) first set her up with a free domain name from dyndns and installed ddclient so that it will remain updated.
2) installed sshd on a port other than 22 (not great security I know)
3) make sure that the ssh port was open on her router
4) set up vino to only accept loopback and then conect to it via ssh tunnel. I do this when she has questions, it is much easier to see what she is doing then try to understand her questions
5) install x2go and log in in th background into my account on her computer to do general maintaince.

This all works really well and has made workng on her machine super simple. Note that x2go does not do 3d so the "gnome" command won't really work and you will have to use a different command to start the desktop session. something like: gnome-session --session=gnome or one of the of other sessions that may de defined on her computer.

Good luck

---

### Post by raja.genupula on 2012-07-01
[http://ubuntuguide.org/wiki/Ubuntu_Precise_Remote_Access](http://ubuntuguide.org/wiki/Ubuntu_Precise_Remote_Access)

---

### Post by helloalternative on 2012-07-02
wow thank you guys, this is excellent! As soon as I am with here I'll get cracking.

cheers

---

### Post by dino99 on 2012-07-02
hey drop your grand'ma on the cloud :p

[https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by spcwingo on 2012-07-02
Team Viewer FTW!

[http://www.teamviewer.com/en/indexa.aspx]("http://www.teamviewer.com/en/indexa.aspx")

---

### Post by QIII on 2012-07-02
I would highly recommend against using an SSH password.  Set up OpenSSH and disable passwords.

I would use a 4096 bit public/private key combination and only use a password for the actual X session login if you do X forwarding or similar.

I use NoMachine NX 3.5 for graphical access.  4.0 is still in testing.

Also, use DenyHosts or something similar to help prevent unauthorized log in attempts.

---

### Post by Grenage on 2012-07-02
> **QIII said:**
> I would highly recommend against using an SSH password.  Set up OpenSSH and disable passwords.

I would use a 4096 bit public/private key combination and only use a password for the actual X session login if you do X forwarding or similar.

I use NoMachine NX 3.5 for graphical access.  4.0 is still in testing.

Also, use DenyHosts or something similar to help prevent unauthorized log in attempts.

+1 to the above; I'm a fan of NoMachine.

---

### Post by QIII on 2012-07-02
The only thing about NX 3.5 is that it uses 2048 bit encryption.  Risk assessment is always a factor.

---

### Post by QIII on 2012-07-02
Oh, also.  With port forwarding on her router, only allow traffic from a list of known IPs if you only plan to access her machine from one place, like your machine at home.

Nothing can make you completely secure.  Use a lot of tools to cover as much of the perimeter as possible.

---

### Post by steve7777777 on 2012-07-03
> **spcwingo said:**
> Team Viewer FTW!

[http://www.teamviewer.com/en/indexa.aspx]("http://www.teamviewer.com/en/indexa.aspx")

Opinions on Teamviewer? Is it a security concern?

---

### Post by 3Miro on 2012-07-03
If you can and want to use CLI, use SSH. It is robust and secure and it doesn't need much of a connection to be smooth.

I would also use NX, it is slower as it requires more traffic over the Internet, but it works and you can use GUI.

I mostly use SSH, but when I am on a very fast network, I use NX (by fast, I mean crossover cable).

---

### Post by Easy Limits on 2012-07-03
> **spcwingo said:**
> team viewer ftw!

[http://www.teamviewer.com/en/indexa.aspx](http://www.teamviewer.com/en/indexa.aspx)

+1

---

### Post by cipherboy_loc on 2012-07-03
I personally like SSH, considering most of my tasks can be done via console. However, for the few times I need a specific GUI application, I tunnel it via SSH. 

Example, gedit:
```

ssh user@host.com -X gedit

```It should be less traffic than an entire remote desktop, but with the security of SSH. Should have fairly smooth integration for everything, especially going Unix/Linux to Unix/Linux (Unixs including Mac).

Cipherboy

---

### Post by spcwingo on 2012-07-04
> **steve7777777 said:**
> Opinions on Teamviewer? Is it a security concern?

I've had nothing but puppy dogs and rainbows from TeamViewer.  :lolflag:

---

### Post by Deuce1912 on 2012-07-04
I also use Teamviewer, and have never had a problem using it. I've set it up to start on boot so its always on. Great program and I highly recommend it.

---

