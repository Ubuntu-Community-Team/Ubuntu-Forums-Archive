---
title: "I can't get connected to the internet"
date: 2010-08-10
forum: General Help
---

### Post by Nsmith0723 on 2010-08-10
I've installed Ubuntu server edition 10.4 to one of my older computers and When I go to install something I get the error message Package could not be found. I'm assuming it's not connected to the internet. It doesn't Show up on my router. I'm trying to install Ubuntu-desktop using the code "sudo apt-get install ubuntu-desktop. any help you could give me would be great. thanks

---

### Post by yunone on 2010-08-10
do you have internet connectivity? can you search to google, cnn, etc?

if you can, are you trying to load something from a repo that is not installed on your machine?

---

### Post by iMisspell on 2010-08-10
Cant anwser your question directly, but maybe the following will help other people help you.

In your terminal type **ifconfig** and copy/past the results here.
Also try and ping a web site:
**ping google.com** and copy/paste results here.
Hit Ctrl+z to stop.

Being this is a fresh install, stating any and all changes which you have made since the install might be helpful, specially if you did anything with the firewall.

Good luck.

_

---

### Post by pricetech on 2010-08-10
> **Nsmith0723 said:**
> It doesn't Show up on my router.

I'm guessing that means your router shows all its "clients", like many do.  This means your network isn't working yet.  Start with the steps above to see if the hardware is even seen, then we'll go from there.

---

### Post by Nsmith0723 on 2010-08-10
No, I have no internet connectivity at all. I'm not sure how i would Copy and paste without graphics.

---

### Post by Nsmith0723 on 2010-08-10
O I forgot. I haven't changed anything so far.

---

### Post by yunone on 2010-08-10
lets start with the basics

unplug your modem cable from the router and connect it directly to your computer with ubuntu installed.

at that point we now know you have a direct connection to the internet

now try browsing the web...google, cnn, etc

once you have established you can do that we can move onto installing the software and configuring your router

---

### Post by Nsmith0723 on 2010-08-10
> **yunone said:**
> lets start with the basics

unplug your modem cable from the router and connect it directly to your computer with ubuntu installed.

at that point we now know you have a direct connection to the internet

now try browsing the web...google, cnn, etc

once you have established you can do that we can move onto installing the software and configuring your router
OK. First off, how am i suppose to browse the internet in a command prompt, maybe if i could install lynx or something. and I've already tried connecting it directly. its a no go. I'm just going to try and install the desktop with a live cd and see if that works. Thanks anyway.

---

### Post by iMisspell on 2010-08-11
> **Nsmith0723 said:**
> ...I'm not sure how i would Copy and paste without graphics. That makes two of us :) ,sorry about that. Im used to SSHing to my server where i have a curser to highlight.

Dont know if any of this will be helpful to you, but...
Command **hwinfo**, will list off your hardware. 

Using *grep* will print out lines with what ever "search word" you define... 
So to make the list smaller and to the point, **hwinfo | grep Ethernet** will list off info with the word 'Ethernet' in it.

If you ifconfig you should see atleast two things...
```
eth0      Link encap:Ethernet  HWaddr .....
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
...
...
...
...

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
...
...
...
...

```

Look to see if the **addr:###.###.###.###** ip makes scene for your local network.

If you see more then one **eth#** (eth0, eth1, etc.) you can try the following...
**sudo ifconfig eth1 down** to all but 'lo' and 'eth0' and see if you can connect/download.



_

---

