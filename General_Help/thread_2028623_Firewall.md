---
title: "Firewall"
date: 2012-07-18
forum: General Help
---

### Post by rickm1945 on 2012-07-18
I have to start the firewall each time I boot-up, and if I close the configuration window I have to restart the firewall. Doesn't the default firewall stay on?

---

### Post by rukiaEnix on 2012-07-18
Hello,

What firewall and what OS are you using?

---

### Post by ajgreeny on 2012-07-18
What you are really doing is starting the firewall configuration application (ufw, gufw?) not the firewall itself, a common misconception when moving from Windows to Ubuntu.

The firewall is actually **iptables**, not ufw, gufw, or whatever it is that you run at startup.  I do not run anything over and above the default that Ubuntu gives you at installation, and never have in my 7 years of using Ubuntu.  If you are not running any kind of outward facing server which connects direct to the net and allows inward traffic, you probably are worrying unnecessarily.

See ```
man ufw
``` for details of how to use ufw, and note this paragraph:-
> NOTES
       On installation, ufw is disabled with a default incoming policy of deny and a default outgoing  policy  of  allow which put simply means that you can send data out, but unless you ask for it, nothing will come inward.

---

### Post by rickm1945 on 2012-07-18
> **rukiaEnix said:**
> Hello,

What firewall and what OS are you using?
OS= Ubuntu 12.04 Precise Pangolin and using firewall that came with the OS. Is there a better one?

---

### Post by rukiaEnix on 2012-07-18
The best is to use IPTABLES.

What I do to keep my configuration when booting is create a file where I  have the iptables rules. And I load that file with the network interfaces file.

---

### Post by rickm1945 on 2012-07-18
> **ajgreeny said:**
> What you are really doing is starting the firewall configuration application (ufw, gufw?) not the firewall itself, a common misconception when moving from Windows to Ubuntu.

The firewall is actually **iptables**, not ufw, gufw, or whatever it is that you run at startup.  I do not run anything over and above the default that Ubuntu gives you at installation, and never have in my 7 years of using Ubuntu.  If you are not running any kind of outward facing server which connects direct to the net and allows inward traffic, you probably are worrying unnecessarily.

See ```
man ufw
``` for details of how to use ufw, and note this paragraph:-
 which put simply means that you can send data out, but unless you ask for it, nothing will come inward.
So how do I enable the firewall. All I want to do is make sure it is on and my machine is protected.  I don't need any additional settings just nothing in and everything out.

---

### Post by rukiaEnix on 2012-07-18
If you want everything out and anything in, then you have to make several settings even if you don't want to.

---

### Post by deadflowr on 2012-07-18
In a terminal:

```
sudo ufw enable
```

To check if it is running:

```
sudo ufw status
```

If running it will say active, if not it will say inactive.

To turn off:

```
sudo ufw disable
```

run man ufw to get more info on how to set it to more advanced levels, or read up on iptables such as this:
[http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

---

### Post by ajgreeny on 2012-07-18
> **rickm1945 said:**
> So how do I enable the firewall. All I want to do is make sure it is on and my machine is protected.  I don't need any additional settings just nothing in and everything out.
That is actually what you get when you install Ubuntu, but if you want just open a terminal and run ```
sudo ufw enable
``` If you had looked at **man ufw** as I suggested, you would already know this.

---

### Post by rickm1945 on 2012-07-19
> **ajgreeny said:**
> That is actually what you get when you install Ubuntu, but if you want just open a terminal and run ```
sudo ufw enable
``` If you had looked at **man ufw** as I suggested, you would already know this.
I did see it in the manual, and it is fine. thanks for the assistance.

---

