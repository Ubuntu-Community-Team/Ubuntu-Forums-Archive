---
title: "Ping test tool !"
date: 2012-01-09
forum: General Help
---

### Post by elliotbeken on 2012-01-09
Hi all i have a project i want to work on.

what the plan i have is to create a ping test tool that allows users to put in an ip address and ping it. (like this [http://centralops.net/co/Ping.aspx](http://centralops.net/co/Ping.aspx))

i want to run it from a server i have at home running ubuntu 11.04

does anyone have an idea on how to do this ?

Thanks

---

### Post by Double.J on 2012-01-09
Probably start by looking at the terminal ping command - look at the man page in the terminal or [here]("http://linux.die.net/man/8/ping")

or head over to the ping home page [here]("http://www.ping127001.com/pingpage.htm") - loads of info and the source code's about half way down. 

You should be able to write a script using ping to achieve what you want.. unless you just want to test a specific ip by pinging it.. then just use the ping command.

Hope it helps!

---

### Post by KdotJ on 2012-01-09
Is the purpose to write your own program to do the pinging? (E.g. sending the packets and calculating RTTs etc) or just to create a web front end for users to remotely use the ping command?

---

### Post by elliotbeken on 2012-01-09
i want to host the front end and also run the ping test from my server.


so if a users wants to ping 8.8.8.8 it pings from my home server. 

basically i want to be able to send pings from my home server to any address or dns name...

---

### Post by KdotJ on 2012-01-09
I see, then you could just use the ping command from your home server surely?

Can I just ask, can you share the reason? Because the trip time that comes back will be between the host and your home server, not the user's machine.

---

### Post by elliotbeken on 2012-01-09
That is what i want it is a test to send from my server reguardless of the users location in the world to a dns or ip address. for example if a user is at a college or place of work and they cant access a site they could go on to my website and ping to see if the site is down or just blocked by their own firewall/network.

in short all i need is:

1. to allow a user in input an ip address or dns address

2. my home server pings the address

3. the output of the ping test is shown on the webpage.

Thanks

---

### Post by elliotbeken on 2012-01-09
something like this [http://www.ipaddressguide.com/ping](http://www.ipaddressguide.com/ping)

but i want the whole process to be run on my server not another one in the internet.

---

### Post by KdotJ on 2012-01-09
The quick way, have your webpage execute the ping command on your server (using the user's inputs they provided) with php (or other) and then capture the output and display it on the page

---

