---
title: "Be invisible to other network clients"
date: 2009-11-11
forum: General Help
---

### Post by simartem on 2009-11-11
I am using internet through a wireless adsl modem which there are other clients connected to this modem. The clients are running windows. I dont want my computer name to be visible on network shares when the other computers look at the network. I dont want to share any files and dont want my name to appear. My computer name is "Ubuntu". I have samba installed and running. How can i be invisible to the network shares ? I am using ubuntu 9.04

Thank you!

---

### Post by alphaniner on 2009-11-11
The Samba 'client' allows you to access shares on other machines.  The Samba 'server' allows you to share stuff on your machine.  The client is installed by default, the server is not.  I'm almost 100% certain that your machine will not be visible at all if you don't have the server packages installed.  If you are not sure, open synaptic and search for 'samba'.  The server package is simply called samba.  If the box beside it isn't green, it's not installed.

Alternately, enter **aptitude search samba** in the terminal.  There will be several lines, but the important one will look something like the following:

```
[COLOR="Red"]p[/COLOR]   samba                           - SMB/CIFS file, print, and login server
```

The 'p' means samba server **is not** installed.  If instead of a 'p' you see an 'i', then samba server **is** installed.

---

### Post by simartem on 2009-11-12
i have a samba server running.. should i stop it to be invisible ? How can i stop the samba server on desire ? There were some commands which i dont remember clearly.. something such as.. /etc/init.d stop samba (i dont know if i am mistaken)

---

### Post by module0000 on 2009-11-12
You can stop samba with /etc/init.d/<sambaname> stop

Or with the GUI in System->Administration->Services, then select samba and stop it.

If you are using 9.10 and do not see "Services" under system->administration, you will need to install it from add/remove software.

---

### Post by simartem on 2009-11-12
thank you
i am on 9.04

---

### Post by alphaniner on 2009-11-12
Out of curiosity, if you "dont want to share any files" why keep samba server installed?

---

