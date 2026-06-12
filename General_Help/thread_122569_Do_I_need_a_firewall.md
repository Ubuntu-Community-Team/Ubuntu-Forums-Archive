---
title: "Do I need a firewall?"
date: 2006-01-27
forum: General Help
---

### Post by jjf on 2006-01-27
Hi.  I'm installing Breezy on an old P3 that will be used mostly for browsing over a high speed (cable) connection.  I want to skip the router and just plug the cable modem directly into the ethernet port.  Problem is, this means I have no hardware firewall.  I'm not worried about spyware or viruses, but I am concerned about tampering and hijacking.

I checked Ubuntu's FAQ about software firewalls, and they say this:

> Since Ubuntu doesn't run any daemons that listen to the outside world by default (the postfix install only listens on localhost) there's no need for a default firewall.

The rationale is that if a user's got a need for installing a world-facing daemon, they'll be aware that they should configure a firewall/ACL for it too. 

To which I reply... huh?  

Should I install a software firewall?  If so, which one?  Thanks.

---

### Post by heimo on 2006-01-28
[quote=jjf]
Should I install a software firewall?  If so, which one?  Thanks.[/quote]

You don't gain anything from configuring / installing a firewall. However, if you want to install one - you could install firestarter, which is actually a graphical user interface for the firewall that is already in your system (integrated in the Linux kernel). Hopefully this answers your question. :) Summa summarum: If you don't run services like web server, mail server, samba server, ftp server or any other services to other computers (outside listening services), you do not need a firewall.

---

### Post by byen on 2006-01-28
Ok...here is what it is:
- Ubuntu by default does not need a firewall as it is built in such a way that the default installed software has no devices/programs listening. So yes..technically you do not need a firewall
- As a former windows user... I still had to get a firewall so I use "Firestarter" Its a graphical program and runs good.

To install firestarter...Open the terminal and type:
> sudo apt-get install firestarter

To configure firestarter to load during startup, [do this (linky)]("http://ubuntuforums.org/showthread.php?p=663298#post663298")

Hope this helps. Goodluck and Welcome to Ubuntu!

Edit: Ah! heimo beat me to it! *must*type*faster*

---

### Post by heimo on 2006-01-28
[quote=byen]
Edit: Ah! heimo beat me to it! *must*type*faster*[/quote] :) Nah... I think many times these "double posts" complete each other nicely and it's always good to have more than one people agreeing on some advice. You also added more detailed information. :KS

Let's also add that as mentioned, Firestarter is a front end, graphical user interface for configuring the firewall that's builtin in Linux and after you've configured it, you do not neccessarily need Firestarter running to be protected by the firewall.

---

### Post by byen on 2006-01-28
[QUOTE=heimo]I think many times these "double posts" complete each other nicely and it's always good to have more than one people agreeing on some advice.[/QUOTE]
Yeah.. thats the bottom line. But I do have to learn to type! It takes me quite a lot of time to type stuff! Well... back to typing...

---

### Post by stream303 on 2006-01-28
[QUOTE=jjf]I want to skip the router and just plug the cable modem directly into the ethernet port.  Problem is, this means I have no hardware firewall.  I'm not worried about spyware or viruses, but I am concerned about tampering and hijacking.
[/QUOTE]

Personally, in situations like this where you are directly exposed to the net, I still prefer a firewall just to keep my box from responding to the net "background noise" of sweeps, probes, etc.  More of a performance thing than a bout of paranoia, but somehow I think it prudent.

But that's just me.  YMMV.

---

### Post by towsonu2003 on 2006-01-28
[QUOTE=byen]Yeah.. thats the bottom line. But I do have to learn to type! It takes me quite a lot of time to type stuff! Well... back to typing...[/QUOTE]
sudo apt-get gtypist ;)

As per the firewall, wouldn't hurt having one, especially when firestarter is so easy to configure (wizard) and needs no maintenance (one setup, than forget about it until you need to open ports or something) and does not sacrifice resources (as opposed to an antivirus for example)

---

### Post by s_spiff on 2006-01-28
Ok I did install firestarter once, but I'm anoob, so basically couldn't configure it, let it remain on defaults, and my net simply didn't work.. I'm on a pppoe connection, and don't have a hardware modem and sorts, the cable just plugs into my eth. card.

---

### Post by byen on 2006-01-28
[QUOTE=towsonu2003]sudo apt-get gtypist ;)
[/QUOTE]
Hey..thanks for that buddy :-)

---

