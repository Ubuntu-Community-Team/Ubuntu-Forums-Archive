---
title: "I Found SSH - Along with problems :)"
date: 2010-07-22
forum: General Help
---

### Post by netboom on 2010-07-22
OK, So I'm trying to get to grips with Linux and I've found the terminal and I've been playing about with SSH to connect to my desktop from my laptop. I used the IP's that I found in my IP connections and connected fine and even managed to copy a file over.

I wanted to try use SSH when I was away from home to connect to my desktop computer so i tried to copy the same file using my my internet IP address(which i got from a website).. I'm sure that terminology is incorrect but hopefully you know what i mean.

I get the msg

ssh: connect to host 83.34.131.228 port 22: Connection refused

anyone know what this means exactly? am i going about it the right way? 

Thanks for your time.

---

### Post by Iowan on 2010-07-22
I suspect the internet IP address is associated with your router. You'll need to set up port forwarding to reach your desktop. You might also want to consider some extra security steps to avoid the script kiddies hammering on port 22.

---

### Post by netboom on 2010-07-22
Thanks for the reply, can you point me in the direction of a tutorial?

---

### Post by marshmallow1304 on 2010-07-22
^Yes.  Among other things, I recommend using a non-standard port.  When setting up port forwarding from your router, use some port somewhere up in the thousands and forward it to 22 on the desktop.  Then use

```
ssh <user>@<ip> -p <port>
```


> **netboom said:**
> Thanks for the reply, can you point me in the direction of a tutorial?

The process varies from router to router, but [PortForward.com]("http://portforward.com/") is a good place to start.  Select your router, continue past the advertisement, then click the 'Default Guide' link.

---

### Post by netboom on 2010-07-22
Thanks very much, fast great support here :)

---

