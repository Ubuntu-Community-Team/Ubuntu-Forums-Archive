---
title: "SSH Between Two Home Computers"
date: 2009-11-13
forum: General Help
---

### Post by kingdogbert on 2009-11-13
As is likely with many others here, I have defaulted to the role of tech support for my family. I've been steadily convincing everyone to switch to Linux (:D), and now I want to take the next logical step. I want to be able to SSH to their machines for remote administration since they all live 500mi away.

Here's the setup. All machines (including mine) are behind NAT'ed routers. The machines run a mix of Linux based on what I thought was appropriate for each user (Ubuntu, Mint, and Mandriva). I have admin access to all machines and all routers (and thanks to the upcoming holidays, I'll have local access for performing any required configuration). All routers have dynamic IPs.

I've read about reverse tunneling, but I don't have a server I'm comfortable using (I could use Georgia Tech's servers since I'm a student there, but I don't know that they'd be happy about it, and it's not a long term solution as I will be graduating at some point), and it seems overly complicated anyways, given the level of access I have to the equipment involved. Is reverse tunneling my best bet, or is there a better way? Thanks

---

### Post by egalvan on 2009-11-13
.errors

---

### Post by Lars Noodén on 2009-11-16
> **kingdogbert said:**
> 
Here's the setup. All machines (including mine) are behind NAT'ed routers. The machines run a mix of Linux based on what I thought was appropriate for each user (Ubuntu, Mint, and Mandriva). I have admin access to all machines and all routers (and thanks to the upcoming holidays, I'll have local access for performing any required configuration). All routers have dynamic IPs.


Depends on how you want to go about things.  If there are dynamic ip numbers all around and no one has a static number, 

1) You could set up key-based authentication to your machine that they could fire up on demand and use to create a reverse tunnel back to their machine.  That would require using dyndns (or equivalent) or telling them on a case by case basis what your current ip number happens to be. You'd have to configure your modem or switch to allow an incoming connection and turn on sshd and open that port in your firewall on the occasions you want them to connect.   

2) Or you could set up key-based authentication to their machines.  That will take a bit of planning if there is more than one machine per home.  You have to have the router or modem accept an incoming connection from the outside world and forward it to the port used by ssh on the appropriate machine.  

Either way: use keys and don't allow login as root

---

### Post by kingdogbert on 2009-11-16
> **Lars Noodén said:**
> Depends on how you want to go about things.  If there are dynamic ip numbers all around and no one has a static number, 

1) You could set up key-based authentication to your machine that they could fire up on demand and use to create a reverse tunnel back to their machine.  That would require using dyndns (or equivalent) or telling them on a case by case basis what your current ip number happens to be. You'd have to configure your modem or switch to allow an incoming connection and turn on sshd and open that port in your firewall on the occasions you want them to connect.   

2) Or you could set up key-based authentication to their machines.  That will take a bit of planning if there is more than one machine per home.  You have to have the router or modem accept an incoming connection from the outside world and forward it to the port used by ssh on the appropriate machine.  

Either way: use keys and don't allow login as root

Let me see if I understand this. Basically, I need to pick one computer to be the SSH server, set up the router to forward accordingly, and use dyndns to find that server from all the other computers, correct? I prolly should have been able to imagine such a setup from the reverse tunnel articles, hehe. 

A related question, for the purposes of teaching them how to do things, is there a way to share a single desktop (so they see the same mouse movements and windows that I do, for example)?

---

### Post by prem1er on 2009-11-16
Yes, look at remote desktop. Again you need a "server" set up on the machine you want to remote into and a client set up on the machine you will be using. Take a look at [this]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html") for getting remote desktop to work on the ubuntu based machines.

---

### Post by Lars Noodén on 2009-11-17
> **kingdogbert said:**
> Let me see if I understand this. Basically, I need to pick one computer to be the SSH server, set up the router to forward accordingly, and use dyndns to find that server from all the other computers, correct? 


Yes, and the connections from their machines to yours are made manually.  

1)
```

        **A**              **B**                      **C**         **D**
      +----+
      |ssh |
desk1 |sshd+----+
      +----+    |
                |    +---+                  +---+
      +----+    |    | s |                  | s |    +-----+
      |ssh |    |    | w |                  | w |    |sshd |
desk2 |sshd+----+----+ i +---- Internet ----+ i +----+     | desk1
      +----+    |    | t |                  | t |    | ssh |
. . .           |    | c |                  | c |    +-----+
      +----+    |    | h |                  | h |
      |ssh |    |    +---+                  +---+
desk*n* |sshd+----+
      +----+

```


If you do it right, they only have to run (click on) a script and enter their key's passphrase and then you can log in.  

You would be at D above.  When others over on A want help, they contact you and you turn on sshd on D.desk1.  Then you set the switch C to forward a specific port, say 22, to sshd.  Then you lookup your current IP address for C, or use dyndns or equivalent and tell it to them.  

Then they use a script you wrote for them as a shortcut to use the key you made for them to connect from their machine on A to your switch C.  The script should include the settings to forward one port from your machine on D to one port on their machine on A.  Say port 4222 on D and 22 on A.  

```

#!/bin/sh
echo YMMV; exit;
 **ssh** -o "ServerAliveInterval=60" \
  -N \
  -f \
  **-i** ~/.ssh/tunnelkey \
  **-R** 4222:localhost:22 \
  *xx.yy.zz.aa*
```

Since you set C to forward the port to D, it appears to A that they are connecting to D.

Then you connect to the local port on your machine on D that A is forwarding and log into your account on A using your key.  

You may want to lock down the server a bit on D by putting these tunnel users into their own group (e.g. 'tunnelers') and then limiting access using Match

```

Match Group tunnelers
   ChrootDirectory %h
   ForceCommand internal-sftp

```

Giving them the shell /bin/rbash or /bin/false might be an idea, too.

---

