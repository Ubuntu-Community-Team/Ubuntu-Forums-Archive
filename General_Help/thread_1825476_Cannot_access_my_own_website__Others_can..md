---
title: "Cannot access my own website // Others can."
date: 2011-08-15
forum: General Help
---

### Post by iLeet on 2011-08-15
Hello again,
I am running Ubuntu 10.04 64-bit on my computer
I installed XAMPP 1.7.4 for Linux
I can access [http://localhost](http://localhost)   just fine but if i were to install forum software then it becomes useless because it trys to redirect me to my global ip address. For some reason I can't access my global ip address, but others can. Try for yourself(Empty Server) [http://99.242.103.96/](http://99.242.103.96/)
The ports are all forwarded and tested too.

I had the same problem on windows

Appreciate help

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-08-15
that is normal most routers/modems do not allow you to do that
theres is a name for the feature that allows that but i don't know it offhand
you could use your /etc/hosts so you system will treat your ip address/domain name as a a loop back

---

### Post by The Cog on 2011-08-15
Agreed. Most routers will not allow address translation when both ends of the conversation are on the inside.

You could try this little trick to put the host address on your own PC as a secondary address:
> sudo ifconfig eth0:1 99.242.103.96 netmask 255.255.255.255
This should allow your PC to connect to itself using the public address (but other internal PCs won't be able to connect).

P.S.
To remove it again, use > sudo ifconfig eth0:1 down
and you may have to change the name accordingly if your main interface isn't eth0

---

### Post by iLeet on 2011-08-15
> **The Cog said:**
> Agreed. Most routers will not allow address translation when both ends of the conversation are on the inside.

You could try this little trick to put the host address on your own PC as a secondary address:

This should allow your PC to connect to itself using the public address (but other internal PCs won't be able to connect).

P.S.
To remove it again, use 
and you may have to change the name accordingly if your main interface isn't eth0

It worked! Thank you so much!

---

