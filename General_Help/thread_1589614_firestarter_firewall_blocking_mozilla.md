---
title: "firestarter firewall blocking mozilla"
date: 2010-10-06
forum: General Help
---

### Post by shanep-server on 2010-10-06
I updated my system with system updates and when i restarted.. I couldn't access the internet from my desktop... i got on laptop internet worked just fine... i disabled firestarter... and mozilla connected to the internet just fine. I turned firestarter on.. and i couldn't reach anything.. What do I have to do to get firestarter to allow me to connect to the internet via firefox

---

### Post by coffeecat on 2010-10-06
> **shanep-server said:**
>  What do I have to do to get firestarter to allow me to connect to the internet via firefox

Uninstall Firestarter - seriously. It's a dead, unmaintained project, with nasty bugs and I wouldn't let it within a hundred miles of my systems.

Do you realise that it is not a firewall? The actual firewall is called iptables and is compiled into the kernel. Firestarter is merely one of a number of iptables configuration frontends. Which is why you don't need it running for iptables to do its work. Trouble is, you don't know whether it is doing what you told it to do. When I tried it, it definitely didn't do what I told it to do - blocking services I had told it to unblock.

If you want a gui to edit iptables rules, a better choice would be gufw.

Why did you install Firestarter? Do you have any specific needs? The default Ubuntu set up is safe and if you are behind a modem-router you are effectively firewalled from the internet anyway.

---

### Post by shanep-server on 2010-10-06
yah i know its just a front end for ip tables i've used gufw before as well.. firestarter just looked better to my eyes LOL.. if its as bad as u say i'll believe u and go back to gufw... I like a firewall going it makes me happy lol and having to manually type out ufw allow tcp port blah blah blah doesn't make me happy. I'll uninstall firestarter an try out gufw... seems stupid for ubuntu guides to be suggesting firestarter if its as bad as u say.

---

### Post by coffeecat on 2010-10-07
> **shanep-server said:**
> .. seems stupid for ubuntu guides to be suggesting firestarter if its as bad as u say.

I would hope the guides that suggest Firestarter are not official Ubuntu ones. There are many guides out there on the internet that Ubuntu/Canonical have no control over just as there are many guides on the internet that offer appallingly bad advice. 

The ubuntu community documentation page for Firestarter...

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

... does give a warning about this being unmaintained.

---

