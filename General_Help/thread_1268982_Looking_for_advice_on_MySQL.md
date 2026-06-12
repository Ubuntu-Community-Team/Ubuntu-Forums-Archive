---
title: "Looking for advice on MySQL"
date: 2009-09-17
forum: General Help
---

### Post by colinireland on 2009-09-17
Hey,

I have just started a postgrad in software design last week. We will be studying database development (mysql). My question is can I install mysql on a laptop? I dont have a desktop. The computer labs in university are all set up for this kind of study but I live an hour drive away from the campus and will have to do most of my work from home. Any advice on what my best options are would be greatly appreciated. Is it possible to install a LAMP server on a laptop (Im new to ubuntu, its proba crazy question!!!)

Thanks,
Colin

---

### Post by gishaust on 2009-09-17
Oh yes  I have done this many times. What os is on your laptop.

---

### Post by aka_bigred on 2009-09-17
You can definitely setup on a laptop, but maybe you would be best finding an old PC for cheap on craigslist.org and leave it as a dedicated machine.  That way if you mess something up, you can still use the laptop. :)

If you can't or don't want to do that, I would suggest setting up a virtual machine.  If you are running Windows, go download [Qemu Manager]("http://www.davereyn.co.uk/download.htm").  It's pretty easy to setup, and it will let you create & trash virtual PC's without worrying about messing up your laptop.

---

### Post by colinireland on 2009-09-17
I have 9.04. I just used virtualbox to install Ubuntu 9.04 server. It seems to work fine. I get the terminal but I cant get startx to work and im not very comfortable working with the terminal. Is it possible to get the server running graphically?

---

### Post by DaithiF on 2009-09-17
of course you can install the LAMP stack on your laptop.  Theres no need to install the server version to do this, Desktop will do just fine.  Once/if you've built a real-world, compute-intensive app used by thousands of people then you'll probably want to run it on a dedicated server machine :) , but while learning theres nothing about the desktop edition that means it isn't suitable for this kind of activity.

---

### Post by yknivag on 2009-09-17
Installing ubuntu within ubuntu as a virtual machine seems like a very long winded way of getting a LAMP server.

Personally I just run apache, php and mysql on my laptop. You can install all three from Synaptic with just a few mouse clicks. You may find it useful to install phpmyadmin too (a web based mysql management tool).

---

### Post by colinireland on 2009-09-18
Thats great to hear. Thanks for the help lads :)

---

### Post by colinireland on 2009-09-18
One more question, If I install LAMP is my laptop alot more vulnerable to hackers etc? Is it possible to turn off the LAMP server when its not in use or will I constantly have more open ports then is necessary?

---

### Post by yknivag on 2009-09-18
It depends really on what you mean by "open".  The ports will be open and listening on the machine, but whether they will be available to the outside world depends on how you connect.  Assuming you're connected on broadband with a router then all ports will likely be closed to the outside world unless you expressly open them and forward traffic to your laptop's IP.

Alternatively you can configure your local firewall (iptables is always installed and running by default on every standard Ubuntu install) to deny access except from the localhost.

---

### Post by XxionxX on 2009-09-18
You can definitely install LAMP on any OS, not just Ubuntu. I use LAMP all of the time for my work. Just Google LAMP and their is a bunch of stuff that will tell you how to install what you need.

---

