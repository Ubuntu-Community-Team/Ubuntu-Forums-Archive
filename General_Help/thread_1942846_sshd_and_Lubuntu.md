---
title: "sshd and Lubuntu"
date: 2012-03-18
forum: General Help
---

### Post by davidstoll on 2012-03-18
What am I missing here?  I ssh all the time into many different machines.  I've even changed the port on some of my machines.  However, I can't ssh into either of my Lubuntu machines.  It says openssh-server is installed.  I have a conf file.  I get this when I try to ssh into an Lubuntu machine (even on the same network):

ssh: exited: Error connecting: Connection refused

---

### Post by Lars Noodén on 2012-03-19
Are you still getting the error?  If so, are you sure that sshd is even running on the server?


```

pgrep -l sshd

```

---

### Post by davidstoll on 2012-03-19
$ pgrep -l sshd
442 sshd

---

### Post by Lars Noodén on 2012-03-19
Do you have a firewall blocking incoming connections on port 22 or have you moved sshd to a new port?

---

### Post by davidstoll on 2012-03-19
> **Lars Noodén said:**
> Do you have a firewall blocking incoming connections on port 22 or have you moved sshd to a new port?

No to both questions.  I have changed SSH ports on Ubuntu and have setup firewalls on Ubuntu, but have not done either on Lubuntu.

The only port changing I have done on Lubuntu is to change VNC ports...not very much else with regards to customization.

---

### Post by Lars Noodén on 2012-03-19
Ok.  How about more obvious stuff like if you are using the right hostname/IP address?  Does the output from ifconfig on the lubuntu machine match the number you are trying to connect to from the other machines?

---

### Post by davidstoll on 2012-03-19
> **Lars Noodén said:**
> Ok.  How about more obvious stuff like if you are using the right hostname/IP address?  Does the output from ifconfig on the lubuntu machine match the number you are trying to connect to from the other machines?

That is a good question, but yes my ifconfig match what I'm trying to ssh into.  192.168.1.whatever.

I can ssh into my router running dd-wrt (remotely or locally).  I can ssh from there to my Mythubuntu (Xubuntu) and Ubuntu machines just fine....and between each other.

---

### Post by Lars Noodén on 2012-03-19
Can you ssh internally on your Lubuntu box to itself via localhost or 127.0.0.1 ?  How about grabbing the keys while still on the Lubuntu machine?

```

[s]ssh -t rsa 127.0.0.1[/s]
ssh 127.0.0.1

```

Edit: should read "ssh-keyscan -t rsa 127.0.0.1"

---

### Post by davidstoll on 2012-03-19
> **Lars Noodén said:**
> Can you ssh internally on your Lubuntu box to itself via localhost or 127.0.0.1 ?  How about grabbing the keys while still on the Lubuntu machine?

```

ssh -t rsa 127.0.0.1
ssh 127.0.0.1

```

Good suggestion, I never tried that...very interesting too...

```
$ ssh -t rsa 127.0.0.1
ssh: Could not resolve hostname rsa: Name or service not known

$ ssh 127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused

$ ssh 192.168.1.100
ssh: connect to host 192.168.1.100 port 22: Connection refused
```

---

### Post by Lars Noodén on 2012-03-19
Again, I'm not sure that sshd is even running, you should have been able to connect locally.

```

/etc/init.d/ssh  status

```

(PS.  I corrected an omission in my post above regarding ssh-keyscan.)

Maybe you can watch the output from sshd while you try to make a connection using the debug mode:

```

sudo /etc/init.d/ssh stop
sudo /usr/sbin/sshd -dd

```

---

### Post by Lars Noodén on 2012-03-19
Which port is it listening to in /etc/ssh/sshd_config ?

---

### Post by davidstoll on 2012-03-19
> **Lars Noodén said:**
> Which port is it listening to in /etc/ssh/sshd_config ?

ha, there it is....

But here's the thing...I didn't change that and both the computers running Lubuntu are not using port 22.  Why would that be?

Anyway, I appreciate your help with this.  Sorry it was so simple.

But, like I mentioned, I have changed ports for Ubuntu and MythBuntu, but not Lubuntu...strange.

---

