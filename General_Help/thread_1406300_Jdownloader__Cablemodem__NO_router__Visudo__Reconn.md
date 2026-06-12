---
title: "Jdownloader | Cablemodem | NO router | Visudo | Reconnect Config question"
date: 2010-02-13
forum: General Help
---

### Post by smeagol271006 on 2010-02-13
Hi people. This is my first post asking for help. 

I Love Jdownloader program but can't solve this old problem.

I'm still a little retard with GNU/Linux :P

Able to do a reconnect by running the following commands
> 
sudo /usr/bin/cambiar-ip
This is the script I'm using.

less /usr/bin/cambiar-ip
> 
#!/bin/bash
dhcpcd -k eth0 ; sleep 4s; dhcpcd -r 190.189.48.52 -l 10000 eth0
It resembles [this]("http://mail.taringa.net/posts/info/1693227/Solucion-Fibertel-en-JDownloader-+-cambio-de-IP-+-Reconnect.html") one in Window$


The program dhcpcd requires root user privileges. 

Avahi daemon and network-manager widget should be disabled or uninstalled for this to work on Ubuntu. 

Also I'm using Karmic.


I'm not Cisco certified. What I think it does, in a non technical comparison, is tell the ISP hardware that your ip should be 190.189.48.52 or whatever number you like.

For the ISP this would be the last lease you used. 

The ISP hardware does not recognize this last lease in its list, so it assigns a new ip.

That does the trick and you get your new ip! 

My ISP promotes the service with dynamic ip so no legal matters here. 



The problem is how to automatize it. 

Sudo runs the script with no privileges problems.

I am able to run it password-less by modifying sudoers file via visudo command.

I add the following line 

> 
your-user-name hostname = NOPASSWD:/usr/bin/cambiar-ip
It can also be like (this would need extra security measures?)

> 
your-user-name ALL = NOPASSWD:/usr/bin/cambiar-ip
Then you can run sudo /usr/bin/cambiar-ip and it won't prompt you for a password.


Password issues solved, I cannot get Jdownloader to run it. 

In the Settings > Reconnection tab 

Tried to use "External" and "Batch" but i get reconnection failed sad face.

I've tried in "External" /usr/bin/sudo /usr/bin/cambiar-ip

It won't work. ](*,)

I'm missing something of the Unix security structure.  :confused:


Here is the wiki of the program 

[http://jdownloader.org/knowledge/wiki/glossary/reconnect](http://jdownloader.org/knowledge/wiki/glossary/reconnect)

Any ideas?

Thanks in advance ;) and sorry for my bad english.


If you need any screenshots of the program i would be happy to provide them.

---

### Post by sisco311 on 2010-02-13
In the *External* tab try to type: /usr/bin/sudo in the command field & the path to your script ( i.e. /usr/bin/change-ip; cambiar means to change, right? :) ) in the *Parameter* text area. 

Or in the *Batch* tab try */bin/bash* as the *Interpreter* & type *sudo cambiar-ip* in the Batch Script text area.

---

### Post by smeagol271006 on 2010-02-13
Holy Eywa !!! :o

It works ... I still can't freaking believe it.

The first solution works no problem. :D (the second does not)

I tried what you said before but used to type

 /usr/bin/sudo /usr/bin/change-ip 

All in the command box ... What a freaking moron!!! 

Now I understand:

Commands without flags, options or arguments in command box.

Flags, options, arguments go in the parameter box.

So simple that I'm crying in shame! (parameter synonim of the flags, options, or arguments then ...).


THANK YOU VERY MUCH !!!

yes cambiar is change :D

modified status to solved

---

### Post by srdr on 2010-03-27
moved to a new thread

---

### Post by DREMA on 2010-04-13
Hello!

Who is your ISP ?? Im trying the same command on my cable modem with no success.

The only way I had managed to change my ip is changing my MAC and rebooting the modem, but I can't think on a way of automatize it.

Any help is appreciated. 

Thanks

---

### Post by smeagol271006 on 2010-04-13
Hi why don't you check this thread:

[thread]1440125[/thread]

If it helps you, please ask for this thread to be merged with the one I wrote above.

My isp is Fibertel from Argentina.

---

