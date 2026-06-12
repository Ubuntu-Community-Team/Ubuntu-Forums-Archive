---
title: "Keep being told 'you are offline'."
date: 2012-01-03
forum: General Help
---

### Post by drdjnicholls on 2012-01-03
Can anyone help me please? Since I began to use Ubuntu (as ex-XP user) I am having a problem which is very time-consuming.
Every now and again, while I am not doing anything unusual, and as far as I recall, sometimes nothing at all, I suddenly get a message on Ubuntu 
(11:10) in the top right hand corner saying 'You are offline'. 
I never had this problem with Windows XP, and furthermore I can see my 
modem is still working and online and when I connect it to another PC running XP, I find that I am still online: on going through the setup particulars that I can find on Ubuntu, I can find no explanation or solution to the problem apart from the one I now have to do which is to reinstall the whole of Ubuntu. whereupon I am connected again. 
On Windows, there is an option to 'repair' a connection if lost, but I cannot see anything like this on Ubuntu. Obviously things would be a lot easier if I knew why this was happening.
Can anyone shed any light on this?
Thanks
David

---

### Post by oldos2er on 2012-01-03
What type of connection do you have? Wired, wireless? What make/model networking card?

---

### Post by drdjnicholls on 2012-01-04
Hi,

Its a Netgear ethernet supplied by Sky and its wired.

---

### Post by drdjnicholls on 2012-01-04
Sorry, perhaps I should have added:
When I am told I have become offline, all the router lights that are on when connected, remain on. It is not a fault of the router as when I unplug it from my PC and plug it into another PC with Windows XP, I am immediately connected to the internet. When I plug it back into the PC running with Ubuntu, I am still offline. Nothing I do reconnects me so, as I say, I have to reinstall Ubuntu which I feel is ridiculous.
Thanks

---

### Post by westie457 on 2012-01-04
> **drdjnicholls said:**
> Sorry, perhaps I should have added:
When I am told I have become offline, all the router lights that are on when connected, remain on. It is not a fault of the router as when I unplug it from my PC and plug it into another PC with Windows XP, I am immediately connected to the internet. When I plug it back into the PC running with Ubuntu, I am still offline. Nothing I do reconnects me so, as I say, I have to reinstall Ubuntu which I feel is ridiculous.
Thanks

How many ethernet plugs can the router take at any time?

If it will only take one then it is a modem not a router. In which case turning off and restarting the modem when changing from Ubuntu to XP or XP to Ubuntu should allow the connection to remain stable for that session.

If the router has two or more sockets then plug a cable in for each PC.

Hope this helps.

---

### Post by carranty on 2012-01-04
> **drdjnicholls said:**
> Nothing I do reconnects me so, as I say, I have to **reinstall** Ubuntu which I feel is ridiculous.
Thanks

Do you mean restart?  Completely reinstalling an operating system because of a dropped network connection is extreme overkill!  What happens when you open the network manager and try to connect again?  Does it give an error message, or just timeout?

Have you tried opening a terminal and typing 

```
sudo /etc/init.d/networking restart
```

In Ubuntu 10.04 this essentially restarts the networking part of your computer, it should work in 11.10 also.

---

### Post by drdjnicholls on 2012-01-05
Re the above answers.

My Netgear router is as I say a router. It has 4 plug sockets at the rear.
I cannot plug in a cable from a PC running XP and a cable from the PC running Ubuntu at the same time as I have only one cable for the router. The only reason I mentioned that there is no loss of connectivity with the PC running XP was to demonstrate the fault lies in Ubuntu and not the router.

When I say reinstall, I do mean reinstall - it takes ages! It was just a restart I wouldn't mind, but reinstalling every time this happens is ridiculous.  
Thanks for text to be typed in the terminal - I will certainly try this next time the problem arises (as I am sure it will do). Hopefully this will do the trick - many thanks indeed.

---

### Post by carranty on 2012-01-05
> **drdjnicholls said:**
> When I say reinstall, I do mean reinstall - it takes ages! It was just a restart I wouldn't mind, but reinstalling every time this happens is ridiculous.

This is very strange, I've never come across this before.  Its as if you have a process running that is overwriting your network configuration files.  Is the connection working now?  If so can you paste the contents of your interfaces file

```
gedit /etc/network/interfaces
```and the output of

```
ifconfig
```Also, to confirm your not behind a proxy can you ping a website and post the first few lines.

```
ping www.ubuntuforums.org
```It would also help to get more information about your network, you have a router (which is probably 192.168.0.1) and then one or more computers/printers/smartphones connected to it.  Try running nmap

```
nmap 192.168.0.1-10
```No need to post the ouput, but save the results somewhere. I'd be interested to see how it compares to the output once you can no longer connect.

You could also run a diagnostic on your router.  In the address bar of your web browser just type 192.168.0.1, it'll ask for your username and password (default is written on the router), then you'll be taken to a webpage from which you can choose to run a diagnostic.

Also, you've probably done this already, but if not, next time it happens try rebooting your router.   Literally unplug it and plug it back in, once its booted up (All three lights are green) try connecting again.

Also, **as I asked earlier**, when you've been disconnected does the connection (probably called "NETGEAR") still show up in your network manager, if so what happens when you click on it? To open the network manager just click on the icon in your system tray at the top right - probably an up arrow and a down arrow between the battery and speaker icons.

---

### Post by drdjnicholls on 2012-01-06
Thanks for all the above. Next time I am given the 
'you are now offline' message 
I will do as suggested and post up the resuilts. I would like to know WHY this happens. 
I will also try the 
sudo /etc/init.d/networking restart
and hope this starts the problem.

---

