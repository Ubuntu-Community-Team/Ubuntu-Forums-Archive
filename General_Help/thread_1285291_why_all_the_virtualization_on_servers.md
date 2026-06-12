---
title: "why all the virtualization on servers??"
date: 2009-10-07
forum: General Help
---

### Post by blur xc on 2009-10-07
I've got plans to build a home server sometime next year, and I've been casually reading this and that on diy home server projects, and read a lot about virtualization on servers.  Why?  I admit, I'm pretty ignorant on the whole server subject, I only know a few basic gernal things...

Eventually, I would like a box w/ a nice big raid array, maybe a print-server, and set up w/ Dansgaurdian to filter my kids' internet usage (rather than monitor each laptop)...

Maybe I could do more with one, but that would require knowing what all there is to do on one in the first place...

Is there a "set up a home linux server for complete idiots" book I should be looking for?

Thanks,
BM

---

### Post by cdbitesky on 2009-10-07
First off what do you plan on using the server for? 
There are many reasons for using virtualization on the server platform. Some people output operating systems such as windows from a linux server to keep the stability of Linux while maintaining the usability of certain windows only applications. There is also the option that you can restart the virtual server without ever having to do so on the real one.
I personally have a web/mail/media server and haven't tried it out. If you are just starting out I would suggest doing without for now.

---

### Post by blur xc on 2009-10-07
> **cdbitesky said:**
> First off what do you plan on using the server for? 
There are many reasons for using virtualization on the server platform. Some people output operating systems such as windows from a linux server to keep the stability of Linux while maintaining the usability of certain windows only applications. There is also the option that you can restart the virtual server without ever having to do so on the real one.
I personally have a web/mail/media server and haven't tried it out. If you are just starting out I would suggest doing without for now.

Primarily I need a NAS server.  I was interested in FreeNAS for a while, but for not much more money (the os's are the same price - $0) I could build a full fledged server, but with a big increase in difficulty to set it up.

Secondarily, I would like to filter my kid's internet usage with something like dansgaurdian.  They are getting small laptops this year for Christmas, and even though all their internet usage will be closely supervised, I still would like to prevent accidental access to inappropriate content for young kids.

Thrid- if it's not too difficult, it would be good to set it up as a print server so all computers could easily access the same printer.  I don't know if that's easier to do than get a wifi or network printer (w/ a rj45 jack on it) and set up each computer to access it directly.  After Christmas, we will have 6 computers in the house- and I will finally no longer have to fight w/ my kids for access to my own pc!

BM

---

### Post by cdbitesky on 2009-10-07
Well its sounds like you have days of fun ahead of you. a NAS is pretty easy to set up depending on what is accessing it, seeing as there are tons of tutorials on how to do so out there. 
I would be very careful with a print server, however as i have had significant issues with using certain printers from a linux(or even vista) machine so if you plan on doing so find one that is compatable with linux; or as you said a wi-fi(be careful about security if you do this *) or ethernet one. The latter seems to be better to me although they are more expensive. 
As for the monitoring the internet usage, I havent never even attempted to do so for i never saw the need so i'm a complete newb in that department. 


*I had a nasty run in when someone hacked into the wireless printer at my old work and printed out page after page of full page stuffs(pics) until it ran out of ink or paper. And we had several. It was rather annoying.

---

