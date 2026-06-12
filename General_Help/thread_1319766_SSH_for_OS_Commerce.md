---
title: "SSH for OS Commerce"
date: 2009-11-08
forum: General Help
---

### Post by sandsjh on 2009-11-08
Is there a program similar to BitVise for Ubuntu? The main thing I need is to map ports to the localhost.

[IMG]http://i37.tinypic.com/21mykc3.jpg[/IMG]

TIA

---

### Post by The Cog on 2009-11-08
Never heard of it. I presume it's some kind of Windows program. 

What are you trying to achieve?

---

### Post by sandsjh on 2009-11-09
Greetings. It does SSH port forwarding.

I connect to the remote server machine.host.com on non-standard port 2222 and have machine.host.com:80 be able to connect to my machine at localhost:81. 

I do this because I believe it makes osCommerce admin panel way more secure by now allowing anything but local access.

---

### Post by The Cog on 2009-11-09
> **sandsjh said:**
> Greetings. It does SSH port forwarding.

I connect to the remote server machine.host.com on non-standard port 2222 and have machine.host.com:80 be able to connect to my machine at localhost:81. 

I do this because I believe it makes osCommerce admin panel way more secure by now allowing anything but local access.

SSH can do port forwarding. A command-line like this:
```
ssh -L 127.0.0.1:81:localhost:80 -L 127.0.0.1:82:localhost:2082 -L 127.0.0.1:83:localhost:2083 -N machine.host.com
```
might be what you need. After running this command, you local machine is listening on ports 80,2083,2084 and forwarding them to ports 81,82,83 on machine.host.com. You will need to run the command under sudo because opening listening ports below number 1024 is a privileged activity on Linux. If you leave the -N off, you will find yourself in a remote command prompt.

---

