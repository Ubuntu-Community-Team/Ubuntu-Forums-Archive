---
title: "Problem with ping"
date: 2012-07-04
forum: General Help
---

### Post by benglish on 2012-07-04
Hi pals!
when i use the command 
      ping google.com
i face an error with the following message:
      unknown host google.com

what's the problem? what should i do to fix it?
i'm just new to ubuntu 10! Please help me!!!

---

### Post by msammels on 2012-07-04
Hey benglish,

Welcome to the forums, and Ubuntu! OK - your error means you have a problem with your DNS server. How are you connecting to the internet? Is it wireless or wired?

---

### Post by benglish on 2012-07-04
TNX for your quick reply

I'm running Ubuntu 10 on a virtual machine (VMWare) and my connection is wired.

My host OS is Windows 7. When I ping in this OS, it works correctly, but when I use Ubuntu10 to ping, i face the mentioned error.

---

### Post by msammels on 2012-07-04
OK, a VMWare issue. How does your network setup in VMWare's virtual machine settings look? Is it host-only, NAT, or what?

---

### Post by benglish on 2012-07-04
It is bridged.

---

### Post by msammels on 2012-07-04
Try switching it to NAT, restart the VM and see if that solves your problem.

---

### Post by benglish on 2012-07-04
I am using it in bridged mode because the project I'm working on needs it to be in this mode. I shouldn't change it to NAT or some other things. Any other solutions?
Please help me. it's really necessary.

---

### Post by msammels on 2012-07-04
OK, sure, no worries. Maybe [this thread](http://ubuntuforums.org/showthread.php?t=1207862) will help you? :)

---

