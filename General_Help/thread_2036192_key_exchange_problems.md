---
title: "key exchange problems"
date: 2012-08-01
forum: General Help
---

### Post by marjenni on 2012-08-01
Hi,
I have three machines, A, B and C.
 
From machine A I can scp files to machine C without being prompted for a password.
 
From machine B, I am always prompted for a password when scp'ing files to machine C, and I am unable to see why this is.
 
What is the easiest way of fixing this?
 
best regards
 
Mark

---

### Post by Lars Noodén on 2012-08-01
Probably on machine C you have loaded a public key from A in [font=Courier New]~/.ssh/authorized_keys[/font] but haven't in B.  Check to make sure your public key is loaded on B.

---

### Post by Cheesemill on 2012-08-01
Make sure you have copied the correct key across. From machine B:
```
ssh-copy-id user@MachineC
```

---

### Post by marjenni on 2012-08-02
Ah thank you, ssh-copy-id looks like what I need. With [EMAIL="user@MachineC"]user@MachineC[/EMAIL] , should I use an IP address for machineC, or should machineC be in known_hosts. If so, how do I put it in known_hosts, or even tell if it is already there?
 
many thanks
 
Mark

---

### Post by Lars Noodén on 2012-08-02
> **marjenni said:**
> Ah thank you, ssh-copy-id looks like what I need. With [EMAIL="user@MachineC"]user@MachineC[/EMAIL] , should I use an IP address for machineC, or should machineC be in known_hosts. If so, how do I put it in known_hosts, or even tell if it is already there?
 
many thanks
 
Mark

With [ssh-copy-id](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-copy-id.1.html) MachineC can be either the hostname or ip number for the machine.  

About [font=Courier New]known_hosts[/font] on MachineA, you can use [ssh-keygen](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-keygen.1.html) to see if MachineC is there.  On MachineA:

```

ssh-keygen -F MachineC

```

If the key for MachineC is not there in [font=Courier New]known_hosts[/font] or in [font=Courier New]/etc/ssh/ssh_known_hosts[/font], you will be given the option of adding it when you first connect.

---

### Post by marjenni on 2012-08-02
Hi,
I run:
ssh-copy-id "[EMAIL="root@xxx.xxx.xxx.xxx -p 1022"]root@xxx.xxx.xxx.xxx -p 1022[/EMAIL]"
 

Now try logging into the machine, with "ssh [EMAIL="'root@xxx.xxx.xxx.xxx"]'root@xxx.xxx.xxx.xxx[/EMAIL] -p 1022'", and check in:
  .ssh/authorized_keys
to make sure we haven't added extra keys that you weren't expecting.
 
 
So I enter:
ssh [EMAIL="root@xxx.xxx.xxx.xxx"]root@xxx.xxx.xxx.xxx[/EMAIL] -p 1022
 
but I am prompted for a password again.
 
Any ideas?
 
best regards
 
Mark

---

### Post by Lars Noodén on 2012-08-02
You need to specify the key when trying to log in.

```

ssh -i ~/.ssh/*machinec_rsa* -p 1022 root@*machinec*

```

Normally, keys are in [font=Courier New]~/.ssh/[/font], but if you have the key somewhere else on machine A, use that path.

If that does not work, check manually on machine C that you have the key properly entered in [font=Courier New]~/.ssh/authorized_keys[/font] in root's directory.  If you are using the key to log in as root, then your key needs to be under root's directory.

---

### Post by marjenni on 2012-08-02
machine C: authorized_keys contains the line that is in machines B id_rsa.pub
 
yet I am still being asked for a password. What is the next step? This is confusing me!
 
best regards
 
Mark

---

### Post by Lars Noodén on 2012-08-02
Are you sure that it is the root account that you placed the key?  That's where it needed to go if you are connecting as root.

---

### Post by marjenni on 2012-08-07
Ah problem solved. There were two public keys in my .ssh directory, id_rsa.pub and id_rsa.pub.bak. It turns out that id_rsa.pub.bak was the real key to use.
 
Many thanks

---

