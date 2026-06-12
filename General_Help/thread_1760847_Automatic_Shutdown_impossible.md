---
title: "Automatic Shutdown impossible"
date: 2011-05-17
forum: General Help
---

### Post by daelomin on 2011-05-17
Hi all,

I'm using the latest ubuntu 11.04 and so far no major issue (besides having to tweak it to have both unity & compiz working together).

However, I'm getting very annoyed at reboot times : the automatic logoff / reboot procedure fails & hangs. I always end up doing a force shutdown -with power off button.

Anyone experienced that? Any work-around?

thanks

---

### Post by bdoe on 2011-05-18
I'm experiencing that issue with Mint 11 "Katya", which is based on Ubuntu 11.04, but without Unity. For me, it happened after installing fglrx. It doesn't seem to matter whether I install it via Jockey, through ubuntu-x-swat/x-update PPA, or through building it myself from ATI's website. Removing fglrx does not fix the problem.

For me, the problem happens when I try to shut down (regardless of method) and even when I just try to log off. Pressing ctrl-alt-del produces a screen full of text, with this at the end:
```
unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused.
init: plymouth-upstart-bridge main process terminated with status 1
```
Pressing ctrl-alt-del causes those lines to repeat. The keyboard is completely unresponsive otherwise.

Edit: Turns out, it had absolutely nothing to do with the graphics drivers! It just so happened that I was also setting up my CIFS mounts at about the same time as I was changing my graphics over to fglrx. Unlike previous manifestations of the age-old CIFS issue, this time it left no hint of a CIFS/NFS hang during shutdown. Weird!

---

### Post by bdoe on 2011-05-19
I don't know if you have any network shares mounted when you try to shut down, but if you do, then you are probably affected by the age-old CIFS bug that appears to have gotten much worse with Natty. See [this thread](http://ubuntuforums.org/showthread.php?t=1741668) for more details.

---

