---
title: "Virtualbox crash"
date: 2011-07-31
forum: General Help
---

### Post by mrnettles on 2011-07-31
Hello,  I had Windows XP running fine on Virtualbox, but it's started crashing. This happens instantly when I try to startup the virtual machine. It doesn't get anywhere near booting up. Total crash, no ctrl-alt-del on host. I've tried reducing the RAM and number of processors but it doesn't help. I hadn't changed anything when the problem started. 

Virtualbox Version 4.0.12   
NAT network  
Host kernel Linux 2.6.35-30-generic-pae(i686), distro Ubuntu 10.10      

Help appreciated as I would like to sync my phone and also use Rosetta Stone without having to start from scratch with a dual boot. I can't face another reinstall!

---

### Post by coldraven on 2011-07-31
No real idea except you could try exporting the VM and then re-import it.
Maybe Virtual box would "clean up" something in the process.
I make a backup of my XP VM onto my external drive like that, just in case of accidents.
On my laptop the export always starts by saying it will take two hours but actually takes about 10 minutes.
Or you could take the opportunity to upgrade to VBox 4.1 which has a handy clone VM option. 
I mean clone it after you have fixed it.

---

### Post by jerrrys on 2011-07-31
not even a black screen?

---

### Post by mrnettles on 2011-08-01
No, it instantly freezes with whatever is on the screen at the time. I don't think exporting and importing will work because I've already tried reinstalling the host and the VM.

---

### Post by mrnettles on 2011-08-03
Coldraven, the exporting and importing worked! Thanks!  I'd still like to know what's going on though.  Jerrrys, do you mean black screen on Vbox? Yes, it did get that far.

---

### Post by mrnettles on 2011-08-20
Well, it worked for a bit. Now the same thing's happening again. Has this happened to anyone else?

---

