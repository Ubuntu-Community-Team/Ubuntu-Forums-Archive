---
title: "Monitor Remote Machine"
date: 2010-04-18
forum: General Help
---

### Post by fiftyfour123 on 2010-04-18
I have a remote ubuntu server and I use a Mac. Is there any program for my mac or web interface that I could use to monitor various services on the remote ubuntu machine? I have webmin but it is much more complicated than what i'm looking for. What I want is to just be able to get an at-a-glance look at the computer. for example, users connected to samba shares, apache bandwidth, uptime, and other things like that. Is there such a thing?

---

### Post by fiftyfour123 on 2010-04-18
anyone?

---

### Post by fiftyfour123 on 2010-04-19
> **fiftyfour123 said:**
> anyone?

bump

---

### Post by t0p on 2010-04-19
You can install [FreeNX]("https://help.ubuntu.com/community/FreeNX") on the computer in question; then use a [NX client]("https://help.ubuntu.com/community/FreeNX#Installing%20the%20NX%20Client") to access that computer remotely.  You'll be able to monitor the remote machine as if you were sitting in front of it.

---

### Post by fiftyfour123 on 2010-04-19
> **t0p said:**
> You can install [FreeNX]("https://help.ubuntu.com/community/FreeNX") on the computer in question; then use a [NX client]("https://help.ubuntu.com/community/FreeNX#Installing%20the%20NX%20Client") to access that computer remotely.  You'll be able to monitor the remote machine as if you were sitting in front of it.

That seems like its the same as VNC. I guess what I'm looking for is a sort of web interface where I can just monitor various processes on the machine.

---

### Post by _0R10N on 2010-04-19
If you're looking for a web interface, well, some of my co-workers use LogMeIn to access remote Windows PCs. I almost sure that it runs under Linux as well.

But if what you want it's to keep trace of a few processes, isn't ssh meet your needs??

Kind regards!

_0R10N >>

---

### Post by fiftyfour123 on 2010-04-19
I want something graphical, which is why I'd rather not use ssh. Basically, I want something similar to webmin. It doesn't need to be as advanced (or buggy for that matter). I don't need to be able to edit config files or anything, just monitor what each service is doing.

---

### Post by lensman3 on 2010-04-19
The "finger" command, but you will have to permit finger to export info.  finger probably won't do what you want.

The "w" command does what you want, but I don't think it will work across a network.

The "w -f" works across the network, but it doesn't report enough info.

---

### Post by fiftyfour123 on 2010-04-19
That's not really what I want either. How about this, Is there a simpler, less buggy, alternative to Webmin?

---

### Post by fiftyfour123 on 2010-04-20
I found monit and that seems to do what I want. However, is there a way to get monit to show the users connected to each service (ssh, ftp, samba, etc.) thanks

EDIT: ok, forget monit. I'm trying ebox, hopefully it'll work out.

---

