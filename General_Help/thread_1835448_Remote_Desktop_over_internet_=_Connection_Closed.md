---
title: "Remote Desktop over internet = Connection Closed"
date: 2011-08-29
forum: General Help
---

### Post by Horadranin on 2011-08-29
Hi!

I'm trying to access my home Ubuntu using Ubuntu from my workplace, both are 10.10 version.

In home I already checked Allow others view and control my desktop. I did some test from inside a virtual machine installed in my home pc and it worked.
Next I forwarded port 5900 in my router to my home Ubuntu machine. To test the port forward I went to [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/), typed my external IP and desired port and it said the port was open. I deactivated the remote access in my home machine and tested again. The site said it was closed, so I re-enabled the service and assumed the port forward was working.

Now I'm in my work Ubuntu but when I try to connect home using vinagre it pops up the message "Connection Closed".

What I did wrong?

---

### Post by HarrisonNapper on 2011-08-29
Your workplace is likely blocking it. Not much you can do and depending on your job function, if it's not an awkward conversation to have, you can ask the sysadmin(s) at your workplace.

---

### Post by Horadranin on 2011-08-29
> **HarrisonNapper said:**
> Your workplace is likely blocking it. Not  much you can do and depending on your job function, if it's not an  awkward conversation to have, you can ask the sysadmin(s) at your  workplace.

Hi HarrisonNapper and thanks for the quick reply.

I installed Wireshark to sniff traffic in port 5900 to see if is anyone  dropping my packets.It captured 2 packets: the fist send a syn from my  private ip and the second is the response from my home external ip with the reset flag set.
I'm not a network expert, but my guess is that my modem/router itself is  refusing the connection. Besides if that is true, why the site says it  is open?

The network admins will not unblock this kind of traffic, if it is happening. I'll need to find alternatives.

---

### Post by Horadranin on 2011-08-29
There is a way to know if VNC traffic is being blocked? I don't know where the network guys are, so is hard just go and ask them.

---

### Post by HarrisonNapper on 2011-08-29
No worries. You can change the server so it's listening on a less standard VNC port but sometimes a proxy or firewall will block outgoing traffic by analyzing the traffic itself, so that may not help. It may be your home router is blocking it. One way to test that is to set up ssh on the intended target machine, ssh on one computer to somewhere outside of your network (see freeshell<dot>org) then try to ssh back in to see 1. if the connection is accepted and 2. if it's routed to the correct machine. This is where updating NAT tables and forwarding your ports becomes handy. 99% chance it will be blocked, though; sorry :)

---

### Post by Horadranin on 2011-08-29
> **HarrisonNapper said:**
> 99% chance it will be blocked, though; sorry :)

..and the 1% change failed, it is not my day today.
I tried ssh to sdf.org to create a account and it failed with connection refused. The workplace firewalls sure is blocking this kind of port.

HarrisonNapper, do you know how to change the build-in VNC server port?

Anyone knows something like LogMeIn [https://secure.logmein.com]("https://secure.logmein.com/") for Linux? It controls a desktop using http so I'll have zero port problem.

---

### Post by spiky001 on 2011-08-29
Is there a reason you want to use VNC (UNSECURE OVER INTERNET) Is  it possible to use ssh far more secure

---

### Post by Horadranin on 2011-08-29
> **spiky001 said:**
> Is there a reason you want to use VNC (UNSECURE OVER INTERNET) Is  it possible to use ssh far more secure
ssh just give me a command line interface and I need the graphical one.
Anything that allows me to use the GUI of my home Ubuntu will do nice.

---

### Post by Wayne_V on 2011-08-29
can you ssh from your work machine?  if so, just port forward your home vnc server (no need to open vnc on your router, just ssh):

ssh -N -t -L 5902:localhost:5900 user@remote

then, connect vinagre to localhost:5902 (note, I use 5902 because my localhost already has vnc server running on it).

---

### Post by Horadranin on 2011-08-29
> **Wayne_V said:**
> can you ssh from your work machine?

No, seems like outbound ssh and telnet traffic is being blocked :(

---

### Post by Wayne_V on 2011-08-29
but some ports are open?  if so, route that port on your router to ssh on your home system and add -p <port#> to the ssh command.  if nothing else, port 80 .... assuming you don't have a web server running at home.

---

### Post by Off Shore on 2011-08-29
> **Horadranin said:**
> ssh just give me a command line interface and I need the graphical one.
Anything that allows me to use the GUI of my home Ubuntu will do nice.

I do understand what you are saying but it seems a shame you cant build up some confidence with a terminal.
This is a really good tutorial on ssh and I hope you might find it useful.

[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

Best Regards

edit: I forgot to say to use port 443 as those pesky ISA servers are usually set up to block port 22.

---

### Post by HarrisonNapper on 2011-08-29
> **Horadranin said:**
> ssh just give me a command line interface and I need the graphical one.
Anything that allows me to use the GUI of my home Ubuntu will do nice.

Doesn't matter a whole lot now since I'd be willing to bet they're blocking by traffic type, but you can enable X forwarding through ssh if the client machine has X11. It is definitely more secure and you should also take as many security precautions as possible with VNC.

---

### Post by Horadranin on 2011-08-29
> **Wayne_V said:**
> but some ports are open?  if so, route that port on your router to ssh on your home system and add -p <port#> to the ssh command.  if nothing else, port 80 .... assuming you don't have a web server running at home.

Thanks for the tips, man.

Port 80 in not in work in my home pc, so I can use it. What you is asking me to do is run the command bellow?
```

ssh -p 80 -N -t -L 5902:localhost:5900 user@remote (with respective user and remote)

```

Or only a plain 
```

ssh -p 80 user@remote

```

For both I get a connection refused on port 80. :(

---

### Post by Horadranin on 2011-08-29
> **Off Shore said:**
> I do understand what you are saying but it seems a shame you cant build up some confidence with a terminal.
This is a really good tutorial on ssh and I hope you might find it useful.

[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

Best Regards

edit: I forgot to say to use port 443 as those pesky ISA servers are usually set up to block port 22.


I'll will give it a try.
But I have little use to connect via CLI only. I want do some text editing, so I need Openoffice. I used to do it in my work Ubuntu and sync it with a service of online storage. I have a account in both Dropbox and Ubuntu One but they are blocking all this kind of stuff here.
Currently I'm using a flash drive but keep files backed up is hard. For 2 times I overwrite my new copy with my old copy loosing recent changes. ](*,)

---

### Post by Wayne_V on 2011-08-29
the first ssh is correct, but you also need to configure your home router to forward port 80 to port 22 on your pc.

---

### Post by HarrisonNapper on 2011-08-29
> **Horadranin said:**
> Thanks for the tips, man.

Port 80 in not in work in my home pc, so I can use it. What you is asking me to do is run the command bellow?
```

ssh -p 80 -N -t -L 5902:localhost:5900 user@remote (with respective user and remote)

```

Or only a plain 
```

ssh -p 80 user@remote

```

For both I get a connection refused on port 80. :(

Port 443 might be better, as the traffic is expected to be secured. ssh over 80 might be blocked. Telnet on the other hand...

EDIT: Also I should mention that trying to get around this stuff could land you in trouble at work. Might want to see if there's a policy reference to make sure.

---

