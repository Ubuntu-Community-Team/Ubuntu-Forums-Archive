---
title: "Can I transfer data through enthernet cable between two computers?"
date: 2012-01-19
forum: General Help
---

### Post by Jaxke on 2012-01-19
Okay, so as the title says, I need to transfer files from computer to computer(laptop-desktop, both have Ubuntu 11.10 installed) **without internet**.

So today I decided to throw away my old desktop computer, but I had  a cruel idea; why wouldn't I use it as my external hard drive... That means I want to transfer files from my laptop to this desktop computer, but it would take forever with small USB drives. 

Is it possible to transfer files over enthernet(RJ45 I suppose) cable, with the other PC(the desktop) having no internet connection? Is there any good software? And yes, of course I do have internet connection on my laptop ;)

Thank you :guitar::)

---

### Post by lincoln32 on 2012-01-19
yes----but set a static ip on both machines so that they can talk to each other. I have never had to do this but it should work. I usually use a router to serve up IP addresses so that I do not need to connect directly
P.S. others may have a better idea just my ideas:D

---

### Post by JRV on 2012-01-19
Lincoln32 is right about setting up static IPs on both boxes.
And you will need a crossover cable, not a standard ethernet cable.

---

### Post by ajgreeny on 2012-01-19
Assuming the two machines are connected to a router you may find transfer-on-lan is worth looking at.  Get it from [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list)

---

### Post by Hylas de Niall on 2012-01-19
Wow! That sounds like the old 'null-modem' hookup i used to use to play Doom back in the day... :D

---

### Post by Morbius1 on 2012-01-19
Another option in the "Transfer-On-Lan" category is Dukto: [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list)

Although I've never used it this way it appears that you can use it without a router:
> **How it works?**

Dukto  usage is very simple, just start it on the two PC connected over the  LAN (**or directly connected**). On the buddy list will be showed the other  peer. Now simply drag and drop your files and folders over the dukto  window and they'll be transferred to the other end. That's all. 
I actually prefer Transfer-On-Lan since it's java based and as long as java is installed you just run a jar file. Duckto doesn't use java so it's found itself in a bit of a problem - having to create different versions for different OS's - Fedora, Ubuntu, Windows, OSX.... But in this case it's both Ubuntu.

---

### Post by CharlesA on 2012-01-19
> **ajgreeny said:**
> Assuming the two machines are connected to a router you may find transfer-on-lan is worth looking at.  Get it from [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list)

This sounds interesting. I just use Samba, myself, but that would probably be easier to deal with, if it's just one person moving data back and forth.

If the machines aren't hooked up to a router, you can use a straight-thru cable if both machines are use gigabit ports, which they might be, but it's still worth noting. :)

---

### Post by Jaxke on 2012-01-21
Ok, thank you guys for the info. I'mma try Dukto right now... :)

---

