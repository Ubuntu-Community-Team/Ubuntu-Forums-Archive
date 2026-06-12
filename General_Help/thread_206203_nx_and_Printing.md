---
title: "nx and Printing"
date: 2006-06-29
forum: General Help
---

### Post by mannheim on 2006-06-29
I am using the new nserver and nxclient on my home and work machines, both of which run ubuntu dapper. I am using nx successfully from home, to connect to my machine at work.

I want to print to the printers which are connected to the local "client" machine (the one running nxclient) from my nx session. The good news: I found something that works for me. The bad news: nx client is supposed to just configure this automatically, but fails to do so. Here are the details if anyone is interested.

The following **works** (for me). On the client machine, I have a printer configured in cups, called LaserJet. On the client machine, I open a terminal and do:

```

ssh -R 30631:localhost:631  myusername@servermachine.net

```

where "myusername" is my user name on "servermachine" where nxserver is running. On the server machine, open up the gnome cups printer config app (or anything equivalent) and configure a new cups printer, specifying the URI [http://localhost:30631/printers/LaserJet](http://localhost:30631/printers/LaserJet), and pick the correct driver. Now anyone on the server machine can print to my home LaserJet printer connected to the client machine. In particular, the nx session running on the server machine can print to the client's LaserJet printer.

Anyway, the thing is, nx client on linux is supposed to be able to do this automagically, but it fails. NX client gives an error message in a dialog box "Could not start CUPS daemon" or something like that. What the nx client is trying to do is very similar to the above scheme, but with the difference that it starts a separate cupsd daemon on the client machine, configured to listen on a non-standard port (2000 instead of 631) and configured to accept print jobs only from the user who launched nxclient. The cups config file is created in ~/.nx/cups/cupsd.conf.

On the client machine, as a normal user, I can also try

```
cupsd -c /home/myusername/.nx/cups/cupsd.conf
```

but it fails "Child exited with status 1!". There is a cups error_log full of complaints about insufficient permissions to write/create/chown various files.

Has anyone got this automagic cups printer sharing to work on dapper?

---

### Post by rvergara on 2006-08-09
I prepared the following How To for Ubuntu Breezy:

[http://www.ubuntuforums.org/showthread.php?t=171121](http://www.ubuntuforums.org/showthread.php?t=171121)

It is a more general and elegant(almost) solution.

Hope it helps

Ramiro

---

