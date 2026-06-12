---
title: "anyone able to configure remote desktop?"
date: 2006-06-07
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-07
Has anyone able to configure remote desktop? With vmcviewer or other. I need to know how, exactly, and how to get it to acces my friend's PC and vice-versa.8)

---

### Post by scxtt on 2006-06-07
make sure you have the vncserver package installed from the repos ... then run it from the command line, it'll prompt you for a password and start the server telling you how to access it (but you can't use "hostname":# like it says most likely cause of DNS issues) ...

on another computer, type vncviewer <ip address>:[connection #] ... (example: vncviewer 192.168.1.100:1)

firewalls / port forwarding can come into play ...

btw, vncviewer is installed by default ... also vino (installed by default) does about the same thing, but IMO doesn't perform as well ... you'll have to "turn it on" tho ...

---

### Post by s_h_a_d_o_w_s on 2006-06-07
I try it and I get this:



Couldn't convert 'blablbalba' to host address

---

### Post by scxtt on 2006-06-07
you'll have to be more specific about the error than that (copy / paste console output?) ...

i've never had a problem w/ ubuntu and VNC ...

also, give vino a shot ...

system --> preferences --> remote desktop (click on the appropriate checkboxes) ...

---

### Post by s_h_a_d_o_w_s on 2006-06-07
Here's my output:

max@linuxrules:~$ vncviewer ubuntudugger.no-domain-set.bellcanada:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Couldn't convert 'ubuntudugger.no-domain-set.bellcanada' to host address
Unable to connect to VNC server

---

### Post by s_h_a_d_o_w_s on 2006-06-07
What's the command 4 vino? (2 run it)

---

### Post by scxtt on 2006-06-07
once you select the right checkboxes, it's "on" ...

do a:

ps -ef | grep vino

and you can tell ...

---

### Post by scxtt on 2006-06-07
[QUOTE=s_h_a_d_o_w_s]Here's my output:

max@linuxrules:~$ vncviewer ubuntudugger.no-domain-set.bellcanada:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Couldn't convert 'ubuntudugger.no-domain-set.bellcanada' to host address
Unable to connect to VNC server[/QUOTE]i'd suggest using your IP address instead ...

---

### Post by s_h_a_d_o_w_s on 2006-06-07
Tries it. SAme thing. I typed:

vncviewer (IP):1

and got same output. got my IP from [this]("http://http://www.lawrencegoetz.com/programs/ipinfo/") site.

---

### Post by s_h_a_d_o_w_s on 2006-06-07
I think it's 'cause vncviewer is using a port my modem has blocked. Any way to unblock or change that port? I have also heard that free NX works well, but i don't know how to get it.

---

### Post by scxtt on 2006-06-07
then your problem is either coming from where you got your IP - mine's just from my cable company - or independent of VNC/vino ...

are you (or the comp. you're connecting to) behind a firewall or on a router?

---

### Post by scxtt on 2006-06-07
[QUOTE=s_h_a_d_o_w_s]I think it's 'cause vncviewer is using a port my modem has blocked. Any way to unblock or change that port? I have also heard that free NX works well, but i don't know how to get it.[/QUOTE]vnc uses port 5901 and vino uses 5900 (run a ps -ef on VNC and it should list the port it's using) ... if you plug directly into your cable modem, it shouldn't be a problem, but if you use a router, you'll have to forward ports ...

---

### Post by lunlun on 2006-12-31
i have setup a config file at ~/.ssh/config

and when i type


"ssh remote" it works, it knows how to convert the remote var to an ip address just as I specified in  the config file.


however, when i do "vncviewer remote" it says, "Couldn't convert 'remote' to host address"


anyone has any ideas?

Thanks for your help:KS

---

