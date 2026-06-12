---
title: "sudo ssh starts two processes"
date: 2012-04-20
forum: General Help
---

### Post by Jim Lavella on 2012-04-20
I am running Windows 7 (64bit), VMware 4.0.2 and Ubuntu 11.10 (32bit).

I use "sudo ssh" to set up a 'tunnel' of port 80 from another machine to mine.
The command looks like this:
sudo ssh -p 52000 -o ServerAliveInterval=30 -L my-machine-ip:80:target-machine-ip:80 [email]userlogin@target_machine.com[/email]

When I run ps -ef on my machine, I notice two SSH processes running under root.  One is for 'sudo ssh' and the other is for just 'ssh'.

Does anyone know what is causing this and how to correct it?

---

### Post by bhutz on 2012-10-25
Did you ever figure out why this happened...is it normal when you run a sudo command for a command it displays twice in the process list (ps -aux)

From what I can see it is, the command "sudo nano" resulted in two processes being displayed.

---

