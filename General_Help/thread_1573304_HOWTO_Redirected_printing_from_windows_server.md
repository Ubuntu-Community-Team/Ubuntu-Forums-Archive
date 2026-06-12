---
title: "HOWTO: Redirected printing from windows server"
date: 2010-09-12
forum: General Help
---

### Post by drfox on 2010-09-12
I regularly have to connect a remote session to a windows server 2008 machine. TSClient has been working well, but I'm always frustrated that I can't print locally. I just discovered a CLI way of enabling redirection of my local printer:
rdesktop <myserver_address> -r printer:Brother-7840W 
works like a charm! I must tell you that my printer is attached to my laptop wirelessly and is an all-in-one device. There are other parameters that you can use to set window size, domain logon, etc.

Now, I guess my question is, why don't we have a GUI frontend that will work with the printer redirection? It looks like the rdesktop and tsclient packages are years old.

Larry

---

