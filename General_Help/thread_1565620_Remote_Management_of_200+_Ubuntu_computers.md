---
title: "Remote Management of 200+ Ubuntu computers"
date: 2010-09-01
forum: General Help
---

### Post by SknarTiT on 2010-09-01
Hi

I have 200+ windows computers set up in many different locations, behind firewalls in different countries. They are all running windows today with Logmein for remote management. 
Im thinking of moving to linux to save the cost of windows licenses and to get a more stable system.

But I find it hard to find a stable solution for remote management.
As most of the staff is not familiar with linux Im in need of a system where they can log inn and see the whole desktop, not just using the terminal.

Anyone have some ideas or solutions that would solve this?

The one solution Ive made some progress with is setting up a reverse ssh tunnel from the clients and connecting remote desktop from a sentral server. Dont like the fact that if the server goes down, i cant access them. And Ive not figured out yet how I can use VNC on a third machine that connects to the servern and then gets directed to the client.

---

### Post by surfer on 2010-09-01
i use [FAI]("http://www.informatik.uni-koeln.de/fai/") for installation and [puppet]("http://www.puppetlabs.com/") for the management. but these are just the tools and will not solve your firewall issues...

---

### Post by madverb on 2010-09-01
Look into Zentyal.

[www.zentyal.org](www.zentyal.org)

---

### Post by Joe of loath on 2010-09-01
Would this help?

[http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape/systems-management](http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape/systems-management)

---

### Post by SknarTiT on 2010-09-05
Thanks all, will look into your suggestions. 

Been using TightVNC Java Viewer SSH for a couple of days now and it looks to be pretty stable.

---

### Post by karnamonkster on 2010-10-04
HI,
 
My major issue is currently deploying the image to around 3000 clients.
please let me know how can i reduce the time involved.

---

