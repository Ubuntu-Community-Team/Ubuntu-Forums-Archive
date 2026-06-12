---
title: "Desktop sharing over the internet?"
date: 2010-11-27
forum: General Help
---

### Post by danielstrong52 on 2010-11-27
Hello everyone: a friend of mine who is currently living in a different country has just installed ubuntu on her computer and I am having a very frustrating time finding coherent/useful information about how to set up a remote desktop connection with her over the internet with. Right now I'm trying to set up a remote server on MY computer so that I know the process and can tell her what to do. Particularly annoying is the erratic behaviour of Ubuntu's default remote desktop function. The results are erratic, sometimes instructing me to connect to localhost, other times to my IP address, and usually informing me that I can only connect to this computer over the local network. At one point this summer i actually succeeded in getting a friend to connect over the internet to it, but that has not happened again. Why is it doing this?

I get the impression that VNC is the best method for connecting remote desktops, but I haven't had any luck with that either. I assume I must be doing something wrong setting the servers up: i just run vncpasswd to set the password and then vncserver. What else do I need to do? I couldn't find any simple or clear tutorials. Some places seemed to suggest I would have to configure the router if I have one (which I do), but I didn't have to do that in the summer. Although, it was a different router then.

Do you need more information on anything? I can't think of anything right now, I'm very tired. If you can point me to any helpful tutorials then that would be great. I have a decent amount of experience with the command line in general, but I'm not very knowledgeable about networks.

Thanks

Dan

---

### Post by Jamesss on 2010-11-27
Hi Dan,

I did the following which works for me:

1) Opened an account with dyndns.com and set the router to automatically update the WAN IP address on the remote machine to a domain name of my choice whenever the IP address is refreshed.

2) Enabled port forwarding on the remote machine's router - default port is 5900 for VNC (IIRC).

3) Enabled port forwarding on the local machine's router and connected to the domain name. 

4) Also, if the remote machine has a dynamic LAN IP address, you probably want to reserve one specifically for that machine.

James

---

