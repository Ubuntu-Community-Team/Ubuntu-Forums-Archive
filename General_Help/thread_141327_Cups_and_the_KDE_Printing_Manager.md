---
title: "Cups and the KDE Printing Manager"
date: 2006-03-08
forum: General Help
---

### Post by doctorwebbox on 2006-03-08
I have been using Ubuntu for a while, now I love the easy user friendly installer but struggle with printing.

Firstly, when I call up the print manager (kcmshell printmgr) and I try to do an administration task such as adding a printer, I am asked for a user name and password. I can't for the life of me figure out what it wants. There are two users on the machine, staff and root. It won't let me in no matter which username and password I give, my way around this is become root in a terminal and then call kcmshell printmgr - this way at least I can get at the tools I want but I'm still confused as to why I have to do this.

The next problem I have is:
I want to share the printer on this machine with other machines on the network. Having added a printer and confirmed that it works OK I have tried to connect to it from another machine - no good. So using the printing manager I went to Configure Server - hoping to find a "share this printer" option or similar. Instead I have found that simply choosing the Configure Server option breaks cups even if I don't adjust a single setting. The message says: "Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error: connection refused", the printer I had added has dissappeared and I have to remove and purge cupsys, re-install,  reconfigure and add the printer again. This seems mad and is not isolated to this one installation, I have had similar problems on other installations. Grrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr.

So I thought maybe the problem is with the printing manager, I tried to use the cups web interface but access to the administration tools are disabled in Ubuntu and I don't know how to re-enable them.  Grrrrrrrrrrrrrrrrrrrrrrrr again.

Please can someone help - I'm very confused and my co-workers are are getting annoyed at not being able to use the printer from their machines and keep telling me "It worked fine when it was Windows" - and they're right :(

---

### Post by feathers on 2006-03-08
Cups has changed some settings in cupsd.conf and the kde configuration utility has not yet made the necessary changes. So you can't actually use it. 
To make a printer usable for other clients you have to explicitly allow the use of this computer. Unfortunately I don't know the exact configuration but I can have a look in the next few days. If nobody else knows the exact configuration I ask your patience till then.

---

### Post by doctorwebbox on 2006-03-08
I managed to sort the networked printing this afternoon. I had to change to it to listen on "Port 631" rather than "Listen 127.0.0.1:631" in cupsd.conf. That did it.

Is the username/password problem related to the kde software being behind the cups software or is that down to something else?

Thanks a lot for your help.

---

