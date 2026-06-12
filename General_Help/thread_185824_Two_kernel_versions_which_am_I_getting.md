---
title: "Two kernel versions: which am I getting?"
date: 2006-06-01
forum: General Help
---

### Post by Gomek on 2006-06-01
Alright, I have an alternate install CD for Dapper Drake.  Since the packages I desire are quite a bit different than the default Ubuntu installation (Fluxbox and stuff), I "Install a server."  With this option on the alternate install CD, am I getting the kernel version that has been fine-tuned for server applications?  Cuz I'm not using server applications, at least on this machine.

Anyone have any clue which version I'm getting, how I can tell, or whether it really even matters?

---

### Post by Gomek on 2006-06-01
bump

---

### Post by ubnoobie on 2006-06-01
if you install the "server" off an alternate iso for ubuntu, kubuntu, or xubuntu, you should get a clean ( as in bare, empty, no gui, etc ) install using the standard desktop kernel. the server-optimised kernel is on the server iso. 

don't confuse the "server" install on a regular alternate iso with the "server edition" of ubuntu.

regardless of what kernel gets installed, it is fairly easy to replace it with one better suited for your hardware, such as the k7 kernel for athlons, etc...

---

### Post by Gomek on 2006-06-01
Ah, very good.  Thank you.  I was hoping for that answer.

---

### Post by jonibo on 2006-06-01
Try the following on the command line:

uname -a

It should give you some information about the kernel you have installed.  Post the output here and someone will tell you what you have got, if it's not obvious...

---

### Post by Gomek on 2006-06-01
Linux test 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Anyone know what the server version output looks like?

---

### Post by thasheep on 2006-06-01
That's a 'normal' kernel - designed to run just about anything. If you have recent hardware you probably want a different kernel. Each on is called linux-image-something. The ones without version numbers, such as linux-image-386 rather than linux-image-2.6.15-23-386 will always depend on the latest version. Install the packages without version numbers and the most recent of the corresponding one with a version number (the actual kernel) will be installed. For best performance you probably want the 686 (pentium II/III/IV/celeron/m/etc) or k7 (amd athlon) version. Keep the 383 one installed as a backup, just choose the new one at boot time. To install a new kernel, you can use synaptic (system>admin>synaptic package manager) or from a terminal
```
sudo apt-get install linux-image-686
```

---

### Post by gimpologist on 2006-06-22
The Ubuntu Server kernel from the server iso once installed to the HD is 2.6.15-23-server.

It would be great if we could get more information on the server kernel because I would love to know if it's better use the default kernel for my server install or to install the linux-image-686 kernel.  Or is the server kernel already optimized for 686 as well as web serving, databases, file sharing, etc. and we just don't know.

---

