---
title: "All ports are closed, how to open them?"
date: 2006-02-15
forum: General Help
---

### Post by LitleDogg on 2006-02-15
Hi

I have run Ubuntu 5.10 fore a couple of weeks now and have not been abel to sucsesfully open ports for inbound comunication (Azureus(firewalld), aMule(lowID)) I have installd Firestarter and put outbound traffic as Perrmissive and added the ports (4662,4665,4672,6881-6999) to Inbound traffic policy. (Port 6881 has worked on my other machine so it is not closed by my ISP, and no it is not forwarded to any other IP than my linux box ;) ) And I have configured my router to forward thees ports to my local IP (Port forwarding works on all my other machines (windows)) BUT when I run nmap and scan my machine all ports come upp closed! So what gives, wher/what/how is the port closed? :-k 

Best regards

Magnar

---

### Post by curtis on 2006-02-15
Does it work without Fire starter running?
As no ports are 'closed' in Ubuntu by default, just no services listening for connections.

---

### Post by newuser111 on 2006-02-15
ports are closed by default on all computers, they are only open if some service is listening on that particular port

---

### Post by LitleDogg on 2006-02-15
:D :D :D 

Three weeks of head scratching and banging my head against the wall, and what was the problem you ask, wel, in my port forwarding table i had forwarded the same range twice to two difrent IP's and everything after that in the table was ignored......... \\:D/ 

So now it works :-D

---

### Post by j800r on 2008-05-31
i've had the same issue. no matter what port i try an get Deluge to listen to, it comes back as closed. I have upnp enabled and originally, it was working fine. No all of a sudden all ports are blocked. I tried manually forwarding and that didn't work either. I tried disabling my router's firewall and that didn't work. Please help! I really don't wanna resort to reinstalling ubuntu or using kubuntu instead. :|

update: no worries now. firestarter was blocking all my torrent programs. I didn't realise cause it wasn't open in the system tray.

---

