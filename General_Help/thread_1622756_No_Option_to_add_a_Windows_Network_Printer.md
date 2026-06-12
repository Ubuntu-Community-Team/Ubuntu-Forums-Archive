---
title: "No Option to add a Windows Network Printer"
date: 2010-11-15
forum: General Help
---

### Post by fiddler616 on 2010-11-15
Hello,

I've been trying to add a printer that's hosted on a Windows XP machine to my Ubuntu/Crunchbang 9.04 laptop. It's been a suprisingly pain-filled process (I've done it before, and it took thirty seconds...), so here's a summary:

Somehow, the cups daemon wasn't running, but I fixed that by downgrading (sic) libgcrypt11.

I've tried both the samba and the samba4 packages.

Since before I started worrying about this, I got an error message while booting up that the winbind daemon had failed to load. I've tried reinstalling it, but that hasn't done anything.

What else should I do?

For reference, here's what I expect:
[IMG]http://i.imgur.com/83IlT.png[/IMG]

And here's what I have:

[IMG]http://i.imgur.com/FGEDa.png[/IMG]

Thanks!

---

### Post by Gordonbp531 on 2010-11-16
I have to say, to be perfectly honest, in your position I would buy a print server. They are pretty cheap these days, and would solve your problem at a stroke, and also mean that the XP machine wouldn't have to be switched on in order for you to print...

---

### Post by fiddler616 on 2010-11-16
> **gendibal said:**
> I have to say, to be perfectly honest, in your position I would buy a print server. They are pretty cheap these days, and would solve your problem at a stroke, and also mean that the XP machine wouldn't have to be switched on in order for you to print...

Well the machine in question is a *tiny* laptop with 70% of its screen broken. So I leave it on 24/7, since I can't imagine the power draw being very high. Although it does make me uncomfortable having Windows be connected to the Internet for an extended period of time...

It also has Intrepid on it. I initially tried to use that as the host OS, but couldn't get a satisfactory printer driver. However, machine with Jaunty and Maverick *have* gotten the right driver...So I guess I should replace Intrepid with something newer.

Though I'm comfortable with bash and the command line, I can't say I've ever used it to install and share a printer. Is there any benefit to using USE? Or should I keep it simple with Ubuntu Desktop's dead-simple printer wizard? Performance really isn't an issue--it's not like it's serving webpages.

---

